# slip_detection_dataset_2023

The data was collected using an EZGripper mounted on a Universal Robot UR5 arm. One of the fingers of the gripper was replaced with a dedicated structure that includes the uSkin tactile sensor, ensuring that it does not interfere with the gripper operation. 

we propose a new object-agnostic protocol to collect tactile data for training robust slip detection models. The proposed protocol relies on few, simple robot actions and on a fast labelling procedure; we create and share a new tactile dataset1 collected with the proposed protocol, and show that our data capture more variability than data collected with state-of-the-art approaches;

The uSkin sensor [1] features 24 taxels (i.e. sensing units) distributed as a 6 × 4 lattice, covered by a slab of fabric The slab of fabric acts as an artificial skin that reacts to stretches and friction. Each taxel is made of a silicone dome embedding a magnet located on top of a 3D Hall effect sensor, updating its values at 100 Hz. 

uSkin Tactile Sensor:

![alt text][uskin]


Therefore, the raw data measured at each taxel, denoted as ui ∈ Z3 , represents the values of the local 3D magnetic field induced by the position of the corresponding magnet.
The forces applied on the pad induce both shear (Ft ) and normal (Fn ) forces across its surface. Hence, at each taxel i ∈ {1, . . . , 24}, we have the following:

ui = [xi , yi , zi ],
ui = g(Fi),
Fi = Fti + Fni ,

where Fi , Fti and Fni correspond to the local net, shear and normal force applied to taxel i, and g is an unknown non-linear function. The values mostly correlated to the distributed
shear forces are xi and yi , whereas zi mostly carry information related to normal forces. At a given time t, a full tactile sample will be denoted as a 24 × 3 matrix Ut = [ut1 , ... , ut24 ]T.

Data is collected with seven objects:

![alt text][objects_table]

These objects are an empty cardboard can, an unopened soda can, three cuboid wood bars - two of them wrapped in either baking paper or duct tape to change their respective coefficients of friction - a metal bar, and a brush. As reported in Table I, this set of objects includes a variety of shapes (cuboid, cylindrical, composite), weights (between 47 and 356 g), dimensions and textures. The coefficient of friction of each object has been estimated by executing the experiment described in [2] with a 500 g weight. For each sampled grasp pose of each object, R = 10 experiments are collected and labelled, leading to a total of 2100 grasps across the seven objects. This corresponds to 70 minutes of tactile data, and approximately 420K tactile samples, with 230K labelled as slip events (Y = 1), and 190K as non-slip events (Y = 0). The resulting dataset has been made publicly available1.

[uskin]: https://github.com/ARQ-CRISP/slip_detection_dataset_2023/blob/main/images/sensor.png "sensor.png"
[objects_table]: https://github.com/ARQ-CRISP/slip_detection_dataset_2023/blob/main/images/objects_table.png "objects_table.png"


## References

[1] T. P. Tomo, M. Regoli, A. Schmitz, L. Natale, H. Kristanto, S. Somlor, L. Jamone, G. Metta, and S. Sugano, “A new silicone structure for uskin—a soft, distributed, digital 3-axis skin sensor and its integration on the humanoid robot icub,” IEEE Robotics and Automation Letters, vol. 3, no. 3, pp. 2584–2591, 2018.

[2] R. Kurtus, “Determining the coefficient of friction,” The School for Champions, 2002.
