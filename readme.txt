This memo explains what you will find in the Github directory of the "Butterfly Effect" open movie.  

Everything here is under Creative Commons licences.   Everything is made by myself and licenced under CC-BY, except: 
* Sound strips, mostly from freesounds.org, and their specific CC is given in the movie.
* Images from the Blender Foundation.

As a foreword, let me stress that I am not a professional 3D artist, I'm a computer scientist at heart, and a part-time Blender contributor as well.   This short open movie will probably not teach you tricks that only experts know of.   There are tens of thousands of Blender tutorials out there, and a few hundreds maybe that are delivered by very talented 3D artists.   Plus the open movies of the Blender foundation offer an huge wealth of 3D resources made by some of the best artists.   The Butterfly Effect is not in this category.   Then again, there are relatively few open movies available with all their ressources, where you can just download and regenerate everything, then modify the scenario, or just pick things for your own compositions.  So having one more is not without interrest I think.   Here are a few things worth pointing out.


The cloud of butterflies

This is one feature that some could find interresting.    When a cloud of butterflies flies accross the station at around 1'30'', there are 200 butterflies in the cloud.   It would have been impossible to define 200 different path curves and 200 different flight actions.   Both curves and NLA actions are defined by a Python script that takes a single curve and action as a reference.    Each vertex in the curve is shifted along the two perpandicular axis, within a range that is defined by the curves radius at this point.  Thus it is possible to have the butterflies gather up at some point in their flights, and split far appart at a later point.   Each flight is made unique by slightly modifying the scale of the wing cycle action as well as its starting point in time.   In spite of being random, this cloud generation is actually repeatable, so that it's best to delete all but the refence curve before saving, so as not to grow the blend file needlessly.

When the cloud passes in front of the gecko, out of focus, this was done in two passes:  first having the butterflies on a transparent background, then overlaying this in front of the gecko.  This gave me more control over the scene set up, and it turned out that I had to use the overlay twice, desynchronized, in order to add more butterflies.


Home baked normal maps everywhere

Nothing too fancy here, but there lots of hand-made normal maps all around.   Once I mastered the creation of custom normal maps, I found this much better than searching for stuff on CGTexture that you don't really control and that you cannot distribute.   The gecko skin material uses a single bump, tiled, with its normal map baked in Blender Internal, from a very simple squashed half-sphere.  The gecko uses 3 shaders into a single material for the skin, one for the back and head, one for the belly, and one for the upper part of the hands and feet, with a 3 color texture paint that defines where each shader is applied, as well as smooth transitions between shaders.   This is sort of like using 3 different materials, but with greater control, and limits not necessarily on face boundaries.  

The metro station's walls with their white tiles also use custom normal maps.    None of the tiles actually has a 3D mesh, it's all flat in terms of mesh.    Here again, I built a few metro tiles in Blender, then baked the normal maps and mask for it, made sure it was tilable, then used it in the metro wall material.   Because the surface of a glazed metro tile is never perfectly flat, I mixed another home-made normal map that adds some random smooth variations.  On a separate project, I use a cloud texture with displace modifier, tune, then bake, then make it tileable in an image editor.

Same for the metro floor, more or less.   The floor also has random chewing gums lying around, produced by a particle system.


The gecko animation

I was really learning animation and armatures while working on the movie, which leaves some traces.    On several occasions I found my rig was not good enough for what I needed it to do, so I would go back to the rig, fix some things, add some bones or constraints, then go back to my metro scene.   Only to find that the new rig was incompatible with all my previous scenes.   In particular when you set the base bone at a fixed location, then move around other bones from there.   If the geometry of the bones in the rest position changes, then all existing moves are wildly affected.   It turned out I had to either rebuild all my finished scenes using the new rig, or live with 2 versions of the rig, which I did.  At the end, I have 3 or 4 versions I think, using one or the other depending on the scene and when it was completed.   

I had heard already a few animators say they would never use walk cycles.   Actually some say they never use things like the NLA editor and off the shelf actions.   I strived for a long time to have a decent walk cycle for my gecko, but it always turned out to be too repetitive to look real.   I had more success in hand-made walks, where I would just move around the body, not necessarily in a straight line, then take care of the legs as need be: just before a limb is stretched to the limit because the body has advanced, I move it forward almost as far as I can (well depending on the stroll).   Once this hand-made walk has been completed for a few seconds, I can accelerate or decelarate some bits by scaling in the action editor.  

One simple thing that I find works well is adding a subtle noise modifier to the curves on the body movement.  Even when the character is standing still, with its legs stable on the ground, this added noise will make it look like it's working to keep its balance, as all living creatures do.   Of course this needs to be very light.   I also used the same technique on the X and Z angle rotations of the camera in some scenes to make it look like hand-held shooting.   Maybe I overdid it some times, you tell me.  

Finally, note that their are a very small number of texture files that I cannot release under CC, but they are really not critical.   They relate to the concrete floor in the staircases, and can be replaced by some simple dark grey shader since never seen at close range.    It turns out using non-cc textures is not such a good idea:  you think you're saving time, then you're sorry you can't do whatever you want with them.   Now I would advise to use your own procedural textures rather than  textures you cannot reproduce. 






