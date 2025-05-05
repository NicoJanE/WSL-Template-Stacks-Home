# 1. Create the WSL Backend to Support X11

This chapter explains how to set up a WSL backend environment in case you want to run graphical programs from WSL using the X11 protocol instead of the default WSLg protocol (which is often slower). This enables graphical output from your WSL container to be displayed on the Windows host via X11.

Another possible use case is when Docker containers inside the WSL environment need to display graphical output on the Windows host. This setup ensures that the Docker output is correctly relayed using the `$DISPLAY` variable. (While we don’t know why you'd need this setup specifically, we include it here to show what is possible!)
  

> 📍 Docker using Windows{: style="color:purple;font-size:13px; "}
> <small>A Docker container running on your Windows host can also use WSL and provide graphical output via the X11 protocol. In this case, graphical output is forwarded from the container to the Windows host using XLaunch.
>
>However, you do not need to manually install and configure a WSL environment yourself, as I previously believed and documented in my AFX stacks. Instead Docker Desktop creates an implicit WSL environment for you (usually named docker-desktop).
>
>To make the WSL environment work with your container:
>
> - Ensure Docker Desktop is configured to use the WSL 2 engine
> - Inside your Docker container, set the $DISPLAY environment variable correctly to point to your Windows host IP (e.g., export DISPLAY=<host-ip>:0)    
> &nbsp; <small> 
>
---

## 2.1 The Basic Container Setup

Before running the Docker Compose file for the basic service of the stack, ensure the required components are installed and configured. These items are explained in the following sections:

### Overview

* **Download the WSL version of Ubuntu**: Get the manual installation files.
* **Install WSL2**: Create a dedicated WSL2 environment as backend for the Docker container.
* **Configure the WSL Ubuntu Distribution**: Ensure proper configuration.
* **Install and Configure an X-Server**: Use VcXsrv on the Windows host.

---

### 2.1.1 Download the Special Ubuntu WSL Version

Finding the correct manual install version (.Appx or .AppxBundle) can be tricky. We need this instead of the Windows Store version because we want to control the installation name and location.

* Go to the [Microsoft WSL distributions download page](https://learn.microsoft.com/en-us/windows/wsl/install-manual).
* Scroll to the "Downloading distributions" section.
* Download the Ubuntu 24.04 `.AppxBundle` (this guide assumes this version).

For example, if you download `Ubuntu2204-221101.AppxBundle`, follow these steps:

1. Rename `Ubuntu2204-221101.AppxBundle` to `Ubuntu2204-221101.zip`
2. Unpack it using 7zip or similar
3. Find `Ubuntu_2204.1.7.0_x64.appx`, rename it to `.zip`, and unpack it
4. Inside you'll find `install.tar.gz` – this is what you’ll use in the next step

---

### 2.1.2 Install the Ubuntu WSL Version

We'll place the base container files inside the `./Base-Container/Afx-Base-Service/wsl2distro` directory.

```bash
cd .\Base-Container\Afx-Base-Service
wsl --import Ubuntu-docker-App-X11 ./wsl2-distro install.tar.gz
```

This creates the `Ubuntu-docker-App-X11` WSL distro in `./wsl2-distro`.

Useful WSL commands:

```bash
wsl --list --verbose              # List all distributions with status
wsl --unregister <YourDistro>     # Remove a distribution
```

---

### 2.1.3 Configure the Ubuntu WSL Version

Start and manage your WSL2 Ubuntu distribution:

```bash
wsl -d Ubuntu-docker-App-X11              # Open WSL terminal
wsl --list --verbose                      # Check if it's running
wsl --terminate Ubuntu-docker-App-X11     # Stop it
wsl -d Ubuntu-docker-App-X11 -- ls /home  # Run command directly
wsl --set-default Ubuntu-docker-App-X11   # Set as default
```

Inside WSL:

```bash
sudo apt update && sudo apt upgrade -y

# Set DISPLAY environment variable
export DISPLAY=$(grep -oP "(?<=nameserver ).+" /etc/resolv.conf):0

# Confirm it
echo $DISPLAY

# Make DISPLAY permanent
echo 'export DISPLAY=$(grep -oP "(?<=nameserver ).+")':0 >> ~/.bashrc

# Optional: Disable WSLg
echo 'unset WAYLAND_DISPLAY' >> ~/.bashrc
echo 'unset XDG_SESSION_TYPE' >> ~/.bashrc

source ~/.bashrc
exit
```

---

### 2.1.4 Install the X-Server (VcXsrv)

1. Download and install [VcXsrv](https://sourceforge.net/projects/vcxsrv/)
2. Run **XLaunch** and configure:

   * Select **Multiple Windows**, click *Next*
   * Select **Start no client**, click *Next*
   * Enable **Clipboard** and **Native opengl**
   * Make sure **Disable access control** is NOT checked (only enable if needed)
   * Click *Next*, then *Finish*

---

### 2.1.5 Test

**Test 1: Basic Graphics Check**

```bash
sudo apt install x11-apps -y
xeyes
```

You should see two eyes following your mouse if XLaunch is running.

**Test 2: Check if X11 is used**

```bash
echo $DISPLAY
```

* If it shows `:0`, WSLg is likely used
* If it shows something like `172.27.112.1:0`, X11 via XLaunch is working
