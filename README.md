lotro FOV mod
=============

This is a cheat table to change the field-of-view (FOV) of the third-person
camera in Lord of the Rings Online.

Default FOV ![default FOV screenshot][default-fov]
Wide FOV ![wide FOV screenshot][wide-fov]

How to use
----------

There are two versions of this cheat table, one for the 32-bit client and one for the 64-bit client.
If you don't know what this means, you need the 32-bit version.

1. Download the cheat table corresponding to the lotro client you are using:
   `lotro-3rd-person-FOV-32bit.CT` or `lotro-3rd-person-FOV-64bit.CT`
1. Install [Cheat Engine](https://www.cheatengine.org/)
1. Start lotro, log in and go into the game. Make sure that the camera is in
   3rd-person view. This mod does not work for first-person view, so don't be
   zoomed all the way in.
1. Tab out of the game to Windows and start Cheat Engine. Cheat Engine also
   comes in 32-bit and 64-bit variants. You need to start the one matching
   your lotro client.
1. Attach Cheat Engine to the running lotro process. To do this, click on the
   attach to process icon (marked red in the screenshot below), then select the
   process of the lotro client. If you have the launcher running, make sure to
   attach to the client not the launcher.

   Attach to lotro client process: ![attach to process screenshot][attach-to-process]
1. Load the cheat table. To do this, click the open button (marked red in the
   screenshot below) and select the `.CT` cheat table corresponding to your
   lotro client: 32-bit or 64-bit.

   Open cheat table: ![open cheat table screenshot][load-cheat-table]
1. If everything worked properly you should see a memory location at the bottom
   of Cheat Engine called "FOV Base Pointer" of type Float with value 45. **If
   you see a garbage value or lots of question marks ??????? something went
   wrong. Stop! Do not continue.** You have either selected the wrong version
   of the cheat table, or a newer version of the game has been released, and
   the cheat table is no longer compatible with it.

   Verify that the value 45 is found:
   ![verify value screenshot][verify-value]
1. Tab back into the game and press Ctrl-PageUp or Ctrl-PageDown to increase or
   decrease the FOV.
   **Only press these keys in 3rd-person mode while in the game. Do not press
   the keys in any other mode, like the character select screen, first-person
   mode or in-game cutscenes.** You will overwrite arbitrary memory, leading to
   unpredictable behaviour or even crashes. Once you have set the FOV, the
   other modes will work as before. Just don't press the keys while in any
   other mode.
1. Optional: Once you have found your favourite FOV value, you can bind it
   directly to the hotkey Ctrl-Home. Tab out to Cheat Engine and note the value
   currently being displayed in "FOV Base Pointer". Then right-click the "FOV
   Base Pointer" entry in Cheat Engine and select "Set/Change Hotkeys". Enter
   the value as shown in the the screenshot below. Save the cheat table, and
   next time you run the game you can use this key to directly set the FOV to
   your preferred value.

   Set your own preference: ![change hotkeys screenshot][change-hotkeys]


Development notes
-----------------

- After some hours of scanning and poking around in lotro's memory, I found out
  that lotro calculates the FOV from two values: it multiplies the current
  reolution's aspect ratio with a scene-specific factor.
- For example, when your screen resolution is set to 1290x1080, the aspect
  ratio factor is 1.777777
- The scene-specific factor is different depending on the mode
    - Character select screen: 60 (I think)
    - In-game 3rd-person: 45
    - In-game first-person: (some value, I forgot)
    - 3d character portraits: the small 3d heads of your characters and pets
      have their own scene.
- We can't change the resulting FOV directly, because it is never stored, just
  as intermediate result. We have to find the original value of the scene
  factor and change it. The factor for 3rd-person camera is 45, so we must find
  a constant value 45 somewhere in memory.
- This is how I found it:
- Scan memory for a float between 44.999999 and 45.000001
- In the game, walk around, move the camera, do stuff, and continue scanning
  for this value to remove all values that change. We want to find a constant
  value.
- After some scans, there are still thousands of constant floats with value 45
  left.
- By sheer luck I found out that the third one is the one we want.
- This value is stored in some nested object, and changes location every time
  you switch scenes or restart the game.
- To create this cheat table I followed the instructions of Cheat Engine's
  tutorial for nested pointers to find the base pointer. From the base pointer
  to the scene factor it's 4 indirections with varying offsets. Make sure to
  understand the nested pointer tutorial to understand what's going on.
- The base pointer location and offsets might or might not change when new
  versions of lotro are released. We have to update the cheat table when they
  do.

  My notes while finding the base pointer: ![developer notes][dev-notes]


[default-fov]: https://github.com/mklinik/lotro-fov/raw/master/doc/20201105070746_1.jpg
[wide-fov]: https://github.com/mklinik/lotro-fov/raw/master/doc/20201105070623_1.jpg
[attach-to-process]: https://github.com/mklinik/lotro-fov/raw/master/doc/attach-to-process.png
[load-cheat-table]: https://github.com/mklinik/lotro-fov/raw/master/doc/load-cheat-table.png
[verify-value]: https://github.com/mklinik/lotro-fov/raw/master/doc/verify-value.png
[change-hotkeys]: https://github.com/mklinik/lotro-fov/raw/master/doc/change-hotkeys.png
[dev-notes]: https://github.com/mklinik/lotro-fov/raw/master/doc/dev-notes.jpg
