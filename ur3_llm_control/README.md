# Hướng dẫn chạy UR3 LLM Control

## 1. Build package

```bash
cd ~/ros2_ws
source /opt/ros/humble/setup.bash
colcon build --symlink-install --packages-select ur3_llm_control
source install/setup.bash
```

## 2. Chạy mô phỏng

Mở Terminal 1:

```bash
source /opt/ros/humble/setup.bash
source ~/ros2_ws/install/setup.bash
export ROS_DOMAIN_ID=24
export NINE_ROUTER_BASE_URL="http://localhost:20128/v1"
export NINE_ROUTER_MODEL="YOUR_MODEL_ID"
read -rsp "9Router API key: " NINE_ROUTER_API_KEY; echo
export NINE_ROUTER_API_KEY
ros2 launch ur3_llm_control llm_robot.launch.py
```

Thay `YOUR_MODEL_ID` bằng model đang dùng trên 9Router và nhập API key khi terminal yêu cầu.

## 3. Mở RViz

Mở Terminal 2:

```bash
source /opt/ros/humble/setup.bash
source ~/ros2_ws/install/setup.bash
export ROS_DOMAIN_ID=24
ros2 launch ur3_llm_control rviz.launch.py
```

## 4. Gửi lệnh cho robot

Mở Terminal 3:

```bash
source /opt/ros/humble/setup.bash
source ~/ros2_ws/install/setup.bash
export ROS_DOMAIN_ID=24
```

Ví dụ điều khiển từng khối:

```bash
ros2 run ur3_llm_control command "Move the yellow cube to zone A."
ros2 run ur3_llm_control command "Pick up the blue cube and place it in zone B."
ros2 run ur3_llm_control command "Please put the red cube in zone C."
```

Hoặc yêu cầu sắp xếp theo student ID 33:

```bash
ros2 run ur3_llm_control command "Arrange all objects according to student ID = 33."
```

Có thể nhập lệnh bằng tiếng Việt, ví dụ:

```bash
ros2 run ur3_llm_control command "Đưa khối màu vàng vào vùng A."
```

Giữ Terminal 1 chạy trong suốt quá trình điều khiển. Nhấn `Ctrl+C` tại Terminal 1 để dừng mô phỏng.
