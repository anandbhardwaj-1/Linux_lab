1. [Visual Studio Code](https://code.visualstudio.com)
2. [VirtualBox](https://www.virtualbox.org)
3. [Ubuntu (ISO)](https://ubuntu.com/download/desktop)

---

## 1️⃣ Install Visual Studio Code

### 🔵 Windows / 🍎 macOS / 🐧 Linux

1. Visit the [Visual Studio Code Download Page](https://code.visualstudio.com/Download).
2. Select your operating system:
   - **Windows** → `.exe` installer
   - **macOS** → `.zip` archive
   - **Linux** → `.deb` or `.rpm` package
3. Download and run the installer.
4. Follow the setup instructions.
5. (Optional) Enable the `code` command in terminal via the Command Palette (`Ctrl+Shift+P` or `Cmd+Shift+P` → type `Shell Command: Install 'code' command in PATH`).

✅ **VS Code is ready to use!**

---

## 2️⃣ Install VirtualBox

VirtualBox allows you to run virtual machines, such as Ubuntu, on your existing OS.

### Steps:

1. Go to the [VirtualBox Download Page](https://www.virtualbox.org/wiki/Downloads).
2. Choose your platform package:
   - **Windows hosts**
   - **macOS hosts**
   - **Linux distributions**
3. Download and run the installer.
4. Follow the installation wizard to complete the setup.

✅ **VirtualBox is now installed!**

---

## 3️⃣ Download Ubuntu ISO

Ubuntu is a popular Linux distribution you can install on a virtual machine.

### Steps:

1. Visit the [Ubuntu Desktop Download Page](https://ubuntu.com/download/desktop).
2. Click **Download** to get the latest LTS version (e.g., Ubuntu 24.04 LTS).
3. Save the `.iso` file to your computer.

📝 This ISO will be used when setting up the virtual machine in VirtualBox.

---

## ✅ Next Steps (Optional)

- Create a new Virtual Machine in VirtualBox.
- Use the Ubuntu `.iso` file as the startup disk.
- Install Ubuntu in the virtual machine.
- Once inside Ubuntu, install **VS Code** or any development tools you need.

---

## 📚 Resources

- [VS Code Docs](https://code.visualstudio.com/docs)
- [VirtualBox User Manual](https://www.virtualbox.org/manual/UserManual.html)
- [Ubuntu Installation Guide](https://ubuntu.com/tutorials/install-ubuntu-desktop)
![alt text](<Screenshot 2025-08-23 at 2.43.42 AM.png>)


# Extra Questions-
## ques1- What are the two advantages of installing ubuntu in virtual box?
## ans- Two main advantages of installing Ubuntu in VirtualBox are:
Safe Testing Environment 🛡️
You can experiment with Ubuntu without affecting your main operating system.
If something goes wrong (like system crash, misconfiguration, or malware), it only affects the virtual machine, not your actual computer.
Flexibility & Convenience ⚡
You can run Ubuntu alongside your existing OS (Windows/macOS/Linux) without dual-booting.
It allows you to easily switch between operating systems, take snapshots, and restore to a previous state quickly.

## ques2- What are the two advantages of dual booting instead of using a VM?
## ans- Two key advantages of dual booting instead of using a virtual machine (VM) are:
Better Performance ⚡
Dual boot gives the OS direct access to your computer’s hardware (CPU, RAM, GPU, etc.), so Ubuntu (or any other OS) runs much faster than inside a VM where resources are shared.
This is especially useful for gaming, programming with heavy tools, or tasks like video editing.
Full Hardware Compatibility 💻
Some hardware features (like GPU acceleration, Wi-Fi drivers, or USB devices) don’t always work smoothly in a VM.
With dual boot, Ubuntu interacts directly with the hardware, so you get maximum compatibility and stability.