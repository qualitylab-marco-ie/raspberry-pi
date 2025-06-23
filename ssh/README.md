# SSH Configuration

## Passwordless setup

### **Step 1: Enable SSH on Raspberry Pi**

#### Option A: If you have access to Raspberry Pi (monitor, keyboard)

1. Open terminal.
2. Run:

   ```bash
   sudo raspi-config
   ```
3. Go to: `Interface Options` → `SSH` → Enable.

---

### **Step 2: Find Raspberry Pi's IP Address**

   ```bash
   $ ip addr show wlan0
   ```

You’ll need the Pi's IP (e.g., `192.168.0.123`).

---

### **Step 3: Connect to Raspberry Pi Using SSH**

1. On Windows, open **Command Prompt** or **PowerShell**.

2. Connect via:

   ```bash
   ssh pi@192.168.0.123
   ```

   *(Replace `pi` with your username and IP with your Pi’s address)*

3. Enter the Pi’s password when prompted.

---

### **Step 4: Set Up SSH Key Authentication (No Password Login)**

#### On your Windows PC:

1. Open **PowerShell**.

2. Generate an SSH key (if you don't have one):

   ```bash
   ssh-keygen
   ```

   * Press **Enter** through all prompts to use default path and no passphrase.

   It creates:

   * Private key: `C:\Users\<yourname>\.ssh\id_rsa`
   * Public key: `C:\Users\<yourname>\.ssh\id_rsa.pub`

3. Copy your public key to your Raspberry Pi:

1. Open PowerShell:

   ```bash
   type $env:USERPROFILE\.ssh\id_rsa.pub
   ```

   * Copy the full text output.

2. On the Raspberry Pi (SSH in as usual):

   ```bash
   mkdir -p ~/.ssh
   nano ~/.ssh/authorized_keys
   ```

   * Paste the key.
   * Save and exit (`Ctrl+X`, then `Y`, then `Enter`)

3. Set correct permissions:

   ```bash
   chmod 700 ~/.ssh
   chmod 600 ~/.ssh/authorized_keys
   ```

---

### **Step 5: Test Passwordless SSH**

Now from Windows:

```bash
ssh pi@192.168.0.123
```

You should log in **without needing a password**.

---
