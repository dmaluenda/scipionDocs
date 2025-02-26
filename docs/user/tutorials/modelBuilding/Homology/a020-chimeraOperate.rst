.. _`app:chimeraOperate`:

ChimeraX Operate protocol
=========================

Protocol designed to perform operations with atomic structures in *Scipion* by
using *ChimeraX*. A volume or set of volumes can also be included. Structures or
maps generated by using this protocol can be saved in *Scipion* after executing
specific *ChimeraX* commands. *ChimeraX rigid fit* protocol constitutes a particular case of
this protocol to perform rigid fitting in *Scipion* by using *ChimeraX* (Appendix :ref:`CHIMERA Rigid fit <app:chimeraRigidFit>`).

-  | Requirements to run this protocol and visualize results:

   -  | *Scipion* plugin: **scipion-em**

   -  | *Scipion* plugin: **scipion-em-chimera**


-  | *Scipion* menu: *Model building -> Tools-Calculators* (:numref:`model_building_app_protocol_chimera_2` (A))

   .. figure:: Images_appendix/Fig117.svg
      :alt: Protocol **chimerax-operate**. A: Protocol location in *Scipion* menu. B: Protocol form.
      :name: model_building_app_protocol_chimera_2
      :align: center
      :width: 90.0%

      Protocol **chimerax-operate**. A: Protocol location in *Scipion* menu. B: Protocol form.

-  | Protocol form parameters (:numref:`model_building_app_protocol_chimera_2` (B)):

   -  | *Input* section

      -  | *Input Volume*: Optional parameter to be completed with the electron density map previously downloaded or generated in *Scipion*.

      -  | *Input additional Volumes*: Optional parameter to include other electron density maps previously downloaded or generated in *Scipion*.

      -  | *Atomic structure*: Atomic structure previously downloaded or generated in *Scipion*.

      -  | *Other atomic structures*: Additional atomic structures.


   -  | *Help* section

      | This section contains *ChimeraX* commands required to save *models* according to their reference volumes, which can also be saved if required. Remark that using *scipionwrite* command, *ChimeraX* session will be saved by default, without prejudice that it may be saved with *scipionss* command. *scipioncombine* command allows to merge in only one atomic structure two or more structures. *ChimeraX* sessions can be restored by using **chimerax-restore session** protocol.


-  | Protocol execution:

   | Adding specific protocol label is recommended in *Run name*
     section, at the form top. To add the label, open the protocol form,
     press the pencil symbol at the right side of *Run name* box,
     complete the label in the new opened window, press OK and, finally,
     close the protocol. This label will be shown in the output summary
     content (see below). If you want to run again this protocol, do not
     forget to set to *Restart* the *Run mode*.

   | Press the *Execute* red button at the form bottom.

   | *ChimeraX* graphics window will be opened after executing the protocol.
     Electron density map(s), if loaded, and the atomic structure(s) are
     shown. Steps to follow depend on the specific operation to carry
     out. Usually, new volumes or structures are generated, sometimes by
     combination of others, each one with a specific *model*
     number displayed in the *Models* panel, and they have to be saved
     in *Scipion*.

   -  | To combine two or more atomic structures, write in *ChimeraX* command line:

        ::

              scipioncombine #n1,n2


      | *#n1* and *#n2* are the respective *model* numbers of two
        different atomic structures. Optionally you can set the
        *model* number of the output combined structure *#n3*:

        ::

              scipioncombine #n1,n2 modelid n3

   -  | To save a map or an atomic structure generated with this
        protocol *model* number *#n*, write in *ChimeraX* command line:

        ::

              scipionwrite #n

      | Optionally you can write a prefix to easily recognize that map
        or structure. Then, the prefix depends on the user. Example:

        ::

              scipionwrite #n prefix my_favorite_model_


   -  Close *ChimeraX* graphics window.


-  Visualization of protocol results:

   After executing the protocol, press *Analyze Results* and *Chimera* graphics
   window will be opened by default. Atomic structures and volumes are
   referred to the origin of coordinates in *ChimeraX*. To show the relative
   position of atomic structures and electron density volumes, the three
   coordinate axes are represented; X axis (red), Y axis (yellow), and Z
   axis (blue) (:numref:`model_building_app_protocol_volume_3`). Coordinate axes, volume, and atomic structure are
   model numbers *#1*, *#2*, and *#3*, respectively, in *ChimeraX Models* panel.
   If no volumes have been included, coordinate axes and each atomic
   structure are model numbers *#1* and *#2*, respectively.

   .. figure:: Images_appendix/Fig102.svg
      :alt: Default *ChimeraX* graphics window with coordinate axes.
      :name: model_building_app_protocol_volume_3
      :align: center
      :width: 50.0%

      Default *ChimeraX* graphics window with coordinate axes.

-  | Summary content:

   -  If an atomic structure is generated:

      -  | Protocol output (below *Scipion* framework):
         | *chimerax - operate -> output atomic structure name, starting
           with the prefix*;
         | *AtomStruct (pseudoatoms=True/ False, volume=True/ False)*.
         | Pseudoatoms is set to *True* when the structure is made of
           pseudoatoms instead of atoms. Volume is set to *True* when an
           electron density map is associated to the atomic structure.

      -  | *SUMMARY* box:
         | Produced files:
         | output atomic structure name, starting with the prefix (.cif
           file)
         | we have some result

   -  If a volume is generated:

      -  | Protocol output (below *Scipion* framework):
         | *chimerax - operate -> output 3D map name*; *Volume (x, y,
           and z dimensions, sampling rate)*.

      -  | *SUMMARY* box:
         | Produced files:
         | output 3D map name, starting with the prefix (.mrc file)
         | we have some result
