# ROS2 Jazzy Publisher/Subscriber Demo

A minimal ROS2 Jazzy workspace demonstrating the publisher/subscriber pattern in both **Python** (`rclpy`) and **C++** (`rclcpp`). Both packages publish and subscribe on the same `chatter` topic using `std_msgs/String`.

```
ros2_pubsub_demo/
└── src/
    ├── demo_pubsub/          # Python (ament_python)
    │   └── demo_pubsub/
    │       ├── publisher.py
    │       └── subscriber.py
    └── demo_pubsub_cpp/      # C++ (ament_cmake)
        └── src/
            ├── publisher.cpp
            └── subscriber.cpp
```

## Requirements

- [ROS2 Jazzy](https://docs.ros.org/en/jazzy/Installation.html)
- Ubuntu 24.04 (Noble) recommended

## Build

```bash
# Clone the repo
git clone https://github.com/<your-username>/ros2_pubsub_demo.git
cd ros2_pubsub_demo

# Source ROS2
source /opt/ros/jazzy/setup.bash

# Build all packages
colcon build

# Source the workspace overlay
source install/setup.bash
```

## Run

Open separate terminals and source the workspace in each (`source install/setup.bash`).

### Python nodes

```bash
# Terminal 1 – Python publisher
ros2 run demo_pubsub py_publisher

# Terminal 2 – Python subscriber
ros2 run demo_pubsub py_subscriber
```

### C++ nodes

```bash
# Terminal 1 – C++ publisher
ros2 run demo_pubsub_cpp cpp_publisher

# Terminal 2 – C++ subscriber
ros2 run demo_pubsub_cpp cpp_subscriber
```

### Cross-language (Python publishes → C++ subscribes, or vice versa)

Because both packages use the same `chatter` topic, you can mix and match freely:

```bash
# Terminal 1 – Python publisher
ros2 run demo_pubsub py_publisher

# Terminal 2 – C++ subscriber
ros2 run demo_pubsub_cpp cpp_subscriber
```

### Inspect the topic

```bash
# List active topics
ros2 topic list

# Echo messages on the chatter topic
ros2 topic echo /chatter

# Check publisher/subscriber info
ros2 topic info /chatter
```

## License

Apache-2.0
