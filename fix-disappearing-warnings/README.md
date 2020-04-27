# Fix disappearing warnings

Resolves an issue that would cause continued (CON) or extended (EXT) warning polygons to disappear from the display.

*PREREQUISITE*: You must have root access to the workstation you are running AWIPS on, either via `su` or `sudo`.
*NOTE*: This patch is for the NWS version only. I am working on one for Unidata's variant of AWIPS.
*NOTE*: This patch directly overwrites the JAR file for the warnings visualization plugin. You should back up the original copy just in case of an unforeseen issue. Additionally, this patch will not survive upgrades (unless it somehow finds its way into the baseline).

## To install

This patch was developed and tested against the AWIPS 19.3.1 operational baseline from the National Weather Service. It should not be used with the Unidata version as the Unidata build of 18.1.1 (as of revision 6) has a fork of the warnings plugin with several key differences specific to Unidata EDEXs.

- Exit CAVE.
- As root (or using sudo), copy the `com.raytheon.viz.warnings.jar` file to `/awips2/cave/plugins/com.raytheon.viz.warnings_1.16.0.2019110413/`.
- Restart CAVE and load warnings. If there are active warnings that are eventually updated, you will see the polygons display properly.

## What was happening?

This bug was the result of a complex interaction between how the Thin Client in polling mode batches requests and how warnings are painted onto the screen, particularly in cases where they are continued (CON) or extended (EXT). In situations where the same warnings were displayed in multiple panes (or the same pane in the case of the default warning menus in NWS CAVE), duplicate data notifications would be sent through CAVE to the warning plugin. This isn't necessarily wrong -- each resource tends to fend for itself as far as fetching its own data -- but in the case of warnings, where a shared key/value store is used amongst all threads, the duplication would end up in that store.

As CAVE would determine which warnings to paint on the screen, it loops through each warning record to see if it is an alteration of a previous warning record, matching on office ID, event tracking number (ETN), phenomena, and significance (watch/warning/advisory). If it does find an alteration, it marks the _original_ warning as `altered` so that down the line it would not render on the latest frame that was trying to be painted. However, because of the duplication of these records, CAVE would end up marking the _continuation_ as `altered`, which caused a chain reaction that ended up with the warning not only not displaying on the screen, but being purged completely so that it would not reappear even if subsequent continuations were issued.

All of this was resolved with one line of code: A duplicate check when determining which records to load into the warning key/value store. You can see my modifications in the `AbstractWWAResource.java` file, which is several levels deep in `com.raytheon.viz.warnings`.

"Fun" facts:
- This did not appear to affect Special Marine Warnings because they were loaded separately and as single resources. If you had Special Marine Warnings on two panes, however, this issue would become reproducible with those, too.
- If one was to load warnings via the menu, and then promptly unload the overarching "National Warnings" resource (typically rendered in gray and used for time matching if no other resources have this role), followup statements continuing or extending the warning would be rendered properly.
- This has been bothering me for a couple years now, and I cannot say how happy I am that it (appears) to be fixed.
