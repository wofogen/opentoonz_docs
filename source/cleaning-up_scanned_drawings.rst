.. _cleaning-up_scanned_drawings:

Cleaning-up Scanned Drawings
============================
In order to be painted and edited with OpenToonz, scanned drawings have to undergo the cleanup process. The process involves autocentering, to align each drawing according to the pegbar holes; line processing, to recognize the drawing outline; image cropping and re-sizing, to make the drawings fit properly the camera.

The process generates a Toonz raster level (TLV format) and the related default palette (TPL format), where the styles used to paint the level will be stored.




.. note:: If the computer performance slows down during the cleanup process of very high resolution images, try activating the Minimize Raster Image Fragmentation option in the Files > Preferences > General dialog (see  :ref:`Optimizing the Memory Usage <optimizing_the_memory_usage>`  ).

.. _the_cleanup_settings:

The Cleanup Settings
--------------------
The cleanup process can be controlled by using the Cleanup Settings that include Cleanup, Processing and Camera parameters.

Usually settings are defined and checked for one of the level drawings, then applied to the whole animation level. If all of the drawings in the scene have the same characteristics, it is very likely that the same settings can be used for every drawing throughout all of the animation levels.

.. tip:: **To define cleanup settings:**

    Choose Scan & Cleanup > Cleanup Settings and use the dialog to control the cleanup process parameters and options. 

.. _defining_cleanup_parameters:

Defining Cleanup Parameters
'''''''''''''''''''''''''''



The Cleanup parameters set the autocentering information and some geometric transformations.

.. _autocentering:

Autocentering
~~~~~~~~~~~~~
The Autocenter option aligns lineart drawings and full-color images according to the shape and position of the pegbar holes, in order to set the correct registration for them once they are used in an animation scene.

Pegbar holes have to be included properly during the scanning process in order to be recognized during the process (see  :ref:`Scanning Guidelines for Autocentering <scanning_guidelines_for_autocentering>`  ). 

When the autocenter fails because it is not possible to recognize properly the pegbar holes, an error message is displayed; yet the drawings and images are processed according to the other set parameters.

Autocenter parameters are the following:

- Autocenter, when activated, triggers the autocenter process. 

- Pegbar Holes sets the side of the drawing along which holes should be detected.

- Field Guide specifies the size of the reference field guide that has to be used to set the center of the processed drawings and images, and the type of pegbar holes that have to be detected (such as Acme or Oxbry).

.. tip:: **To check the autocenter on a selected drawing:**

    1. Activate the Autocenter option.

    2. Set the side where Pegbar Holes have to be detected.

    3. Set the Field Guide to be used as reference to set the center in the correct place, and to match the shape of the pegbar holes.

    4. Choose Scan & Cleanup > Preview Cleanup to preview the process.

.. _other_cleanup_parameters:

Other Cleanup Parameters
~~~~~~~~~~~~~~~~~~~~~~~~
The Cleanup page contains also other parameters that can be activated regardless of the autocenter, as they will affect processed images even if the Autocenter option is not activated. Parameters are the following:

- Rotate rotates the image by 90° steps clockwise. It can be used to set the right orientation for images scanned with a different direction in order to fit the scanner bed.

- Flip mirrors the image horizontally, vertically or both, according to the activated options. It can be used, for example, when processing a shadow level drawn on the other side of the paper where the character level is drawn, in order to match the two animation levels later.

- Save in lets you define the folder where the cleaned up drawings are saved. By default it is set to the +drawings default folder of the current project (see  :ref:`Project Default Folders <project_default_folders>`  ). 

.. _defining_line_processing_parameters:

Defining Line Processing Parameters
'''''''''''''''''''''''''''''''''''
The Processing parameters set the line processing options in order to prepare drawings for the painting process, recognizing black lines in black and white, or grayscale lineart drawings, or colored lines in colored lineart drawings. 

The line recognition process can also be skipped in case you are doing the cleanup only for registering full-color images, such as backgrounds, that were scanned including pegbar holes. 

.. tip:: **To set the type of line processing:**

    Set the Line Processing option to None, if no line processing is required, Greyscale, if lines have to be recognized as black, or Color, if lines have to be recognized as colored.

.. _processing_black_and_white_or_greyscale_lineart_drawings:

Processing Black and White or Greyscale Lineart Drawings
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
 |Toonz71_037| 

For black and white or greyscale lineart drawings, a set of parameters are available to calibrate the black line recognition process. 

The result of the process can be previewed both in the preview area available at the bottom of the Cleanup Settings window, and in the OpenToonz viewer (see  :ref:`Previewing the Cleanup Process <previewing_the_cleanup_process>`  ).

Parameters are the following:

- Antialias can be set to Standard, None or Morphological. Use Standard to keep the antialias resulting from current camera and defined settings. Use None to eliminate the antialiasing from the processed line, so that the resulting line will be fully solid with no semi-transparent pixels smoothing its edges. Use Morphological to replace the standard antialias with the one obtained analyzing the image edges.

- Autoadjust corrects the levels of grey in the drawings in order to avoid darker and lighter drawings in a sequence (see  :ref:`Autoadjusting Greyscale Lineart Drawings <autoadjusting_greyscale_lineart_drawings>`  ). 

- Sharpness defines how sharp the processed lines will be. Higher values produce sharper, harder lines, and lower values create smoother lines. 

- Despeckling removes small spots or marks from the processed images. Its value expresses the size in pixels of the side of the maximum area that has to be removed. The spots and marks removed by this option can also be checked by activating the Opacity Check (see  :ref:`Using the Opacity Check <using_the_opacity_check>`  ).

- MLAA Intensity sets the intensity of the morphological antialias. The higher the value the more blurred the line. (It is available only when Morphological is selected).

- Brightness controls the thickness of the recognized line: the lower the value, the thicker the line.

- Contrast controls the antialiasing of the recognized line: a higher value produces more solid pixels, a lower value more antialiasing pixels. The amount of antialiasing can also be checked by activating the Opacity Check (see  :ref:`Using the Opacity Check <using_the_opacity_check>`  ).

.. note:: If the Antialias is sets on None or Morphological, the Contrast parameter will not be effective.

.. tip:: **To set the line processing for black and white or greyscale lineart drawings:**

    1. Activate the Line Processing > Greyscale option.

    2. Define the parameters according to your needs.

    3. Preview the result of the cleanup process (see  :ref:`Previewing the Cleanup Process <previewing_the_cleanup_process>`  ).

.. _autoadjusting_greyscale_lineart_drawings:

Autoadjusting Greyscale Lineart Drawings
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
The Autoadjust option available among the Cleanup parameters allows you to even the differences between drawings made by key animators and those made by in-betweeners by adjusting the line darkness of all of the level drawings.

.. note:: The Autoadjust option has effect only on drawings scanned in greyscale mode, while it has no effect on drawings scanned in black and white. 

Three different autoadjust algorithms are available:

- Black Eq computes the average of the darkest grey tone found in drawing lines below a certain threshold and sets this value to the conventional black level, so that grey levels of each image are automatically adjusted.

- Histogram makes a histogram of the grey levels of the first image and equalizes the histograms of the following images according to it. It works well when the content of the images (apart from line darkness) does not vary too much across the level.

- Histo-L takes into account the number of lines in each image to normalize the histogram of grey levels, before the histogram equalization is performed. This is useful for example when a character becomes bigger or smaller in an animated level, or when parts of the character are animated independently in some frames. 

.. note:: The advantage of the Histo-L mode over the others is that it adjusts the grey levels of each image independently, while the other algorithms equalize each image to make it look like the first one of the level.

Only the effects of the Black Eq process can be checked using the Scan & Cleanup > Cleanup Preview command; the effects of Histogram and Histo-L are only visible selecting a sequence of at least two frames (i.e. one as reference frame and the others to be auto-adjusted) and processing them using the Scan & Cleanup > Cleanup command. You may need to make a few trials using different algorithms before obtaining the desired results. 

.. note:: These algorithms work on the area of the drawing specified in the Field text boxes, excluding a 5 mm boundary edge. In this way any line might be drawn to delimit the camera shot on paper, and the pegbar holes, do not affect the result.

.. _processing_colored_lineart_drawings:

Processing Colored Lineart Drawings
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
 |Toonz71_038| 

For colored lineart drawings, a set of parameters are available to calibrate the line recognition process, and to set which and how colors have to be detected in the drawings (see  :ref:`Defining Colors for the Color Line Processing <defining_colors_for_the_color_line_processing>`  ).

For all the cleanup colors you can define a color to be assigned automatically to the lines after the processing, with no need to paint them. The two colors, the one used for the recognition and the one to be assigned after the recognition, are available in the bottom area of the Style Editor.

Different parameters are available for the black color, that usually defines the main outline in lineart drawings, and for the additional colors, that usually defines special outlines for areas such as shadows and highlights.

The result of the process can be previewed both in the preview area available at the bottom of the Cleanup Settings window, and in the OpenToonz viewer (see  :ref:`Previewing the Cleanup Process <previewing_the_cleanup_process>`  ).

General parameters are the following:

- Antialias can be set to Standard, None or Morphological. Use Standard to keep the antialias resulting from current camera and defined settings. Use None to remove the antialiasing from the processed line, so that the resulting line will be fully solid with no semi-transparent pixels smoothing its edges. Use Morphological to replace the standard antialias with the one obtained analyzing the image edges.

.. note:: If the Antialias is sets on None or Morphological, the Contrast parameter will not be effective.

- Sharpness defines how sharp the processed lines will be. Higher values produce sharper, harder lines, and lower values create smoother lines. 

- Despeckling removes small spots or marks from the processed images. Its value expresses the size in pixels of the side of the maximum area that has to be removed. The spots and marks removed by this option can also be checked by activating the Opacity Check (see  :ref:`Using the Opacity Check <using_the_opacity_check>`  ).

- MLAA Intensity sets the intensity of the morphological antialias. The higher the value the more blurred the line. (It is available only when Morphological is selected).

In the color list, parameters for the black color are the following:

- Brightness controls the thickness of the recognized line: the lower the value, the thicker the line.

- Contrast controls the antialiasing of the recognized line: a higher value produces more solid pixels, a lower value more antialiasing pixels. The amount of antialiasing can also be checked by activating the Opacity Check (see  :ref:`Using the Opacity Check <using_the_opacity_check>`  ).

- Color Threshold sets pixels that have to be considered black and those that have to be considered colors: the higher the value, the higher the number of pixels that will be considered as colored.

- White Threshold sets pixels that have to be considered white, for example to eliminate the paper color: the higher the value, the higher the number of pixels that will be considered as white.

In the color list, parameters for the other colors are the following:

- Brightness controls the thickness of the recognized colored line: the lower the value, the thicker the line.

- Contrast controls the antialiasing of the recognized colored line: a higher value produces more solid pixels, a lower value more antialiasing pixels. The amount of antialiasing can also be checked by activating the Opacity Check (see  :ref:`Using the Opacity Check <using_the_opacity_check>`  ).

- H Range sets the range of hue for the color recognition: the higher the value, the higher the number of differently colored pixels that will be associated to the set color.

- Line Width sets the width of the recognized colored line: the higher the value, the higher the number of desaturated pixels that will be associated to the set color, thus increasing the line thickness.

.. tip:: **To set the line processing for colored lineart drawings:**

    1. Activate the Line Processing > Color option.

    2. Define the general parameters according to your needs.

    3. Define the colors you want to be detected in the drawings (see  :ref:`Defining Colors for the Color Line Processing <defining_colors_for_the_color_line_processing>`  ).

    4. Define the color parameters according to your needs.

    5. Preview the result of the cleanup process (see  :ref:`Previewing the Cleanup Process <previewing_the_cleanup_process>`  ).

.. _defining_colors_for_the_color_line_processing:

Defining Colors for the Color Line Processing
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
The colors used to recognize and process drawing lines when doing color line processing can be defined by using the style editor or picking color values directly from the drawing you want to process

It is possible to add colors to the list, or removed them if they are not needed. The maximum number of color you can define is seven (black included). 

.. note:: The first color of the list, i.e. the black color, cannot be edited or removed.

.. tip:: **To define colors:**

    1. Select the color you want to define in the list available in the Processing parameters.

    2. Define the color by doing one of the following:

    - Use the style editor (see  :ref:`Editing Styles <editing_styles>`  ).

    - Use the RGB Picker tool (|RGB_picker|) to pick the value of the line color from the drawings visible in the work area (see  :ref:`Plain Colors <plain_colors>`  ).

.. tip:: **To define colors to be assigned to lines after cleanup processing:**

    1. Select the color for which you want to define the post-process color.

    2. At the bottom of the Style Editor select the square on the right of current color: it is the color to be assigned after the processing.

    3. Edit the color in the Style Editor.

.. tip:: **To add a color in the color list:**

    Click the + button available under the color list.

.. tip:: **To remove a color from the color list:**

    1. Select the color you want to remove from the list.

    2. Click the - button available under the color list.

.. _defining_camera:

Defining Camera
'''''''''''''''
 |Toonz71_040| 

The Camera parameters define the size and resolution of the camera that is used to crop and resize drawings during the cleanup process, in order to prepare and optimize them for the scene.

For example if the cleanup camera is 768x576 pixels (PAL) with a 12 field size, the cleaned up drawings will be cropped according to the 12 field size and will have the resolution of 768x576 pixels.

The cleanup camera definition is similar to the definition of the stage camera (see  :ref:`Defining Camera Settings <defining_camera_settings>`  ). Usually the two cameras have the same parameters, but sometimes you may need to define a cleanup camera that is larger than the stage camera especially if you want drawings border area to overflow the shot. 

You can also set other parameters and options:

- The Closest Field defines the smallest field size you will zoom into the drawing with the camera when compositing the scene. This value is meaningful if it is smaller than the camera field size, as it increases the final image resolution, preventing zoomed-in images from appearing jagged. For example if the cleanup camera is 768x576 pixels (PAL) with a 12 field size and the closest field is set to 6, the cleaned up drawings will have twice the camera resolution, that is 1536 by 1152 pixels. 

- The E/W and N/S Offset shifts the camera position in case you want to define for the drawings a center different from the one automatically set by the reference field guide when the autocenter is on, or different from the actual center of the image if the autocenter is off; after the cleanup the camera center will be the new center for the processed drawings.

The cleanup camera size, resolution and offset can also be graphically controlled in the viewer when checking the cleanup process with the Camera Test mode (see  :ref:`Using the Camera Test <using_the_camera_test>`  ).

.. _saving_and_loading_cleanup_settings:

Saving and Loading Cleanup Settings
'''''''''''''''''''''''''''''''''''
Cleanup settings can be saved as CLN files in order to be loaded back and used in a different scene. 

They can also be associated specifically to an animation level by saving them in the same location and with the same name of the level: in this way the settings will be automatically displayed when the level is selected, and used every time the level is cleaned up.

Loaded cleanup settings can also become the default settings for the scene or for the project (see  :ref:`Scene Settings and Project Default Settings <scene_settings_and_project_default_settings>`  ). 

.. tip:: **To save the cleanup settings:**

    1. Select an empty cell in the xsheet.

    2. Click the Save Settings button (|save|) in the bottom bar of the cleanup settings window.

    3. In the browser that opens choose for the CLN file a location and name, and click the Save button.

.. tip:: **To load saved cleanup settings:**

    1. Select an empty cell in the xsheet.

    2. Click the Load Settings button (|load|) in the bottom bar of the cleanup settings window.

    3. In the browser that opens retrieve the CLN file you want to load, and click the Load button.

.. tip:: **To save the current cleanup settings for a specific level:**

    1. Select any cell where the level is exposed in the xsheet.

    2. Click the Save Settings button (|save|) in the bottom bar of the cleanup settings window.

    3. In the browser that opens save the CLN file in the same location and with the same name as the level, and click the Save button.

.. tip:: **To load cleanup settings for a specific level:**

    1. Select any cell where the level is exposed in the xsheet.

    2. Click the Load Settings button (|load|) in the bottom bar of the cleanup settings window.

    3. In the browser that opens retrieve the CLN file you want to load, and click the Load button.

    4. Click the Save Settings button (|save|) and in the browser that opens save the CLN file in the same location and with the same name as the level, and click the Save button.

.. tip:: **To reset cleanup settings to the scene default:**

    Click the Reset Settings button (|reset|) in the bottom bar of the cleanup settings window.



.. _checking_the_cleanup_process:

Checking the Cleanup Process
----------------------------
While defining the cleanup settings it is possible to preview the full cleanup process, or perform the camera test only, in order to check the result before performing the final cleanup.

.. _previewing_the_cleanup_process:

Previewing the Cleanup Process
''''''''''''''''''''''''''''''
The full cleanup process can be checked both in the preview area available in the cleanup settings window, and in the main viewer. 

.. _using_the_preview_area_in_the_cleanup_settings_window:

Using the Preview Area in the Cleanup Settings Window
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
At the bottom of the cleanup settings window a preview area is available to display the drawing selected in the xsheet as it will be after the real cleanup process according to the defined cleanup settings. At the same time it allows you to compare the final result with the original scanned drawing that is displayed on the left side. 

You can activate or deactivate it, resize it or navigate its content.

Using this preview area is faster than checking the cleanup process in the main viewer because the set processing parameters are applied only to the visible part of the drawing, and not to the drawing as a whole.

If you change any parameter in the cleanup settings, the previewed drawing automatically updates to display how the changes affect the process.

.. tip:: **To activate the preview area:**

    In the xsheet select the scanned drawing you want to preview, and click the Preview button (|preview|) in the bottom bar of the cleanup settings window.



.. tip:: **To deactivate the preview area:**

    Click the Preview button (|preview|) in the bottom bar of the cleanup settings window.



.. tip:: **To resize the preview area:**

    Do any of the following:

    - Click and drag the horizontal separator. 

    - Click and drag the separator toward the window border to hide the preview area.

    - Click and drag the separator collapsed to the window border toward the window center to display again the preview area.

.. tip:: **To navigate the preview area:**

    Do one of the following:

    - Use the mouse wheel, or the zoom shortcut keys (by default + and - keys) to zoom in and zoom out.

    - Middle-click and drag to scroll in any direction.

    - Use the reset view shortcut (by default the 0 key) to display preview at its actual size.

.. _previewing_the_cleanup_process_in_the_main_viewer:

Previewing the Cleanup Process in the Main Viewer
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
A cleanup preview can be activated in the main viewer to display the drawing selected in the xsheet as it will be after the real cleanup process according to the defined cleanup settings, displaying at the same time all the other drawings and images exposed in the xsheet at that frame.

If you change any parameter in the cleanup settings, the preview automatically updates to display how the changes affect the process.

.. note:: The Opacity Check when activated, affects also the cleanup preview in the main viewer (see below ).

.. note:: The Preview Cleanup and the Camera Test checks cannot be activated at the same time: when one is activated the other one is automatically deactivated.

.. tip:: **To activate the cleanup preview in the main viewer:**

    In the xsheet select the scanned drawing you want to preview, and choose Scan & Cleanup > Preview Cleanup. 

.. tip:: **To deactivate the cleanup preview in the main viewer:**

    Choose Scan & Cleanup > Preview Cleanup. 

.. tip:: **To preview a different drawing:**

    Select it in the xsheet.

.. tip:: **To exit the preview cleanup mode:**

    Choose Scan & Cleanup > Preview Cleanup to deactivate it. 

.. _using_the_opacity_check:

Using the Opacity Check
~~~~~~~~~~~~~~~~~~~~~~~
When calibrating the line processing it is important to check the amount of antialiasing along the drawing outline to understand how smooth the result will be, and to check the small spots and marks that are removed from the drawing because of the despeckling function (see  :ref:`Defining Line Processing Parameters <defining_line_processing_parameters>`  ). 




The opacity check, when activated, displays fully solid pixels in black, and semi-transparent pixels belonging to the line antialiasing in red; moreover pixels that will be removed because of the despeckling function are displayed in green.

The check is visible both in the preview area of the cleanup settings and in the cleanup preview performed in the main viewer.

.. tip:: **To activate and deactivate the opacity check:**

    Click the Opacity Check button (|check|) in the bottom bar of the cleanup settings window.



.. _using_the_camera_test:

Using the Camera Test
'''''''''''''''''''''
The camera test can be used to check the cleanup process as concerning the Cleanup and the Camera parameters. It displays the drawing selected in the xsheet directly in the viewer without line processing but with the position modified according to the Cleanup parameters (Autocenter, Rotate and Flip), and the size modified according to the Camera parameters. In particular a red box displays how the cleanup camera will crop the drawing, and a blue box displays the camera closest field. 

It is possible to modify the camera box directly in the viewer thus updating the cleanup camera information visible in the cleanup settings dialog (see  :ref:`Defining Camera <defining_camera>`  ).

If you change any of the Cleanup or Camera parameters, the camera test automatically updates to display how the changes affect the process.

.. note:: The Preview Cleanup and the Camera Test checks cannot be activated at the same time: when one is activated the other one is automatically deactivated.

.. tip:: **To activate the camera test:**

    In the xsheet select the drawing you want to preview, and choose Scan & Cleanup > Camera Test. 

.. tip:: **To deactivate the camera test:**

    Choose Scan & Cleanup > Camera Test. 

.. tip:: **To modify the cleanup camera directly in the viewer:**

    Do any of the following:

    - Operate the handles on the top and right edges to scale the camera size horizontally or vertically, thus changing the camera A/R as well.

    - Operate the handle on the top right corner to scale the camera size while keeping the A/R.

    - Activate the DPI Lock in the cleanup camera parameters, and operate the handles to scale also the camera resolution.

    - Move the camera box to modify the cleanup camera E/W and N/S offset.

.. tip:: **To perform the camera test on a different drawing:**

    Select it in the xsheet.

.. tip:: **To exit the camera test mode:**

    Choose Scan & Cleanup > Camera Test to deactivate it. 

.. _cleaning_up_drawings:

Cleaning up Drawings
--------------------
Once the cleanup settings are defined and the process is checked, it is possible to cleanup all of the drawings of the scene, or a selection of them.

Drawings can be processed directly inside the scene after performing a selection, or they can be processed automatically in batch mode. 

In both cases they will be cleaned up according to the Cleanup Settings defined for the scene, unless a specific CLN file was saved for any of the animation levels in the scene.

By default cleaned up drawings are saved in the +drawings directory of the current project (see  :ref:`Project Default Folders <project_default_folders>`  ), but you can change the location by using the Save In option available in the cleanup settings dialog. 

Cleaned up animation levels are saved as TLV files; the related palettes are saved in the same location and with the same name of the animation levels as TPL files.

It is also possible to automatically create a backup copy of the cleaned up drawings in the same location where the cleaned up drawings are saved. In this way it will be possible to retrieve the original drawing in case some mistakes, e.g. a deletion of a drawing section, are made during the painting process.

.. tip:: **To automatically create a backup copy of the cleaned up drawings:**

    1. Choose File > Preferences > Drawing.

    2. Activate the Keep Original Cleaned Up Drawings As Backup option.

.. tip:: **To revert to the original cleaned up drawings:**

    1. In the level strip select the drawings you want to revert (see  :ref:`Using the Level Strip <using_the_level_strip>`  ).

    2. Do one of the following:

    - Choose Level > Revert to Cleaned Up.

    - Right click the selection and choose Revert to Cleaned Up from the menu that opens.

.. _cleaning_up_drawings_directly_in_the_scene:

Cleaning up Drawings Directly in the Scene
''''''''''''''''''''''''''''''''''''''''''
 |Toonz71_051| 

When cleaning up drawings directly in the scene it is possible to perform a selection of drawings and process them with the current cleanup settings. In this case you can also manage the process frame by frame, as you are prompted to choose an action for each drawing of the selection.

You can also select non-consecutive drawings and drawings from different animation levels. Levels will be processed starting from the first selected column, considering only exposed drawings according to their numbering order.

When a drawing is cleaned up, its cell color turns from light blue to light green, the color denoting Toonz raster levels (see  :ref:`Working with Xsheet Columns <working_with_xsheet_columns>`  ). If you cleanup partially an animation level, the remaining cells where the level is exposed will have a double color (green and blue), to stress the fact that the level is partially processed.

When drawings belonging to partially processed levels are selected to be cleaned up, you are prompted whether to cleanup selected drawings overwriting the previous cleaned up version, or to add non-cleaned up frames to the existing level, or to delete the existing level and create a new level with the selected drawings only.

If you want you can also revert to the scanned version of the level you cleaned up by using the Level Settings dialog (see  :ref:`Editing Level Settings <editing_level_settings>`  ). 

.. note:: If you want to create a new TLV level from an already cleaned up level you can selet it and run the cleanup again. A questions pop up will appear and giving you the possibility to set a different name for the new TLV level by adding a suffix.

.. tip:: **To process the selection according to the chosen settings:**

    1. In the xsheet select the drawings you want to process.

    2. Choose Scan & Cleanup > Cleanup.

    3. In the Cleanup dialog for each drawing choose one of the following:

    - Cleanup: the current drawing will be cleaned up.

    - Skip: the current drawing will not be cleanup up and the dialog displays the next drawing.

    - Cleanup All: all the selected drawings will be cleaned up without further prompts.

    - Cancel: the cleanup process will be interrupted.

.. tip:: **To revert to the scanned version of a cleaned up level:**

    1. Select any drawing of the cleaned up level.

    2. Choose Level > Level Setting.

    3. Copy the Scan Path information in the Path text field.

.. _cleaning_up_drawings_in_batch_mode:

Cleaning up Drawings in Batch Mode
''''''''''''''''''''''''''''''''''
The cleanup of drawings exposed in a scene can be added to a task list and performed in batch mode in order to run it in the background while you perform other work on your computer.

Cleanup tasks can be submitted from the OpenToonz browser and can be managed and executed in the Tasks pane, together with render tasks (see for  :ref:`Rendering Scenes in Batch Mode <rendering_scenes_in_batch_mode>`  s).

The Tasks pane is divided into two sections: on the left there is the task tree where all of the cleanup tasks are displayed with a brush icon and all of the render tasks with a clapboard icon; on the right there is information about the task selected in the tree.




The task list can be saved as TNZBAT files and loaded back later in case you want to manage it through different working sessions.

.. tip:: **To save a task list:**

    1. Do one of the following:

    - Click the Save Task List (|save|) or the Save Task List As button (|save_as|) in the bottom bar of the Tasks pane.

    - Right-click the Tasks item at the top of the list and choose Save Task List or the Save Task List As from the menu that opens.

    2. Use the browser that opens to save the list.

.. tip:: **To load a task list:**

    1. Do one of the following:

    - Click the Load Task List button (|load|) in the bottom bar of the Tasks pane.

    - Right-click the Tasks item at the top of the list and choose Load Task List from the menu that opens.

    2. Use the browser that opens to retrieve and load a previously saved list.

.. tip:: **To resize the tasks pane sections:**

    Do any of the following:

    - Click and drag the separator to resize sections. 

    - Click and drag the separator toward the window border to hide a section.

    - Click and drag the separator collapsed to the window border toward the window center to display again the hidden section.

.. _managing_and_executing_cleanup_tasks:

Managing and Executing Cleanup Tasks
''''''''''''''''''''''''''''''''''''
When a cleanup task is selected in the tree, in the section on the right of the Tasks pane task-related properties are displayed, some of which can be edited to configure the task. Properties are the following:

- Name displays the tasks name; it can be edited to better identify the task. 

- Status displays if the task is waiting, running, completed or failed.

- Command Line displays the command line related to the task execution with arguments and qualifiers.

- Server displays the computer that is running, or will run, the task.

- Submitted By displays the user that submitted the task.

- Submitted On displays the computer from where the task was submitted.

- Submission Date displays when the task was submitted.

- Start Date displays when the execution of the task started.

- Completion Date displays when the execution of the task was completed.

- Duration displays how long the execution lasted.

- Step Count displays the number of frames rendered.

- Failed Steps displays the number of frames that failed to be rendered.

- Successful Steps displays the number of frames successfully rendered.

- Priority sets the importance or urgency of the task: tasks with a higher priority will be executed first. This can be edited to change the priority of a task.

- Visible Only, when activated, limits the cleanup process only to columns whose camera stand toggle (|camera_stand|) is on, that is to say whose content is visible (see 

:ref:`Working with Xsheet Columns <working_with_xsheet_columns>`  ).



    - Overwrite, when activated, processes levels even if they are already available in the destination folder, overwriting them.

    - Dependencies lets you set which of the other submitted tasks have to be successfully completed before starting the current task execution: these tasks can be added from the box on the right where all submitted tasks are displayed.

Task execution can be started and stopped from the task list. If you are using the OpenToonz render farm, render tasks and sub-tasks will be distributed on the farm, one for each computer, so that several tasks can be executed at the same time (see  :ref:`Using the OpenToonz Farm <using_the_toonz_farm>`  ). 

When the tasks are executed, the icon color tells the status of the task according to the following color code:

    - Grey, when the task is waiting or is not executed yet.

    - Yellow, when the task is being executed.

    - Green, when the task is successfully executed.

    - Orange, when the task is executed with some errors.

    - Red, when the task execution has failed.

.. tip:: **To add scenes to cleanup in the task list:**

    Do one of the following:

    - Click the Add Cleanup Task button (|add_cleanup|) in the bottom bar of the Tasks pane and use the browser to select a scene file.



    - Select the scenes in the OpenToonz Browser, then right-click any of them and choose Add As Cleanup Task from the menu that opens.

.. tip:: **To configure the cleanup task in the task list:**

    1. Select the cleanup task in the task list.

    2. Configure it by using the options available on the right of the list.

.. tip:: **To select tasks in the task list:**

    Do any of the following:

    - Click a task to select it.

    - Shift-click a task to extend the selection up to that task.

    - Ctrl-click (PC) or Cmd-click (Mac) a task to add it to, or remove it from the selection.

.. tip:: **To execute selected tasks:**

    Do one of the following:

    - Click the Start button (|start|) in the bottom bar of the pane.



    - Right-click any selected task icons and choose Start from the menu that opens.

.. tip:: **To stop the execution of selected tasks:**

    Do one of the following:

    - Click the Stop button (|stop|) in the bottom bar of the pane.



    - Right-click any selected task icon and choose Stop from the menu that opens.

.. tip:: **To remove selected tasks from the list:**

    Do one of the following:

    - Click the Remove button (|remove|) in the bottom bar of the Tasks pane.



.. tip:: **Right-click any selected task in the list and choose Remove from the menu that opens.**

.. tip:: **To add tasks to the Dependencies list:**

    - Select a task in the list on the right and click the Add button.

.. tip:: **To remove tasks from the Dependencies list:**

    - Select a task in the list on the left and click the Remove button.

.. |Toonz71_037| image:: /_static/Toonz71/Toonz71_037.gif
.. |Toonz71_038| image:: /_static/Toonz71/Toonz71_038.gif
.. |Toonz71_040| image:: /_static/Toonz71/Toonz71_040.gif
.. |Toonz71_051| image:: /_static/Toonz71/Toonz71_051.gif
.. |RGB_picker| image:: /_static/cleanup/RGB_picker.png
.. |add_cleanup| image:: /_static/cleanup/add_cleanup.png
.. |camera_stand| image:: /_static/cleanup/camera_stand.png
.. |load| image:: /_static/cleanup/load.png
.. |check| image:: /_static/cleanup/check.png
.. |preview| image:: /_static/cleanup/preview.png
.. |remove| image:: /_static/cleanup/remove.png
.. |reset| image:: /_static/cleanup/reset.png
.. |save| image:: /_static/cleanup/save.png
.. |save_as| image:: /_static/cleanup/save_as.png
.. |start| image:: /_static/cleanup/start.png
.. |stop| image:: /_static/cleanup/stop.png
