# PWM Regulated Fan Based on CPU Temperature for Raspberry Pi

# Installation guide
Install packages:
```
sudo apt install -y git
```
Clone git repository:
```
git clone https://github.com/blenherr/pwmfan.git
```
Copy fanctrl.service:
```
sudo cp pwmfan/fanctrl.service /lib/systemd/system/
```
Enable service:
```
sudo systemctl enable fanctrl
```
Start service
```
sudo systemctl start fanctrl
```

# Acknowledgment
- https://www.instructables.com/PWM-Regulated-Fan-Based-on-CPU-Temperature-for-Ras
