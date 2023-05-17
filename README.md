Wacom Tablet Configuration Scripts

These scripts automatically configure Wacom tablets when they're connected to your system. They set the mapping output and area for devices of type "STYLUS" or "ERASER".
Files

    wacom_setup.fish: This script is written in Fish shell script.
    wacom_setup.sh: This script is written in Bash shell script.

Usage

    Fish Script:

        First, ensure that your system has Fish shell installed. You can install it from your package manager. For example, on Ubuntu, you can install it with sudo apt-get install fish.

        To run the script, navigate to the directory containing the script and run fish wacom_setup.fish.

    Bash Script:
        Most Unix-like systems come with Bash pre-installed. To run the script, navigate to the directory containing the script and run bash wacom_setup.sh.

What the Scripts Do

The scripts run xsetwacom --list devices to get a list of all connected Wacom devices. They then parse this output to get the device ID and type of each device.

If a device's type is either "STYLUS" or "ERASER", the scripts run the following commands:

    xsetwacom set [device_id] MapToOutput 1920x1080+0+0
    xsetwacom set [device_id] Area 0 0 31920 17955

These commands set the mapping output and area for the device.
Note

Please make sure to replace the values of MapToOutput and Area with the values you need for your screen configuration. To map the Area to a 16:9 asspect ratio you shall do a very simple calculation: first run xsetwacom get area [device_id] than execute {tablet width*(screen height / screen width) eg. 31920*(1080/1920) in my case, if your monitor is 2K resolution or 4k resolution adjust accordingly. Also note I left the TOUCH and PAD out of the scripts on purpose, to be able to use all your screens regardless of the STYLUS mapping with touch compatible tablets. They can be added and you can create a pull request to create a new branch for comlete mapping including touch inputs. ENJOY =)