# Raspberry Pi

---

### 🔧 **Essential Setup**

#### 1. **Operating System**

Install **Raspberry Pi OS (Bookworm)** — the official and best-supported OS:

* Go to: [https://www.raspberrypi.com/software](https://www.raspberrypi.com/software)
* Download and use the **Raspberry Pi Imager** to flash the OS to your microSD or SSD.
* Choose:

  * `Raspberry Pi OS (64-bit)` (recommended for most uses)
  * Enable SSH, Wi-Fi, and set hostname/password during flashing.

#### 2. **System Updates**

Once booted, update everything:

```bash
sudo apt update && sudo apt full-upgrade -y
```

#### 3. **Install Git**

Useful for version control and downloading project repos:

```bash
sudo apt install git -y
```

#### 4. **Enable Interfaces**

Use `raspi-config`:

```bash
sudo raspi-config
```

Enable:

* SSH (if not already)
* I2C
* SPI
* Serial
* Camera (if needed)
* VNC (for GUI remote access)

---

### 🧰 **General Tools**

| Tool              | Install Command                    | Purpose                  |
| ----------------- | ---------------------------------- | ------------------------ |
| `curl` / `wget`   | `sudo apt install curl wget`       | Downloading tools        |
| `build-essential` | `sudo apt install build-essential` | Compiler and build tools |
| `python3-pip`     | `sudo apt install python3-pip`     | Python package manager   |

---

### 🧪 **For Electronics/Automation Projects**

#### Python Libraries:

```bash
pip3 install RPi.GPIO gpiozero smbus2 adafruit-circuitpython-dht
```

#### I2C Tools:

```bash
sudo apt install i2c-tools
```

---

### 🔒 **Security Tips**

* Change the default password if you haven’t.
* Use SSH keys if possible.
* Keep the system updated.
* Disable services you don’t use.


Perfect — if you're planning to use your **Raspberry Pi 5** as an embedded system controller (relays, flow meters, sensors, etc.), here’s a focused setup tailored specifically for **embedded systems development**, especially with **Python, GPIO, UART, I2C, SPI**, and basic automation tools.

---

## ✅ Base Setup Recap (if not done yet)

Make sure:

* **OS**: Raspberry Pi OS 64-bit (Bookworm)
* **Updated system**:

```bash
sudo apt update && sudo apt full-upgrade -y
```

* **Developer tools**:

```bash
sudo apt install git build-essential python3-pip python3-venv -y
```

---

## ⚙️ Essential Libraries & Tools for Embedded Projects

### 🧪 Python GPIO & Sensors

```bash
sudo apt install python3-rpi.gpio python3-gpiozero i2c-tools -y
pip3 install smbus2 adafruit-blinka adafruit-circuitpython-ssd1306 adafruit-circuitpython-dht
```

| Library                 | Purpose                                  |
| ----------------------- | ---------------------------------------- |
| `RPi.GPIO`              | Low-level GPIO access                    |
| `gpiozero`              | High-level GPIO abstraction              |
| `smbus2`                | I2C communication                        |
| `Adafruit_Blinka`       | Compatibility layer for Adafruit sensors |
| `CircuitPython` drivers | For sensors, OLED displays, flow meters  |
| `i2c-tools`             | I2C device scanner                       |

---

### 📟 Serial Communication (UART/RS485)

```bash
sudo apt install python3-serial -y
```

To enable UART:

```bash
sudo raspi-config
# → Interface Options → Serial → No (login shell), Yes (serial port)
```

Useful lib:

```bash
pip3 install pyserial
```

---

### 🧰 Control Relays (GPIO or I2C)

* GPIO relay boards: use `RPi.GPIO` or `gpiozero`
* I2C relay boards (like PCF8574): use `smbus2` and custom drivers

Simple GPIO example:

```python
import RPi.GPIO as GPIO
GPIO.setmode(GPIO.BCM)
GPIO.setup(17, GPIO.OUT)
GPIO.output(17, GPIO.HIGH)  # Turn relay ON
GPIO.output(17, GPIO.LOW)   # Turn relay OFF
GPIO.cleanup()
```

---

## 🛠 Recommended Folder Structure

```bash
~/Projects/embedded/
├── relay_control/
├── flow_meter_reader/
├── sensor_monitor/
├── lib/
└── logs/
```

---

## 📈 Data Logging & Visualization

Install CSV & JSON tools:

```bash
pip3 install pandas
```

Install lightweight dashboards:

```bash
pip3 install flask
```

Or use:

* **Jupyter Notebook**: For debugging and visualizing sensor data
* **Node-RED**: If you prefer flow-based programming for automation

---

## 📋 Flow Meter Reading (Pulse Counting)

Install `pigpio` for more accurate pulse counting:

```bash
sudo apt install pigpio python3-pigpio -y
sudo systemctl enable pigpiod
sudo systemctl start pigpiod
```

Example for pulse reading:

```python
import pigpio

FLOW_PIN = 4
pulses = 0

def pulse_callback(gpio, level, tick):
    global pulses
    pulses += 1

pi = pigpio.pi()
pi.set_mode(FLOW_PIN, pigpio.INPUT)
cb = pi.callback(FLOW_PIN, pigpio.RISING_EDGE, pulse_callback)

try:
    while True:
        print(f"Pulses: {pulses}")
        time.sleep(1)
except KeyboardInterrupt:
    cb.cancel()
    pi.stop()
```

---

## 🔄 System Automation

Set your scripts to run on boot with:

* `cron` (`@reboot`)
* `systemd` service
* `rc.local` (if enabled)

---

## 🧪 Optional but Useful

| Tool               | Install                                        | Purpose                       |
| ------------------ | ---------------------------------------------- | ----------------------------- |
| `tmux`             | `sudo apt install tmux`                        | Persistent terminal sessions  |
| `MQTT` (mosquitto) | `sudo apt install mosquitto mosquitto-clients` | Sensor messaging over network |
| `SQLite3`          | `sudo apt install sqlite3`                     | Lightweight local database    |

---

## 🧰 Extras for Development Comfort

```bash
sudo apt install thonny geany vim -y
```

* **Thonny**: Great Python IDE
* **Geany**: Lightweight general-purpose IDE

---

Would you like a **starter Python script** to:

* Read a flow meter
* Log data to CSV
* Control a relay based on flow?

Or help making it **auto-start on boot**?
