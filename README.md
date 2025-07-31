# Mocap ROS 2 - NatNet Bridge

A ROS 2 package to publish Motion Capture (MoCap) data over the NatNet protocol.

This package connects to a machine running OptiTrack Motive and publishes the pose data of all rigid bodies configured in the software, including their IDs. The connection settings can be modified in the parameter file inside the `config` folder.

The package is based on the NatNet SDK sample: [NatNet SDK](https://optitrack.com/support/downloads/developer-tools.html#natnet-sdk).  
This project includes work derived from the NatNet SDK by OptiTrack. Redistribution or reuse of this code may be restricted—please contact the original copyright holder.

---

## Overview

The `mocap_ros2` package provides a ROS 2 node that publishes rigid body pose data using the MoCap NatNet protocol. It connects to a given IP and port (where Motive is running) and publishes pose and ID information for all rigid bodies set up in the Motive environment.

---

## Prerequisites

- ROS 2 (e.g., Humble or later)
- OptiTrack Motive (on a Windows machine)
- Rigid bodies configured in Motive

---

## Installation

1. Clone the repository and build it in your ROS 2 workspace:

    ```bash
    mkdir -p mocap_ws/src && cd mocap_ws/src
    git clone https://github.com/hpaul360/natnet_bridge_ros2.git
    cd ..
    colcon build --symlink-install
    ```

2. Edit the parameter file to set the correct IP and port for your OptiTrack Motive setup. File:  
   `mocap_ros2/mocap_client/config/params.yaml`

    ```yaml
    # Dummy mode (for testing without Motive)
    dummy_send: false  # Set to true to send dummy data
    send_rate: 100
    number_of_bodies: 1
    dummy_x: 0.0
    dummy_y: 0.0
    dummy_z: 1.0
    dummy_qx: 0.0
    dummy_qy: 0.0
    dummy_qz: 0.0
    dummy_qw: 1.0

    # Network settings
    server_address: "192.168.0.98"
    multicast_address: "239.255.42.99"
    connection_type: 0  # 0 = multicast, 1 = unicast
    server_command_port: 1510
    server_data_port: 1511

    # ROS 2 topic and options
    pub_topic: "/mocap/rigid_bodies"
    record: false
    record_file_name: ""
    ```

---

## Usage

1. Ensure Motive is running on the Windows PC, and the machine is on the same network.
2. Launch the node:

    ```bash
    source mocap_ws/install/setup.bash
    ros2 launch mocap_client mocap.launch.py
    ```

3. The node will connect to Motive, publish pose data for all rigid bodies, and output their IDs.

---

## Configuration

All runtime parameters can be adjusted in:
`mocap_ros2/mocap_client/config/params.yaml`


---

## Author

- [Hannibal Paul](https://github.com/hpaul360)

---

## Acknowledgments

This package uses the NatNet SDK provided by OptiTrack.  
Redistribution or reuse may be restricted. Please consult the [NatNet SDK license](https://optitrack.com/support/downloads/developer-tools.html#natnet-sdk) or contact OptiTrack for permission.

---

## Issues and Contributions

To report issues or contribute to development, visit the [GitHub repository](https://github.com/hpaul360/mocap_ros2).

---

## Contact

For questions or support, contact the author:  
[Hannibal Paul](https://hannibalpaul.com/)

