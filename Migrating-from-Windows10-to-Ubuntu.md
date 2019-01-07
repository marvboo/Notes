# Migrating from Windows 10 to Ubuntu on a laptop

---


##### Hardware
---

  *  Acer E5-575-33BM i3-7100U running Win10
      * a M.2 SSD standoff and screw were included
      * BIOS version 1.25
  *  M.2 256GB 2280 SSD
  *  External USB hard drive for data backup
  *  2GB USB stick

<br>

##### Prep and Installation
---

I used the [Ubuntu Installation guide][1], specifically the
[USB Installation guide][2]. Here are the steps that I ended up with.

1. Backup Windows data to the external USB hard drive
2. Download [Ubuntu 16.04.2 LTS][3] .iso file
3. Download [Rufus][4] and create a USB installer on the 2GB stick
4. Disable FastBoot in Windows
    * Control Panel >> Power Options
    * choose what the power buttons do
    * shutdown settings
    * deselect Fast startup
    * save
5. I did not modify Secure Boot or UEFI mode
    * e.g.,  Secure Boot on, UEFI boot selected
6. Shutdown Windows  (do not hibernate)
7. Disconnect laptop charger
    * remove laptop access panel
    * remove Windows hard drive (optional)
    * install 256GB M.2 SSD
    * replace laptop access panel
8. Edit BIOS (F2)
    * make sure the M.2 SSD is visible
    * move USB boot order up to first
    * save and plug in the USB stick installer before it reboots
9. Ubuntu boots from USB with a black background
    * select Try Ubuntu
    * give it a try, make sure WiFi works
    * when ready, click on the install icon on the Ubuntu desktop
10. Follow install prompts
    * I did not install 3rd party options
    * This can be done later with: sudo apt-get install ubuntu-restricted-extras
11. Reboot and remove USB stick


<br>
<br>

##### Minor Hiccup
---

After rebooting, I was greeted with a "No Bootable Device" message.
The solution was to set [UEFI trusted files][5].

1. Reboot
2. Edit BIOS , boot options
3. Set supervisor password, if you haven't already   
4. Set trusted UEFI file   
    * I ended up selecting shim.efi and grub.efi
    * select each file, type 'Yes', enter
5. Change the SSD to boot first, save and reboot

Success! Everything worked perfectly: WiFi, battery indicator, audio, USB ports,
suspend.

<br>



#### Resources:

---

1. [Ubuntu Installation](https://help.ubuntu.com/community/Installation)
2. [Ubuntu USB Installation](https://help.ubuntu.com/community/Installation/FromUSBStickQuick)
3. [Ubuntu Desktop Download](https://www.ubuntu.com/download/desktop)
4. [Rufus USB Installer](https://rufus.akeo.ie/)
5. [UEFI trusted files](https://itsfoss.com/no-bootable-device-found-ubuntu/)


[1]: https://help.ubuntu.com/community/Installation
[2]: https://help.ubuntu.com/community/Installation/FromUSBStickQuick
[3]: https://www.ubuntu.com/download/desktop
[4]: https://rufus.akeo.ie/
[5]: https://itsfoss.com/no-bootable-device-found-ubuntu/
