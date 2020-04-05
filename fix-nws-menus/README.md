# NWS AWIPS menu fixes

The menu system in Unidata AWIPS vs. the NWS CAVE client has some key differences, particularly around models and how observations are displayed. Worse yet, some menus have been completely deleted in the Unidata build, so when firing up a NWS client, there are several error messages regarding menus every time.

This folder contains menu files that can be imported into your localization to squelch error messages and bring models back. It also contains a simplified radar menu (eliminating the unnecessary-to-the-general-public "dial radar" nomenclature).

## To install

Installing these menu files requires the Localization perspective to be available.

- Open the Localization perspective in your NWS client.
- Navigate to CAVE->Menus.
- Begin to import files, matching the paths in this repository. Right-click on a subfolder of Menus (such as `ffmp`), and choose `Import File...`. You will be presented with a file picker. Navigate to the directory containing the files from this repository, choose the name of the folder you are importing, and then begin importing each file within that folder until you're done.
- Repeat these steps until you are through each folder. (Yes, I know how manual of a process this is, and yes, I know how terrible it can be.)
- After you are done, restart CAVE, and you should see your new, functioning menuNavigate to CAVE->Menus.
- Begin to import files, matching the paths in this repository. Right-click on a subfolder of Menus (such as `ffmp`), and choose `Import File...`. You will be presented with a file picker. Navigate to the directory containing the files from this repository, choose the name of the folder you are importing, and then begin importing each file within that folder until you're done.
- Repeat these steps until you are through each folder. (Yes, I know how manual of a process this is, and yes, I know how terrible it can be.)
- After you are done, restart CAVE, and you should see your new, functioning menus.
