# 5 Axis Desktop Robot Arm
I am going to build a compact desktop 5 Axis robotic arm with around 400 mm reach and a weight of around 900g, with swappable end effectors to increase functionality.

Here is the CAD screenshot of the full arm with the claw end effector:
![Robot arm with claw](assets/arm-assembly-with-claw-end-effector.png)

Here is the CAD screenshot of the drill end effector:
![Drill end effector](assets/drill-end-effector.png)


All the CAD STEP files are visible in: [CAD Files](cad). Additionally, my Onshape document is available to view using the following link: [Onshape Document](https://cad.onshape.com/documents/6e9b1a5896790ac8c1d4ec04/w/12c5f12a733b298ddd2827c6/e/e15365438cc5c7eb83e6249b?renderMode=0&uiState=6aa2230ec2980b84891cc26d)

My end goal is for the arm to be able to autonomously respond to commands using a small local AI and a router. For this, it will need to be able to take voice commands using a microphone, use a camera to navigate the environment and complete the task, talk to me in case it needs to clarify something, and run YOLO, speech to text and text to speech, and maybe a small LLM, all locally. This is why I selected the Nvidia Jetson Orin Nano Super for this project. While it is definitely overkill for V1, it will be useful in the future. Right now I am just going to use V1 to verify that my general arm design and expected lifting capacity are where I want them to be before moving on to add computer vision and autonomous operation.


## Goals
- I want this arm to be able to perform precision movement within 1 mm accuracy. 
- I want the arm to be able to lift at least 400 g. I am not sure if v1 can achieve this because it is a little heavy, so I will have to test it once I build it.

## Design

**Gears vs Belts:** Since gears can have backlash, I chose to use belts, since a properly tensioned belt should have minimal backlash. However, belts need to be larger to avoid putting too much strain on the belt, so they are bulkier and heavier which will affect my weight capacity.

**Torque:** I used a robot arm torque calculator to decide what ratios to use. According to the calculator, the realistic capacity for the arm at full reach is about 350g including losses from inefficiency. While this doesn't meet my goal, it is good for a first version and with belt tuning the efficiency could increase. I selected the STS3215 servos because they are affordable and adequate for most joints and commonly used for arms like the SO101, while the higher torque STS3250 are used on joints which see a lot of load (the 2nd and 3rd ones). In order to get enough torque at these high load joints, I am going to use a 30:80 torque multiplying ratio for the 2nd joint and a 30:60 torque multiplying ratio on the 3rd joint, with 10 mm GT2 belts which are thicker and stronger than the more common 6 mm ones. I chose to use servos because they have built in potentiometers which reduces the number of components needed for getting precise motion.

**Mass:** I tried to optimize the weight of 3d printed parts to make the arm as light as possible. However, motors and metal parts like shafts and screws make up over 75% of the actual weight so after a point it wasn't worth it to optimize the plastic parts in exchange for strength. The center of mass is around 170 mm from the L-axis pivot point (the second motor).

**Material:** I selected PETG because it can be used in most 3d printers, is similar in price to PLA, and is much less brittle than PLA. My test prints verified that it is a strong material, as it was pretty challenging to bend and it barely budged.

**Safety:** I will be using a switch and keeping all of the electronics inside of the base box to reduce risk of touching any live wires or terminals. I will also be using electrical tape to seal connections, and I have a fuse to protect the system in case of a short circuit. Here is my wiring diagram:
![Wiring diagram](assets/Robot%20Arm%20V1%20Wiring%20Diagram.png)

## Bill of Materials
My BOM is visible in BOM.csv. You can also access it from here: [BOM.csv](BOM.csv)
It shows all the parts, quantities, costs, and purchase links which are needed to assemble the arm. The BOM is split into the parts I currently need (USD $533.84 of parts) and parts I already have/have purchased (USD $636.45).

Thanks for reading!




