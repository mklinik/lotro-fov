lotro FOV mod
=============

This is a cheat table for cheat engine to change the field-of-view (FOV) of the
third-person camera of the game Lord of the Rings Online.

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
   wrong. Stop! Do not continue.**

   Verify that the value 45 is found:
   ![verify value screenshot][verify-value]



[default-fov]: https://github.com/mklinik/lotro-fov/raw/master/doc/20201105070746_1.jpg
[wide-fov]: https://github.com/mklinik/lotro-fov/raw/master/doc/20201105070623_1.jpg
[attach-to-process]: https://github.com/mklinik/lotro-fov/raw/master/doc/attach-to-process.png
[load-cheat-table]: https://github.com/mklinik/lotro-fov/raw/master/doc/load-cheat-table.png
[verify-value]: https://github.com/mklinik/lotro-fov/raw/master/doc/verify-value.png
