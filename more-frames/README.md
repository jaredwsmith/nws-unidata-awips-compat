# Enable more frames in NWS AWIPS

The NWS baseline CAVE client maxes out at 64 frames in the Frames dropdown menu in the toolbar, while Unidata AWIPS can go as high as 500 frames. This patch changes this for NWS clients, adding a `> 64` option to the Frames dropdown menu with options to go as high as 500 frames, incremented by 50.

*PREREQUISITE*: Must be able to become an administrator/root on your Windows or Linux computer.

*_NOTE_*: This will not survive upgrades to subsequent versions of AWIPS, and will need to be reapplied each time.

## To install

- Close CAVE if it is open.
- Copy the modified `plugin.xml` file from this repository to the plugin folder. On Windows, it will be in `C:\Program Files\Raytheon\AWIPS II\CAVE\plugins\com.raytheon.uf.viz.d2d.ui_1.18.0.201906111150`. On Linux, it will be in `/awips2/cave/plugins/com.raytheon.uf.viz.d2d.ui_1.18.0.2019110413`. (The version number and datestamp at the end may vary based on build). You will be asked to elevate to an adminstrator on Windows; on Linux, you should execute the command as root or by elevating with
  `sudo`.
- Open CAVE and check your Frames toolbar item.
