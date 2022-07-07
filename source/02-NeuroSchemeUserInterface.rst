==========================
NeuroScheme User Interface
==========================

--------------
NeuroScheme UI
--------------

After loading a scene the user will be presented with the pane view containing all the entities in a grid visualization (:numref:`fig1`). 

.. _fig1:

.. figure:: images/NSImage008.png
   :alt: NeuroScheme user interface.
   :align: center

   NeuroScheme user interface.  

----------------
NeuroScheme Menu
----------------

The application menu provides actions to load and save data, and to configure several options.

^^^^^^^^^
File Menu
^^^^^^^^^

The **File** menu provides the actions:

- **Clean Scene**: Removes the loaded data and cleans the view. 
- **Import JSON**: Loads scene data in JSON format. 
- **Export JSON**: Saves the current scene to disk in JSON format. 
- **Load BlueConfig**: Disabled.
- **Load XML Scene**: Loads scene in NeuroML format (XML).
- **Quit**: Exits the application. 

^^^^^^^^^^
Panes Menu
^^^^^^^^^^

The **Panes** menu provides actions to open and close view panes:

- **Split Vertically**: Splits the current pane into two vertical panel. 
- **Split Horizontally**: Splits the current pane into two horizontal panes.
- **Kill pane**: Closes the current pane.


^^^^^^^^^
View Menu
^^^^^^^^^

The **View** menu provides options to configure the panes visualization:

- **Home**: 
- **Show connectivity**: Shows or hides the connections between the entities in the scene. 
- **Show non-hierarchical entities**: Shows or hides non-hierarchical entities in the scene.
- **Show entities name**: Shows or hides the names of the entities in the scene. 

^^^^^^^^^^^
Events Menu
^^^^^^^^^^^

The **Events** menu provides actions regarding the communication with other applications:

- **Auto publish selection**: Enables or disables the automatic publication of selections in the scene. 
- **Publish selection**: Published the current selected entities. 
- **Send auto focus event on display**: Enables or disables the publication of a focus event on display.
- **Focus event on displayed**: Publishes a focus event on the displayed entities. 
- **Send focus on selection**: Publishes a focus event on the selected entities. 
- **Auto focus on selection**: Enables or disables the automatic publication of a focus event on the selected entities.

^^^^^^^^^^
Tools Menu
^^^^^^^^^^

The **Tools** menu provides options to execute and configure the recording feature.

- **Recorder**: Shows the recorder configuration dialog and starts recording if the user clicks the **Start Recording** button.
- **Advanced recorder options**: Enables or disables additional recorder options in the configuration dialog.

^^^^^^^^^
Help Menu
^^^^^^^^^

The **Help** menu provides access to the **About** dialog that shows information about the application. 

- **About...**: Displays the about dialog. 

-------------------------------
NeuroScheme Application Toolbar
-------------------------------

The application bar presents several icons to perform actions such as sending events, showing or properties of the entities in the scenes (:numref:`fig2`). 

.. _fig2:

.. figure:: images/NSImage001.png
   :alt: NeuroScheme application toolbar
   :align: center

   NeuroScheme application tool bar. 

From left to right:

- **Home**: Resets the view. 
- **Show connectivity**: Shows/Hides the entities relationships. 
- **Show non-hierarchical entities**: Shows/Hides non-hierarchical entities. 
- **Show entities name**: Shows/Hides the entities' name. 
- **Clean scene**: Removes the scene and clears the view. 
- **Search and filter**: Opens the panel to sort or filter entities based on its properties. 
- **Saved selections**: Opens the panel to save or restore a selection of entities. 
- **Connect/Disconnect ZeroEQ**: Connects/Disconnects the application from ZeroEQ events. 
- **Publish Selection**: Publishes the currently selected entities. 
- **Auto publish selection**: Enables/Disables the automatic publication of selected entitites. 
- **Send focus event of selected entitites**: Sends a focus event on the currently selected entitites. 
- **Automatically send focus event on selection**: Enables/Disables the automatic publication of a focus event on the selected entities. 
- **Send focus event of displayed entitites**: Sends a focus event on the currently displayed entities. 
- **Automatically send focus event on displayed**: Enables/Disables the automatic publication of a focus event on the displayed entities. 
- **Recorder**: Shows the recorder configuration dialog and starts recording if the user clicks on the **Start** button. 

--------
Recorder
--------

The recording feature can be activated using the **Tools** menu or by clicking the **Recorder** icon in the toolbar. The user will be presented with the recorder configuration dialog (:numref:`figA`).

.. _figA:

.. figure:: images/NSImage009.png
   :alt: Recorder configuration dialog.
   :align: center

   Recorder configuration.

The recorder will generate a Matroska MKV video if the media application **ffmpeg** is detected and available, if not the generated output will be individual frames. The **frames per second** of the output can be specified here. The user can choose explicilty which worker (video or frames) to use to generate the output in the advanced configuration dialog (:numref:`figB`) (enabled using the **Advanced recorder options** checkbox in the **Tools** menu).

.. _figB:

.. figure:: images/NSImage010.png
   :alt: Recorder advanced configuration dialog.
   :align: center

   Recorder advanced configuration dialog.

Using the **advanced configuration** an area of the application can be selected for recording or an individual widget.

If the output is a video the user can specify the location of the generated file using the **Select** button. If the output is a sequence of frames the user can specify the destination directory using the **Select** button in the dialog.

The dimensions of the output are shown and can be modified with the **scale** options. 

While the recorder is working the associated toolbar button will remain down and the icon will change every second with an image of a "Stop" button with REC letters written inside it. The user must click it again to stop the recording. The recorder can also be stopped using the **Recorder** button in the **Tools** menu or the keyboard shortcut **Ctrl + R**.

.. note::
   If the output is a video the filename of the output file will end with "_temporal" while recording. Once the recording has finished it will change to the selected output name in the configuration dialog. The application will warn if the user tries to exit the application while a recording is being made.


.. warning::
   To record a video the system must have **ffmpeg** installed, preferably with Nvidia hardware acceleration. 
   If ffmpeg is not available in the system only the **images** worker will be available in the recorder.

------
Panels
------

^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Layout, search and filter panel
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

The **layout, search and filter** panel allows the manipulation of the visualization of the selected view pane (:numref:`fig3`). 

The **layout** allows the modification of the representation of the entities. The graph can be configured as:

- **Grid**: Entities placed as a grid, with the options to set the X and Y coordinates padding. 
- **3D**: Entities placed in 3D positions. 
- **Scatterplot**: Entities placed as a X/Y plot. The options allow the user to specify the properties represented in the X and Y axis.
- **Circular**: Entities placed in a circle, with the option to specify the radius of the representation. 
- **Free**: In this mode the entities can be selected by the mouse left button and, once selected, can be moved holding down the shift key and moving the mouse. The entities can be placed anywhere on the pane view. 

.. _fig3:

.. figure:: images/NSImage002.png
   :alt: Layout panel
   :align: center

   Layout part of the panel. 

^^^^^^^^^^^^^^^
Selection panel
^^^^^^^^^^^^^^^

The entities can be selected in the view pane by left clicking on them. The selection panel allows the user to store the selection, or to restore or delete an old selection (:numref:`fig4`). 

.. _fig4:

.. figure:: images/NSImage003.png
   :alt: Selection panel
   :align: center

   Selection panel. 

When a selection is stored it will ask the user for a name for the selection (:numref:`fig5`). 

.. _fig5:

.. figure:: images/NSImage006.png
   :alt: Selection name dialog. 
   :align: center

   Selection name dialog. 

^^^^^^^^^^^^^^^^^^^^^^^
Entity inspection panel
^^^^^^^^^^^^^^^^^^^^^^^

The entity inspection panel can be opened by using the context menu (right mouse click) on any entity and allows the modification of the properties of the entity. The entity can be deleted from the model using this panel (:numref:`fig6`). 

.. _fig6:

.. figure:: images/NSImage004.png
   :alt: Entity inspection panel.
   :align: center

   Entity inspection panel. 

^^^^^^^^^^^^^^^^^^^^^^
Connections list panel
^^^^^^^^^^^^^^^^^^^^^^

The **connections list panel** can be opened by using the context menu (right mouse click) on any entity and allows the modification or removal of the relationships between entities (:numref:`fig7`). 

.. _fig7:

.. figure:: images/NSImage005.png
   :alt: Connections list panel.
   :align: center

   Connections list panel. 

^^^^^^^^^^^^^^^^^^^^^^^^^^
Connection inspector panel
^^^^^^^^^^^^^^^^^^^^^^^^^^

The **connection inspector panel** can be opening by hovering over a connection and using the context menu (right mouse click). It allows the modification of the connection properties (:numref:`fig8`). 

.. _fig8:

.. figure:: images/NSImage007.png
   :alt: Connection inspector panel.
   :align: center

   Connection inspector panel. 

------------- 
Context menus
-------------

^^^^^^^^^^^^^^^^^^^
Entity context menu
^^^^^^^^^^^^^^^^^^^

The entity **context menu** provides access to several panels to visualize and modify the properties of the entity or the entity itself. The default entries are:

- **Edit**: shows the entity inspection panel. 
- **Delete**: removes the entity from the view pane. 
- **Duplicate**: duplicates the entity. 
- **Show connections**: opens the connections list panel. 

Other entries can appear depending on the current model configuration, and depend on the entity being clicked. 

^^^^^^^^^^^^^^^^^^^^^^^
Connection context menu
^^^^^^^^^^^^^^^^^^^^^^^

The connections also have a context menu with a default entry:

- **Edit relationship**: Shows the connection inspector panel to edit connection properties. 

^^^^^^^^^^^^^^^^^
Pane context menu
^^^^^^^^^^^^^^^^^

If the context menu is requested when the mouse is not hovering an entity or a connection the view panel context menu is show. This menu allows the user to add entities and inputs/outputs. 

------------------
Keys and shortcuts
------------------

The following actions can be performed by clicking the button, selecting the option at menu bar and pressing the corresponding key combination:

- **Ctrl + K**: Close current view pane. 
- **Ctrl + H**: Home. 
- **Ctrl + C**: Show/Hide connectivity in the view panes. 
- **Ctrl + I**: Show/Hide non-hierarchical entities.  
- **Ctrl + S**: Publish selection event. 
- **Ctrl + R**: Launch recorder.
- **Ctrl + Q**: Close application.
