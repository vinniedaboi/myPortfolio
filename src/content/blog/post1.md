---
title: "Making your first cinematic in UE5"
description: "A guide on how to make your first cinematic in UE5, using free assets, and built-in plugins."
pubDate: "May 5, 2023"
heroImage: "https://miro.medium.com/v2/resize:fit:1400/1*Zsixza6z-6KnUBH6TKwxkg.png"
tags: ["UE5","Game Development"]
badge: "Tutorial"
---

# Step 1: Installing Unreal Engine 5

Head over to install [**Epic Launcher**](https://store.epicgames.com/en-US/download) if you haven’t, in the Epic Launcher click Library, then click the small plus sign. Install the version of Unreal Engine 5 you want to use, I’m using Unreal Engine 5.03.

![](https://miro.medium.com/v2/resize:fit:1400/1*HVUiUrZhqmvgYM7YY5hUAA.gif)

Installation of Unreal Engine 5

# Step 2: Install Packages from Marketplace

Head to Marketplace and install the [**Automotive Winter Scene**](https://www.unrealengine.com/marketplace/en-US/product/automotive-winter-scene) package and the [**Vehicle Variety Pack Volume**](https://www.unrealengine.com/marketplace/en-US/product/9a705589d1994c6e8757fdbedaf698af). Make a project under Vehicle Variety Pack Volume by clicking “Create Project”, it will create a project with the name you choose.

![](https://miro.medium.com/v2/resize:fit:1400/1*8BJYM8R9irrP0Lq9y_dPwA.gif)

Creating a project with Vehicle Variety Pack

# Step 3: Import Automotive Winter Scene to the project

At the same area, click Automotive Winter Scene > Add to Project, and select the project you created with the Vehicle Variety Pack.

![](https://miro.medium.com/v2/resize:fit:1400/1*uvdZvxawVldi4khapO6kbA.gif)

Adding Automotive Winter Scene to a project

# Step 4: Opening the map and importing the Sedan we are going to use

Launch Unreal Engine and click on the project, it should take some time to compile the shaders if it is your first time. Open your content browser and click Automotive Winter Scene > Maps > IceRoad. This should load up the IceRoad map. Then click on VehicleVarietyPack... > Blueprints > Sedan. Drag and drop the Sedan onto the map.

![](https://miro.medium.com/v2/resize:fit:1400/1*bTpR5CznBFWsaaExQmCL1A.gif)

Dragging and dropping the Sedan

# Step 5: Enabling take recorder plugin and remove wind/camera folders

Click on Tools > Plugins > Take Recorder, it should prompt you to restart your editor, restart it and you should be able to use take recorder. Remove all files in the 2_Atmospherics > Wind, then remove the 3_Camera folder because we don’t need those cameras.

![](https://miro.medium.com/v2/resize:fit:1400/1*jQlZBbbyvOPIUaytNhS9pQ.gif)

# Step 6: Making the sedan drivable

Click on the sedan, in the details box, search for “Auto Possess Player”. Click the dropdown and select “Player 0”. Now click play (green button on the top) and you should be able to drive the car! The car wheels may be stuck to the floor, to fix this go to the Blueprints folder in the VehicleVolumePack, and click Sedan > Sedan_Config, you should see there is a front wheel and back wheel Blueprint, click on those and edit wheel radius to 41. Then, Select Mode and select Landscape mode, click Manage > Splines and you should see a section “Deform all landscape to splines”, click all splines and you should be good. (Don’t forget to compile when editing blueprint)

![](https://miro.medium.com/v2/resize:fit:1400/1*Jj2MlZpokyPY5JBFIrziKg.gif)

![](https://miro.medium.com/v2/resize:fit:1400/1*ikRVo2fzNweuCzw_mKhKVA.png)

# Step 7: Configuring the take recorder

Let’s record our scene now to make the cinematic, remember the take recorder plugin we enabled? Click Window > Cinematics > Take Recorder. On the take recorder menu, you’ll see “ Source”, click on that and it should drop down a list of objects, select BP_Sedan_Chaos.

![](https://miro.medium.com/v2/resize:fit:1400/1*hXJdzqzw-q9H22ZQcOafzg.gif)

Adding take recorder actor.

# Step 8: Recording our scene

Finally, we can record our scene, click on play, then click record on the take recorder menu. Now it should start recording, drive with your car and when you feel like you have enough footage hit Esc.

![](https://miro.medium.com/v2/resize:fit:1400/1*ZVnkqsxzGLOb5djrsP44BQ.gif)

# Step 9: Adding a camera to our scene and making it “cinematic”

You can open your scene via Content > Cinematics > Takes > Date > Your_Scene. After opening your scene via double-clicking. Click the small box with a green plus beside “Select Mode” and click on Cinematics > Cine Camera Actor.

![](https://miro.medium.com/v2/resize:fit:1400/1*HT79obe-Vgcy2gOqR7eXng.png)

# Step 10: Creating our camera angles

Click on Perspective and select our CineCameraActor, now we pilot the camera and place it where we want around the car, you can see in the previous screenshot I placed it around the left side of the car. Now drag the CineCameraActor from the sidebar to the Sequencer and place it above the BP_Sedan object, see Screenshot_2 for reference.

![](https://miro.medium.com/v2/resize:fit:1400/1*V-VyroPOqIqMix9q1lg8Bw.png)

![](https://miro.medium.com/v2/resize:fit:1400/1*hrLHx_FMAc3N7weAyBzbUQ.png)

# Step 11: Binding the camera to the car

We’re almost there! Now we have to bind the camera to the car, click the plus sign on the CineCameraActor object, Attach > BP_Sedan_Chaos_Scene… > BP_Sedan_Chaos, it should now prompt two selections between SpringArm and VehicleMesh, and select SpringArm > SpringEndPoint. Now your camera should go a bit crazy relocate the car and place the camera angle back to where it was. Now run the animation and you can see that the camera is following the car.

![](https://miro.medium.com/v2/resize:fit:1400/1*Zsixza6z-6KnUBH6TKwxkg.png)

# Step 12: Adding animation and shake to the car

Now we have a working camera, it’s time for us to animate it to swing from left to right, giving a cinematic effect. We first enable the keyframe by clicking the button in Screenshot_1, also select a portion of the cinematic you want to use by dragging the green and orange bars as seen in the previous screenshot.

![](https://miro.medium.com/v2/resize:fit:1400/1*_OoeNXWuEkUfnG_SVkjw9w.png)


Now let’s default the keys to Linear, click on the button beside the key sign and select Linear.

![](https://miro.medium.com/v2/resize:fit:1240/1*tutTIc-x7aFFuF4ZzIObuQ.png)


Then now at the beginning of the green bar (you have to move that orange thing on the letter S to the green bar to access that frame), we click on the location plus sign which is circled white as seen in the screenshot below. It should produce this triangle circled in blue on the green bar.

![](https://miro.medium.com/v2/resize:fit:1400/1*YFjReHZq7Xd5cfL9R5ZI9Q.png)


Now move the orange tick to the red bar, change the camera position to somewhere you like then click the plus button on location again, I changed it to the right side of the vehicle as seen in the screenshot below, it should produce another triangle.

![](https://miro.medium.com/v2/resize:fit:1400/1*OqSobPPbRtwOWS3JrNo-fg.png)


Now run the animation and you should see the camera slowly move to the new camera position throughout. After this, we can now add a shake. In the content directory right click and click Blueprint Class, search for CameraShakeBase and select it, name it whatever you want. Now open it and close it then open it again. You should get the screen in screenshot_6

![](https://miro.medium.com/v2/resize:fit:1400/1*-MXPEoaJwTIcvBtJAY9PrQ.png)


![](https://miro.medium.com/v2/resize:fit:1400/1*5Ps7tWicq4PzZTNE-z7f8g.png)

Now copy my configs in screenshot 6 (don’t forget to compile), now you have a shake effect! Time to add it to the camera. Select track on the CineCameraActor (refer to step 11’s screenshot) click Camera Shake > Whatever_Your_Shake_Blueprint_Is. Now you have a shake effect! Your final product should look like the screenshot below.

![](https://miro.medium.com/v2/resize:fit:1400/1*VgDmO9Ws1A0qa9FZaFIYcg.png)

# Final Step: Final Blueprint edits and exporting with movie renderer

Now we have to bind the camera cut to the CineCameraActor, to do this we click Camera on Camera Cut and add our CineCameraActor.

![](https://miro.medium.com/v2/resize:fit:1400/1*EmJKtsb6gSiTIj0Ld1TyrQ.gif)

Now we edit the Sedan Blueprint (screenshot below), click on Vehicle Mesh and search for “Simulate Physics” and disable it then recompile the blueprint.

![](https://miro.medium.com/v2/resize:fit:1208/1*LqhMGAULYVNZKoJsrqvAtg.png)

![](https://miro.medium.com/v2/resize:fit:1400/1*zt8uWuYVmUZf3QzhI11n7Q.gif)

Now we click the movie button on the Sequencer, select Image Output Format as an avi video and render! Your rendered video should be in the folder you set it or you can open the capture folder after it is done in the bottom right.

![](https://miro.medium.com/v2/resize:fit:1400/1*LoTQ7Q9pD8qOGDYvgUTyCA.png)

![](https://miro.medium.com/v2/resize:fit:1400/1*hfLwtuAh5OTT5yw3I4odtQ.png)

You’ve now successfully created your first cinematic! Congrats! If you have any problems you can email me at vinnie5224@gmail.com 
