# Additional basemaps

The basemaps in this directory are not found on a typical Unidata AWIPS install, but are available within the NWS 19.3.1 operational baseline. Without these, loading METARs, buoys, and forecast soundings may yield error messages/black banners in AlertViz (on Linux).

## To install

- Open the Localization perspective.
- Navigate to CAVE->Basemaps.
- Right-click on the Basemaps folder, select `Import File...`, and import each of these basemaps (sadly, one by one).
- To ensure the County Names map option works correctly, you'll also need to import the CountyNames.xml bundle in the Bundles folder by going to CAVE->Bundles->maps, right-clicking on the `maps` folder, selecting `Import File...`, and then choosing the `CountyNames.xml` file.
- Restart CAVE to ensure the changes take effect.
