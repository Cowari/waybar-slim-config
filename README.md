# Waybar Config

<img width="1918" height="48" alt="20250813_16h48m29s_grim" src="https://github.com/user-attachments/assets/f1257f09-5ba5-47b3-ade0-dff1f9f9cf66" />


This is a stylish and functional configuration for [Waybar](https://github.com/Alexays/Waybar), designed for use with Wayland compositors like Sway.
The configuration includes modules for system information, time, network status, and battery level.

## Features

- **Minimalist Design**: A modern and clean look with rounded corners and a pleasant color palette.
- **System Modules**:
  - CPU usage (`cpu`)
  - Memory usage (`memory`)
  - Disk usage (`disk`)
  - System temperature (`temperature`)
- **Clock**: Displays the current time in `HH:MM:SS` format.
- **Network**: Indicates network status (Wi-Fi, Ethernet, or disconnected).
- **Battery**: Shows battery level with different colors for states (normal, low, critical, charging).
- **Customizable**: Easily modifiable CSS styles for personalization.

## Installation

### Prerequisites

1. **Waybar**: Ensure Waybar is installed on your system. If not, install it:
   ```bash
   sudo pacman -S waybar  # For Arch Linux
   sudo apt install waybar # For Ubuntu/Debian
   ```

2. **Fonts**: Ensure you have fonts that support icons (e.g., Font Awesome):
   ```bash
   sudo pacman -S ttf-font-awesome  # For Arch Linux
   sudo apt install fonts-font-awesome # For Ubuntu/Debian
   ```

## Setup

1. Clone or download this repository:
   ```bash
   git clone https://github.com/Cowari/waybar-slim-config.git
   ```
Or download the ZIP file and extract it.

2. Copy all files from the repository to your Waybar configuration directory:
   ```bash
   cp -r waybar-slim-config/* ~/.config/waybar/
   ```
   
3. Ensure the custom scripts are executable
   ```bash
   chmod +x ~/.config/waybar/custom/*.sh
   ```
   
4. Launch Waybar:
   ```bash
   waybar
   ```
   
5. If you’re using Sway, add the following line to your config (~/.config/sway/config):
   ```bash
   bar {
     swaybar_command waybar
   }
   ```

## Network Script Configuration

The `network.sh` script is used to display the network status (Ethernet, Wi-Fi, or disconnected).
By default, the script is configured for specific network interfaces (`enp37s0` and `wlo1`). You may need to adjust these values to match your system's network interfaces.

### Steps to Configure the Script
1. Find Your Network Interfaces:
Run the following command to list all available network interfaces on your system:
   ```bash
   ip link show
   ```
Look for interface names such as:
- Ethernet: Often starts with `enp` or `eth` (e.g., `enp37s0`, `eth0`).
- Wi-Fi: Often starts with `wlp` or `wlo` (e.g., `wlo1`, `wlan0`).

2. Update the Script:
Open the `network.sh` script located at `~/.config/waybar/custom/network.sh`:
   ```bash
   nano ~/.config/waybar/custom/network.sh
   ```
Update the following lines with your interface names:
   ```bash
   eth_operstate=$(cat /sys/class/net/enp37s0/operstate)
   wifi_operstate=$(cat /sys/class/net/wlo1/operstate)
   ```
Replace `enp37s0` or `enp0s20f0u3`, and `wlo1` with your actual interface names.

## License

This project is distributed under the [MIT License](https://mit-license.org). You are free to use, modify, and distribute it.

---

If you have any questions or suggestions, feel free to open an issue in this repository.
Thanks for using! 🚀
