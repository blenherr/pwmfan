# PWM Regulated Fan Based on CPU Temperature for Raspberry Pi

- [Installation guide](#installation-guide)
- [Configuration](#configuration)
- [Calibration](#calibration)
- [Add service](#add-service)
- [Acknowledgment](#acknowledgment)


# Installation guide
Install packages:
```
sudo apt install -y git
```
Clone git repository:
```
git clone https://github.com/blenherr/pwmfan.git
```

# Configuration
Change `FAN_PIN` to your used pwm pin in this files: `calibration.py` and `fanctrl.py`
```
nano ~/pwmfan/calibration.py
```
```
nano ~/pwmfan/fanctrl.py
```

# Calibration
Use the `calibration.py` program to find the `FAN_MIN` value by running in the terminal:
```
python ~/pwmfan/calibration.py
```

# Add service
Create `fanctrl.service` file
```
sudo nano /lib/systemd/system/fanctrl.service
```
Add following lines and change `your_user_goes_here` with your own user
```
[Unit]
Description=Raspberry Pi - PWM Fan Control

[Service]
Type=simple
User=your_user_goes_here
Group=your_user_goes_here
ExecStart=/usr/bin/python /home/your_user_goes_here/pwmfan/fanctrl.py
Restart=on-failure
RestartSec=10

[Install]
WantedBy=multi-user.target
```
Save and close

Enable service
```
sudo systemctl enable fanctrl
```
Start service
```
sudo systemctl start fanctrl
```


# Acknowledgment
- https://www.instructables.com/PWM-Regulated-Fan-Based-on-CPU-Temperature-for-Ras
