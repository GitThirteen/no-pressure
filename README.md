# no-pressure
Fun little VR game in which you either solve tasks with your friend or you all die a painful death :>

# Super mega hyper uber duper important
Please download the Fab folder and drag n' drop its content into Content/Fab. The assets are too big for GitHub:
https://drive.google.com/file/d/1n_s4r8NDtz5-AaI2xLR7eQW_lkWqnXbI/view?usp=sharing

# Our Submission
Our submission consists of three levels:
1) SP_Menu - starting level, here, one can create or join a session via IP
2) MP_Lobby - after joining the session, players meet here where they can press a READY button
3) SpaceStation - actual gameplay happens here, in the _Features_ section, we descibe the functionality we added there

## Networking
Our networking approach (session creation, joining, etc.) is directly copied from Assignment 3, which was heavily tested by us.
During testing of this assignment, we have run into issues whenever we tried to run the application as a Client.

Whenever we try to run ANY level with _NetMode_ set to _Client_, the game instantly crashes (nondeterministically, roughly 90% of the time). UE's coredump indicates a memory corruption during rendering.
Without success, we have tried to:
1. Reboot the machines
2. Clear all the local caches
3. Create a new project and move the content over
4. Try with Assignment 3 (non-deterministic crashes again)

We have found that our problem **exactly** matches the one acknowledged by Epic on [their forum](https://forums.unrealengine.com/t/game-crash-as-client-in-5-6-and-5-7/2664156).
They claim the issue is resolved in 5.7 release, but there are still reports of this crash in the past two weeks (even on 5.7).

Because of this, we were not able to fully test the multiplayer capabilities of our submission, but we have made sure that the relevant gameplay elements and events are appropriately replicated,
which we hope to showcase during the presentation.

## Features
We have made heavy use of interactable objects, which highlight whenever you look at them and have an easy interface that is enabled whenever a user's hand interacts with it.

### Meteors and Pistols (2-player simultaneous interaction)
Whenever one player picks up a pistol from the ground, meteors start shooting at the spaceship. Meteors are either orange or blue. When a meteor is shot, it displays a digit.
The players must communicate said color and digit to appropriately set the color of a button on an array of nine buttons.

### Radio (spatial audio)
In the lobby, it is possible to turn the radio on and off (using the interaction interface). The radio's audio is spatialized.

### Meteor Task UI Helpers (create & modify >=3 objects)
1. On grabbing of the pistol, meteors start spawning and shooting at the spaceship
2. On press of the _Burst ON/OFF_ button, pistol's mode can be switched
3. On press of the _Spawn Gun_, a new gun is spawned
4. On press of the _Reset_ button, the array of 9 buttons fully resets

### Locomotion (metaphor without a helper object)
To move within the environment, both triggers must be pressed and the user must make mvoements as if they were running.