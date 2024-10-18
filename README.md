## A Runtime Verification Framework for Safety Analysis of Autonomous Driving Systems

The input scripts supporting our experiments are available in the [AWSIM-Script folder](AWSIM-Script).

The AW-Checker tool and its guidelines can be found in the [AW-Checker folder](AW-Checker).

The traces of our experiments are in the [Traces folder](Traces).

The extended AWSIM-Labs and AWSIM-Script can be found at this forked repo: https://github.com/duongtd23/AWSIM-Labs.


### Demonstrations of some collisions

Below are demonstrations of some collision and non-collision cases from our experiments.

## Cut-in scenarios
### Scenario 30-10-6

In this [scenario](AWSIM-Script/cutin/cutin30-10-6.script), the ego vehicle and the NPC vehicle travel at speeds of 30 km/h and 10 km/h (`Ve` and `Vo`), respectively, on two adjacent lanes. 
The NPC vehicle abruptly cuts in front of the ego vehicle.
The lateral velocity of the cut-in (`Vy`) is 1.6 m/s.
When the cut-in starts, the longitudinal distance between the two vehicles (`dx0`) is 11 meters.
A collision occurred (in both lidar-only and camera-lidar fusion perception modes), which can be seen in the [video](Screencasts/camera_lidar_fusion/cutin-30-10-6.mp4?ref_type=heads) above.
Note that, a collision is not expected under the good driver model.

### Scenario 40-20-3

In this [scenario](AWSIM-Script/cutin/cutin40-20-3.script), the ego vehicle and the NPC vehicle travel at speeds of 40 km/h and 20 km/h (`Ve` and `Vo`), respectively. 
The lateral velocity of the cut-in (`Vy`) is 1.0 m/s 
When the cut-in starts, the longitudinal distance between the two vehicles (`dx0`) is 7 meters.
A collision occurred in the camera-lidar fusion perception mode, shown in the [video](Screencasts/camera_lidar_fusion/cutin-40-20-3.mp4?ref_type=heads) above. 


While in the lidar-only perception mode, no collision occurred, as shown in the following [video](Screencasts/lidar/cutin-40-20-3.mp4?ref_type=heads):

## Cut-out scenarios
### Scenario 50-1

In this [scenario](AWSIM-Script/cutout/cutout50-1.script), the ego vehicle and the NPC vehicle travel at a speed of 50 km/h (`Ve` and `Vo`) on the same lane, with a longitudinal distance (`dx0`) of twice the Time Headway (THW) between them (THW = 2 seconds).
The NPC vehicle suddenly changes its lane to the adjacent lane to avoid a stopped vehicle (challenging vehicle).
The ego vehicle needs to decelerate to avoid a collision.
The lateral velocity of the cut-out (`Vy`) is 1.6 m/s.
The longitudinal distance between the ego vehicle and the challenging vehicle (static obstacle) at the cut-out starts is:

```
dx0 + dx0_f + length(NPC) = 2 * 13.889 + 14 + 4 = 45.778 (m)
```

Since achieving the 2-second THW constraint in Autoware is challenging (Autoware often maintains a greater distance to the vehicle ahead for safety), 
we propose to dynamically spawn the challenging vehicle at the moment the cut-out starts, ensuring that the distance from the spawning position to the ego vehicle equals the distance above.

A collision occurred in both perception modes ([video](Screencasts/camera_lidar_fusion/cutout-50-1.mp4?ref_type=heads) above).

## Deceleration scenarios
### Scenario 20

In this [scenario](AWSIM-Script/deceleration/deceleration20.script), the ego vehicle and the NPC vehicle ahead travel at a speed of 20 km/h (`Ve` and `Vo`) on the same traffic lane, with a longitudinal distance of twice the THW between them.
The NPC vehicle suddenly decelerates and stops at a deceleration of 1.0G.

Similar to the cut-out scenario, we propose to dynamically spawn the challenging vehicle to achieve the 2-second THW constraint in Autoware.

A collision occurred in the camera-lidar fusion perception mode ([video](Screencasts/camera_lidar_fusion/decel-20.mp4?ref_type=heads) above).

In contrast, the lidar-only mode could avoid a collision (see [video](Screencasts/lidar/decel-20.mp4?ref_type=heads) below).
