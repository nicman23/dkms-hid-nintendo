## ASUS HID FTE100* DKMS driver

Note that this DKMS driver is obsolete if you are running Kernel version 4.10 or later. It has been included in the base version of this Kernel.

This driver has also been backported to Yaketty (Ubuntu Kernel version 4.8) - so you will not need this DKMS driver if you are running Ubuntu 16.04.2 LTS with Kernel version 4.8 or later.

If you are running Ubuntu 16.04.2 LTS with an earlier Kernel version and would like to upgrade - please see the information [here](https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Ubuntu_16.04_LTS_-_Xenial_Xerus).

## Prerequisites

1. Ensure secure boot is not enabled (or you have an acceptable alterantive in place). With end-to-end secure boot enabled, 
after installing this DKMS driver you will get this error message in kernel log:

    ```
    modprobe: ERROR: could not insert 'hid_asus': Required key not available
    ```

    You won't be able to run third-party (aka 'out of tree') kernel modules with 
    secure boot. This is because for secure boot to work all the modules 
    have to be signed - and given our module is third party it hasn't been signed.

    If you want to use this module you'll need to disable secure boot.

2. Ensure `dkms` package is installed.

3. Ensure Linux kernel headers installed for your kernel version.

## Getting Started

1. Clone source code locally.

  ```
  git clone https://github.com/vlasenko/hid-asus-dkms.git
  cd hid-asus-dkms
  ```

2. Install DKMS driver and load kernel module into memory.

  ```
  ./dkms-add.sh
  ```

Check that multi-touch gestures work after executing this command
and after reboot as well.

## Submitting issues

Please use GitHub issue tracker for submitting issues with DKMS driver:

https://github.com/vlasenko/hid-asus-dkms/issues

This is the most convenient place for us to provide support on this project.

Please provide in your issue the output for the following three commands (preferably ran immediately after a completed reboot):
```
dmesg | grep hid
xinput
xinput list-props "Asus TouchPad"
```

This will allow us to confirm you have the correct hardware and that your X Input Drivers are configured correctly.

If the driver has installed correctly but is showing some edge case issues (like random movements) - you may need to configure your X Input Driver to ignore these edge cases. See [this](https://github.com/vlasenko/hid-asus-dkms/issues/42#issuecomment-283515964) for comments about how this can be acheived with the Synaptics driver.

## Updating to the latest driver version

1. Pull latest source code from repository.
  ```
  cd hid-asus-dkms
  git pull
  ```

2. Reinstall DKMS driver.

  ```
  ./dkms-add.sh
  ```

This will install DKMS driver into the system and reloads it immediately.

## Development Scripts

1. Script to clean compile the module from source without installing to dkms
  ```
  ./dev-run.sh
  ```
2. Script to bind touchpad to this DKMS driver, until reboot
  ```
  ./dev-attach.sh
  ```
3. Script to restore back touchpad handling by hid_generic driver, until reboot
  ```
  ./dev-restore.sh
  ```
