## AWSIM-Script

The three folder `cutin`, `cutout`, and `deceleration` contain the input scripts supporting our experiments.

To launch the simulation with these scripts, we first need to setup AWSIM-Labs project. The setup guide is available at: https://github.com/duongtd23/AWSIM-Labs/tree/awsim-script.

After finishing the setup, we can use the following command to run the simulation for the cutin case in which the ego's velocity, NPC's velocity, and cutin's lateral velocity are 20 km/h, 10 km/h, and 0.6 m/s, respectively:
```
./awsimlabs.x86_64 -script AWSIM-Script/cutin/cutin20-10-1.script -output Traces/lidar/cutin/cutin20-10-1
```

To launch Autoware, following the installation guide provided by Autoware Foundation at: https://autowarefoundation.github.io/autoware-documentation/main/installation/autoware/source-installation/
