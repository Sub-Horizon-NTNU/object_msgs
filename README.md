# object_msgs

Shared **ROS 2 message definitions for Selene's perception pipeline**. This package defines the data exchanged by object detection, environment estimation and mission code; it contains no executable detector or controller.

## Messages

| Message | Purpose |
| --- | --- |
| [Object](msg/Object.msg) | A detected object with timestamp/frame, 3D position and velocity, planar acceleration, ID, colour, type and confidence. |
| [Buoy](msg/Buoy.msg) / [Buoys](msg/Buoys.msg) | A buoy's planar position, colour and ID, and a list of buoys. |
| [Boat](msg/Boat.msg) / [Boats](msg/Boats.msg) | Boat position, velocity, acceleration and metadata, and a boat list with an amount field. |

The message files are the source of truth for exact field names. In particular, the current `Boat` interface spells its vertical velocity field `velocty_z`; consumers must use that spelling until the interface is changed in a coordinated update.

Used by [usv_object_detector](https://github.com/Sub-Horizon-NTNU/usv_object_detector), [environment_estimator](https://github.com/Sub-Horizon-NTNU/environment_estimator) and [usv_mission_package](https://github.com/Sub-Horizon-NTNU/usv_mission_package).

## Build

Place the repository in a ROS 2 workspace's `src/` directory. After sourcing ROS 2, run from the workspace root:

```sh
colcon build --packages-select object_msgs
source install/setup.bash
ros2 interface show object_msgs/msg/Object
```

Rebuild dependent packages after changing message definitions. Coordinate frames and units must be agreed by publishers and consumers; the definitions alone do not enforce them.
