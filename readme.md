# mobile-aloha

## 1. Environment Setup

1. Download the cobot-magic project:
~~~bash
git clone https://github.com/agilexrobotics/cobot_magic.git
~~~

2. Compile:
~~~bash
cd cobot_magic/remote_control
./tools/build.sh

cd cobot_magic/camera_ws
catkin_make
~~~


## 2. Testing

~~~bash
# 1. Setup rule
ls /dev/ttyACM*

udevadm info -a -n /dev/ttyACM* | grep serial -m 1

sudo vim /etc/udev/rules.d/arx_can.rules

sudo udevadm control --reload && sudo udevadm trigger

# 2. Start remote arm
cd remote_control
./tools/can.sh

cd master1

source devel/setup.bash

roslaunch arm_control arx5v.launch
~~~


## 3. Data Collection

~~~bash
# 1. Start roscore
roscore

# 2. Start the robotic arm and camera
./tools/remote.sh

# 3. Collect data
python collect_data.py --max_timesteps 500 --dataset_dir ./data --episode_idx 0
~~~


## 4. Model Training and Inference

~~~bash
# 1. Activate virtual environment
conda activate aloha

# 2. Training
python act/train.py --dataset_dir ~/data0314/ --ckpt_dir ~/train0314/ --batch_size 4 --num_epochs 3000

# 3. Inference
## 3.1 Start the secondary arm only
cd remote_control
./tools/puppet.sh

## 3.2 Start inference code
python act/inference.py --ckpt_dir ~/train0314/
~~~


---

# Contact Us

# Contact Information

- **Sales Email:** [Sales@agilex.ai](mailto:Sales@agilex.ai)
- **Phone Numbers:**
  - 0755-86165015 (Monday to Friday)
  - 17796377363 (Weekends and Holidays)

---

## WeChat

- **Scan QR Code to Add Friends:**
  - 松灵机器人 (AgileX Robotics)
  - 售后服务 (After-Sales Service)

![WeChat QR Codes](./collect_data/docs/1.jpg)  <!-- Replace with the actual path to the QR code images -->

---

# Addresses

- **Dongguan Office Address:**
  Dongguan City, Songshan Lake Small and Medium-Sized Enterprise Venture Park, Building 10, Floor 1

- **Shenzhen Office Address:**
  Shenzhen City, Nanshan District, Zhigu Industrial Park, Building A3, Floor 9

---

## Additional Emails

- **Marketing Email:** [Marketing@agilex.ai](mailto:Marketing@agilex.ai)
- **HR Email:** [hr@agilex.ai](mailto:hr@agilex.ai)
