# Laptop Screen Dimmer Script

## Overview
This is a simple Bash script that uses `xrandr` to adjust screen brightness on Linux laptops, allowing dimming to levels lower than the system's default controls (e.g., below 1.0 for extra dimness). It's useful for low-light conditions or extending battery life.

**Developed on LMDE 6 with Kernel 6.1.0-28-amd64, specifically for built-in laptop screens (e.g., on a 13th Gen Intel Core i9-13900H setup). It may not work reliably on external monitors and could require modifications for other distributions, hardware, or multi-monitor setups.**

**Note**: This script modifies display settings via `xrandr`, which affects the gamma/brightness output. Use with caution to avoid eye strain or display issues. Tested on internal laptop displays only.

## Features
- Sets brightness as a float value between 0.0 and 1.0 (e.g., 0.1 for very dim).
- Automatically detects the primary connected display.
- Checks for required dependencies and provides installation instructions.
- Console-based output for errors and confirmations.

## Requirements
- **Operating System**: Linux (developed and tested on LMDE 6 / Debian-based distros). May need adaptations for other systems (e.g., Fedora, Arch) due to differences in package management or display servers.
- **Hardware**: Laptop with internal display supporting `xrandr` (e.g., Intel or NVIDIA GPUs like RTX 4070). **Not tested on external monitors; may require manual output specification for multi-display setups.**
- **Dependencies**:
  - `xrandr` (install via `sudo apt install x11-xserver-utils` on Debian-based systems).
  - `cut` (from coreutils, usually pre-installed).
- **Display Server**: X11 (as used in Cinnamon on LMDE 6). May not work on Wayland without adjustments.

## Installation
1. Clone or download the repository:
   ```
   git clone https://github.com/bladeofzion/dimmer.git
   cd laptop-screen-dimmer
   ```
2. Make the script executable:
   ```
   chmod +x dimmer  # Rename if needed
   ```
3. Install dependencies if missing (script will check and prompt):
   ```
   sudo apt update
   sudo apt install x11-xserver-utils
   ```

## Usage
Run the script from the terminal with a brightness value:


- `<brightness>`: A float between 0.0 (very dim/black) and 1.0 (normal). Values above 1.0 can brighten beyond normal.
- Example: `./screen-dimmer.sh 0.3` for moderate dimming.

The script detects the connected display automatically. If you have multiple monitors, you may need to modify it to specify the output (e.g., via `xrandr --output eDP-1 --brightness 0.3`).

## Warnings
- **Display-Specific**: Designed for laptop internal screens; external monitors may not respond or could behave unpredictably. Test carefully.
- **No GUI**: Outputs to console; consider adding Zenity for prompts if desired.
- **Risks**: Extremely low brightness (e.g., 0.0) can make the screen unusable—have a way to reset (e.g., reboot or run with 1.0).
- **Compatibility**: Assumes X11; for Wayland, use alternatives like `brightnessctl`. **Developed on LMDE 6; test on other systems and adjust for display outputs.**
- **Backup**: No warranty for display issues.

## Customization
- For external/multi-monitors: Edit the `xrandr` command to hardcode the output (e.g., replace with `--output eDP-1`—check yours via `xrandr`).
- Add range checks or GUI (e.g., Zenity slider) for better usability.
- Adjust for non-Debian systems by modifying dependency installation prompts.

## License
This project is licensed under the MIT License. See [LICENSE](LICENSE) for details. (Add a LICENSE file to your repo if desired.)

## Contributing
Feel free to fork and submit pull requests for improvements, such as multi-monitor support or Wayland compatibility.

## Credits
Developed for personal use on LMDE 6 laptops to achieve ultra-low brightness. Inspired by xrandr brightness guides.

*Last Updated: Monday, 21 July 2025, 10:07 PM*
