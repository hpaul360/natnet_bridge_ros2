# Mocap ROS2 - NatNet bridge

MOCAP (NATNET protocol) position publisher in ROS2.

Connects to an IP and port running Motive and publishes all the rigid bodies set in the software, including their IDs. Edit the parameter file if required in the `config` folder.

The package is based on the NatNet SDK sample: [NatNet SDK](https://optitrack.com/support/downloads/developer-tools.html#natnet-sdk).
This project is based on work derived from the NatNet SDK by OptiTrack. Redistribution or reuse of this code may be restricted. Please contact the original copyright holder.


## Overview

The `mocap_ros2` package provides a ROS2 node for publishing position data using the MOCAP (Motion Capture) NATNET protocol. It connects to a specified IP and port running OptiTrack Motive, publishing position information for all rigid bodies configured in the Motive software, along with their respective IDs.

## Prerequisites

- ROS2 (Robot Operating System 2)
- OptiTrack Motive with configured rigid bodies

## Installation

1. Clone this repository to your ROS2 workspace:

    ```bash
    git clone https://github.com/hpaul360/mocap_ros2.git
    ```

2. Build the package:

    ```bash
    colcon build --symlink-install
    ```

3. Edit the parameter file in the `config` folder to set the correct IP and port for your OptiTrack Motive setup: mocap_ros2/mocap_client/config/params.yaml
   ```bash
   # Dummy parameters for testing
   dummy_send: false #true. Set it to false to connect to the mocap.
   send_rate: 100
   number_of_bodies: 1 # Same values will be sent for all the bodies
   dummy_x: 0.0
   dummy_y: 0.0
   dummy_z: 1.0
   dummy_qx: 0.0
   dummy_qy: 0.0
   dummy_qz: 0.0
   dummy_qw: 1.0
   # Connection parametrs
   server_address: "192.168.0.98"
   multicast_address: "239.255.42.99"
   connection_type: 0 #default value: 0. 0 = multicast, 1 = unicast.
   server_command_port: 1510
   server_data_port: 1511
   pub_topic: "/mocap/rigid_bodies"
   record: false #true. Record flag for Motive software 
   record_file_name: ""
   ```

## Usage

1. Ensure OptiTrack Motive is running with configured rigid bodies.
2. Launch the `mocap_ros2` node:

    ```bash
    ros2 launch mocap_client mocap.launch.py
    ```

3. The node will connect to Motive, publish position data for all rigid bodies, and output their respective IDs.

## Configuration

Edit the parameters in the `config/mocap_ros2_params.yaml` file to customize IP, port, and other settings as needed.

## Author
- [Hannibal Paul](https://github.com/hpaul360)
  
## Acknowledgments

The package is based on the NatNet SDK sample provided by OptiTrack.
This project is based on work derived from the NatNet SDK by OptiTrack. Redistribution or reuse of this code may be restricted. Please contact the original copyright holder.

## Issues and Contributions

Report any issues or contribute to the development of this package on [GitHub](https://github.com/hpaul360/mocap_ros2).

## Contact

For questions or further assistance, feel free to contact the author [Hannibal Paul](https://hannibalpaul.com/).
