---
layout: default_c
RefPages:
 - howto_create_a_dev_container   
--- 

<small>
<br><br>
_Copyright (c) 2025 Nico Jan Eelhart_
_This source code is licensed under the MIT License found in the  'LICENSE.md' file in the root directory of this source tree._
</small>
<br><br><br>

# 1. Create the WSL Backend to Support X11

This chapter explains how to set up a WSL backend environment in case you want to run graphical programs from WSL using the X11 protocol instead of the default WSLg protocol (which is limited). This enables graphical output from your WSL container to be displayed on the Windows host via X11.

Another possible use case is when Docker containers inside the WSL environment need to display graphical output on the Windows host. This setup ensures that the Docker output is correctly relayed using the `$DISPLAY` variable. (While we don’t know why you'd need this setup specifically, we include it here to show what is possible!)
  

>📍**Correction: Docker and WSL**{: style="color:red;font-size:13px; "} <br>
> <small>A Docker container running on your Windows host can also use WSL and provide graphical output. In this case, graphical output is forwarded from the container to the Windows host using **WSLg**. <br> <br>
>However, you do not need to manually install and configure a WSL environment yourself, as I previously believed and documented in my Stacks. Instead Docker Desktop creates an implicit WSL environment for you (usually named docker-desktop) that uses the WSLg engine. <br><br>
>To make the WSL environment work with your container:  </small>

> - <small>Ensure Docker Desktop is configured to use the **WSL 2 engine** </small>  <br>
> - <small>Inside your Docker container, **set the $DISPLAY** environment variable correctly to point to your Windows host IP (e.g. **export DISPLAY=\<host-ip\>:0**) </small> 
>
> This document continues to describes the X11 setup, which **allows** displaying complete Linux desktop environments (GNOME, KDE, etc.) within Windows, **unlike** WSLg which only shows individual applications.
> &nbsp;

## 2.1 The WSL Container installation

This is the the overview of required actions to be performed to enable X11 on a WSL environment
### Overview

- **Download the WSL version of Ubuntu**: Get the manual installation files.
- **Install WSL2**: Create a dedicated WSL2 environment as backend for the Docker container.
- **Configure the WSL Ubuntu Distribution**: Ensure proper configuration.
- **Install and Configure an X-Server**: Use VcXsrv on the Windows host.

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

Place the WSL files in centralized location, i.e. `./wsl/wsl-x11/` directory.

<pre class="nje-cmd-multi-line">
cd .\wsl\wsl-x11

wsl --import image-wsl-x11 ./wsl/wsl-x11 install.tar.gz
</pre>

This creates the file:  `image-wsl-x11
` WSL distro in `./wsl/wsl-x11
`.

Other useful WSL commands:

<pre class="nje-cmd-multi-line">
wsl --list --verbose              # List all distributions with status
wsl --unregister YourDistro       # Remove a distribution
</pre>

---

### 2.1.3 Configure the Ubuntu WSL Version

Start and manage your WSL2 Ubuntu distribution:

<pre class="nje-cmd-multi-line">
wsl -d image-wsl-x11                      # Opens the WSL terminal
wsl --list --verbose                      # Check if it's running
wsl --terminate image-wsl-x11             # Stop it
wsl -d image-wsl-x11 -- ls /home          # Run the ls command directly
wsl --set-default image-wsl-x11           # Set as default
</pre>

Inside the WSL, execute these command (one time):

<pre class="nje-cmd-multi-line">
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
</pre>

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
- Open the container (`wsl -d image-wsl-x11`)
- Run these commands
<pre class="nje-cmd-multi-line">
sudo apt install x11-apps -y
xeyes
</pre>

You should see two eyes following your mouse if XLaunch is running.

**Test 2: Check if X11 is used**
- Run this command in the container
<pre class="nje-cmd-multi-line">
echo $DISPLAY
</pre>

* If it shows `:0`, WSLg is likely used
* If it shows something like `172.27.112.1:0`, X11 via XLaunch is working
