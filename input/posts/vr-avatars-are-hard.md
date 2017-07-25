Title: VR Avatars Are Hard
Published: 2017-07-25
Tags:
  - programming
  - modelling
  - virtual_reality
  - unity
  - blender
  - leap_motion
  - htc_vive

---

So the first thing I want in VR is an avatar. That is, I want to have a 3D model follow my body while I’m in VR. You’d think this would be common in VR, but it seems many VR experiences decide to skip it. In some regards, this is because it’s actually pretty hard.

The first issue is that 3D models usually used for games have heads. You can in theory stick the camera into the head, but then you see the backside of head’s faces if it has any. Or as I was running into my most recent case, large eyeballs and modelled bangs. The solution to this is to keep the head “separate” from the body. But if you do that incorrectly, then your model has no head. You need the model to have a head when it’s making a shadow or being viewed in a mirror, but not otherwise. Unity actually has a “shadow only” setting for this, but you end up having to duplicate the head nonetheless. Either way, you need to be able to set this at modelling time, not after you have the model. That puts some limitations on your artist, and limits the ability to use characters modelled by others without some extra work.

The next issue is getting the gaze and body to sync up. This is actually not that hard. You have the model, you can transform it easily, and you have the information from the VR headset. The only things to keep in mind is that you want only the X and Z parts of the position, and only the rotation around the Y axis for the rotation. (We’re using Unity axes here, which are X to the right, Z forward, and Y up.) You might think the Y part of the position would be good for setting the height, but you then run into the next problem...

Height becomes a problem for two reasons. The first is that the position of the headset will move up and down slightly as you move around. The second is the more obvious fact that your players will be of different heights. I had a clever moment where I adjust the scaling of the Y axis so that the player is always the same height as the character. I’ve not moved it over to my new stack yet, but I’ll see if that can be automated rather than hard coded like it is now.

Another problem with an avatar is performing the inverse kinematics (IK) for the hands and gaze. Well, in theory this is a problem, but Unity has IK libraries built in, so map the gaze to where the player is looking, and the hands to the hand controllers, and... Well, it works, but it’s still going to take fiddling.

I’m however, going another level beyond that is kind of hard. I also have a LeapMotion controller, which is actually great at taking in hand motions. But I’ve not gotten that to work yet, I’ll keep playing with it.

Anyway, this was just mainly a test post, but figured I’ll kill two birds with one stone!
