# GOES-R series RGB support and other fixes

This directory contains the necessary files to enable support for GOES-R-series RGB composites. Support for the CIMSS Natural Color and Sandwich RGBs is also included. Additionally, this tweaks the GOES Night Fog product to use the 10.3um channel in the difference calculation as opposed to the legacy 11.2um channel.

## Important note

GOES RGBs can only be rendered on machines with nVidia cards due to specifics around the OpenGL implementation. This means these will not work with a AMD or Intel-based graphics chip, nor will they work within a virtual machine. If you see errors about "glsl shader programs," this likely means you're in this camp.

## To install

- Open the Localization perspective

### Step one: Derived Parameters

- Navigate to D2D->Derived Parameters->Definitions.
- Right-click on `Definitions` and import the `SatFog.xml` and `SatMoisture12u10u.xml` files.
- Right-click on `goesr` and import each `.xml` file.
- Import the files within the `natColor` folder to the `goesr` folder in Localization.
- One by one, right-click on the imported `CIMSSGOES16`-prefixed files and select _Move to...->New File_
- Provide the path `natColor/` followed by the exact file name you are moving. Do this for each of the three CIMSS files.
- Import the files within the `sandwich` folder to the `goesr` folder in Localization.
- Similarly to what we did with the `natColor` files, you'll need to right-click on each of the `goesrSandwich`-prefixed files, select `Move To...`, and then `New File...`.
- Provide the path `sandwich/` followed by the exact file name you are moving. Do this for each of the three `goesrSandwich` files.
- We're done within `definitions`. Now, navigate up to `functions`.
- Right-click on the `functions` folder and import the three files within the `functions` folder in this repo.

### Step two: Install bundles

- Navigate to CAVE->Bundles->satellite->goesr.
- Right-click on `goesr` and select `Import File...`
- Import the goesrRGBRecipe-prefixed files.

### Step three: Install menus

- Navigate to CAVE->Menus->satellite->goesr.
- Right-click on `goesr` and select `Import File...`
- Import the goesrRGBComposites.xml file.

Restart CAVE for your changes to take effect.
