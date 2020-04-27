# Enabling the localization perspective in the NWS Thin Client

The `ThinClientPluginBlacklist.txt` file governs which Eclipse plugins are loaded by CAVE in Thin Client mode. By default, the NWS Thin Clients on both Windows and Linux shut down virtually every different perspective other than D2D. In order to add customizations to CAVE, the Localization perspective is required. This file is modified to permit the Localization perspective and its associated components to run.

*PREREQUISITE:* You will need administrator/root permissions to your computer in order to install this file.
*NOTE:* This modification will not survive an upgrade and will need to be reapplied with the next release.

To install this file and enable the Localization perspective in Thin Client:

- Close CAVE if it is open.
- Copy the modified ThinClientPluginBlacklist.txt in this repository to the plugin folder. On Windows, it will be in `C:\Program Files\Raytheon\AWIPS II\CAVE\plugins\com.raytheon.uf.viz.thinclient.cave_1.0.0.201906111150`. On Linux, it will be in `/awips2/cave/plugins/com.raytheon.uf.viz.thinclient.cave_1.0.0.201911041`. Windows should ask you to elevate to an administrator; on Linux, you'll need to issue the command either as root or using `sudo`.
- Open CAVE.
- Go to CAVE->Perspective. Select `Localization`. You're in!
