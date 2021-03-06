# Rover-Robot-Simulation
## Project repository for the Unity rover search and sample return project.  

[//]: # (Image References)

[image1]: ./misc/Perspect_transform.png
[image2]: /misc/color_thresh.png
[image3]: /misc/Rover_vector.png
[image4]: /misc/Rover_simulation.gif

### **Rover_Project_Test_Notebook.ipynb**

- See the samples in world-map, will help to make a vector later. In order to do it, I transformed the images with samples using the function `perspect_transform()`. This will allow mapping the sample to a top perspective.
  
  ![alt text][image1]

- In order to detect obstacles and rocks with the rover, it is necessary to modify  `color_thresh()` to detect the colors of this objects and convert them to binary images (black and white).
  
  ![alt text][image2]

- Using the `rover_coords()`, `to_polar_coords()`, `rotate_pix()` functions. I created and mapped two vectors with angle and distance properties: one for the path that avoids the obstacles and other that point the samples.


  ![alt text][image3]

### **Perception.py**

- Implementation of the changes made, and tested in Jupyter Notebook environment, with *Rover_project_Test_Notebook.ipynb*. (Line 6-94)

- `Perception_step()` is the main function, and it contains all the functions implemented, from warped images to "worldmap-coord" conversion. (Line 98-192)

  - In order to guide the rover robot in the simulation, the function `to_polar_coords()` is providing the vector that follows the path or finds the rocks samples in lines 158-185, switching between, drawing a vector to throttle through the path or head towards the samples found.

### **Decision.py**
- From (line 15-37) the  **If** conditions determine, When the rover should stop, go towards the rocks or activate the robot arm to pick up the samples.
  
  ![alt text][image4]
  
  
  
## **Conclution and posibble improvements**

#### The Rover performs decently so far, it collects samples and drives itself thru the paths avoiding the obstacles (most of the times). However, it is not very accurate; some issues occur:

#### When it tries to avoid small obstacles.
#### It presents erratic movement when the rover is choosing to avoid the walls or collect the samples.
#### Some times is unable to find hidden samples.

#### To solve these problems, the creation of two vectors may be necessary. The first vector would need to recognize closer objects and the second one for further objects. After this change, it only takes to modify the *decision.py* file.
