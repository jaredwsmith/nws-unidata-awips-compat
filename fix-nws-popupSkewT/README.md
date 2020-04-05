# Fix popupSkewT sounding sources

The NWS AWIPS baseline uses dramatically different field names for grids (etc. `eta212` vs. `NAM40`). This causes incompatibilities between NWS CAVE and Unidata EDEX servers. For this particular patch, we will be updating the `sources.xml` file for the popupSkewT feature.

_NOTE_: This only seems to be effective for Linux installations. I'm looking for a Windows workaround.

_PREREQUISITE_: You must have root access to your Linux workstation to install this file.

_NOTE_: This will not survive upgrades and must be reapplied with each subsequent install of AWIPS.

## To install

- Close CAVE.
- Copy the repository's `sources.xml` file to `/awips2/cave/etc/popupSkewT`, overwriting the existing sources.xml. You will need to do this as root or use `sudo`.
- Restart CAVE.

## To use

I wrote a tutorial for AllisonHouse a while back outlining just how useful this tool is. [Check it out!](https://support.allisonhouse.com/hc/en-us/articles/360011185572-Display-a-Skew-T-using-GOES-16-Infrared-RAP13-NAM12-GFS20-Data)
