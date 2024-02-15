# slip_detection_dataset_2023

[Tactile dataset](https://github.com/ARQ-CRISP/slip_detection_dataset_2023/tree/main/dataset) generated using a new object-agnostic protocol that allows collecting tactile data for training robust slip detection models during robotic object grasping. The proposed protocol steps are described in detail in [1] and are summarised as follows:

1) Descritise the object into valid grasp pose configurations (section IV-A) 
2) Move the robot arm to a given grasp configuration (section IV-B) 
3) Close the robot fingers (i.e. grasp the object)
4) Start collecting tactile data
5) Raise the robot arm to a pre-defined pose, i.e. the robot
lifts the object (lasting ≈0.2s)
6) Once the robot arm is static, wait a period of 2s
7) Stop recording tactile data
8) Label the collected data (section IV-C)

![alt text][protocol]

## Experimental Setup

### Robotic Setup
The data was collected using an EZGripper mounted on a Universal Robot UR5 arm. One of the fingers of the gripper was replaced with a dedicated structure that includes the uSkin tactile sensor [2], ensuring that it does not interfere with the gripper operation.

![alt text][robotic_setup]

### uSkin Tactile Sensor

![alt text][uskin]

The [uSkin sensor](https://ieeexplore.ieee.org/abstract/document/8307485?casa_token=RghI6jquxKsAAAAA:PYxylx6reYD-enQwc1N99BtJVf0_Mh7EW4yGBc3zJyx_t0SI0VE6osIWL6rtN8vFOdv9XTk) features 24 taxels (i.e. sensing units) distributed as a 6 × 4 lattice, covered by a slab of fabric. The slab of fabric acts as an artificial skin that reacts to stretches and friction. Each taxel is made of a silicone dome embedding a magnet located on top of a 3D Hall effect sensor, updating its values at 100 Hz. Therefore, the raw data measured at each taxel represents the values of the local 3D magnetic field induced by the position of the corresponding magnet. The forces applied on the pad induce both shear and normal forces across its surface. Hence, at each taxel i ∈ {1, . . . , 24}, we have ui = [xi , yi , zi]


## Dataset Description
Tactlie slip data has been collected for robitc grasps of seven objects:

![alt text][objects_table]

These objects are an empty cardboard can, an unopened soda can, three cuboid wood bars - two of them wrapped in either baking paper or duct tape to change their respective coefficients of friction - a metal bar, and a brush. As reported in Table I, this set of objects includes a variety of shapes (cuboid, cylindrical, composite), weights (between 47 and 356 g), dimensions and textures. The coefficient of friction of each object has been estimated by executing the experiment described in [here](https://nfsi.org/wp-content/uploads/2013/10/Determining.pdf), using a 500 g weight. For each sampled grasp pose of each object, 10 experiments were collected and labelled, leading to a total of 2100 grasps across the seven objects. This corresponds to ≈70 minutes of tactile data, and ≈420K tactile samples, with ≈230K labelled as slip events, and ≈190K as non-slip events.


<!-- Further testing data as been captured for each of the objects -->



[uskin]: https://github.com/ARQ-CRISP/slip_detection_dataset_2023/blob/main/images/sensor.png "sensor.png"
[objects_table]: https://github.com/ARQ-CRISP/slip_detection_dataset_2023/blob/main/images/objects_table.png "objects_table.png"
[robotic_setup]: https://github.com/ARQ-CRISP/slip_detection_dataset_2023/blob/main/images/robotic_setup.png "robotic_setup.png"
[protocol]: https://github.com/ARQ-CRISP/slip_detection_dataset_2023/blob/main/images/protocol.png "protocol.png"


## References
[1] R. Zenha*, B. Denoun*, A. Cavallaro, A. Bernardino, L. Jamone, "An Efficient Protocol to Train Robust Tactile Slip Detection Models for Robotic Grasping", 2024
