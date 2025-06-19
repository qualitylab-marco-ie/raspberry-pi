# Raspberry Pi

Great choice with the Raspberry Pi 5! It’s powerful and perfect for a wide range of projects. Here's a recommended setup for a **brand new Raspberry Pi 5**, assuming you're starting fresh and want flexibility for various projects (e.g., automation, IoT, scripting, electronics, etc.).

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
