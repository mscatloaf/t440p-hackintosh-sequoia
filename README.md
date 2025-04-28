# t440p-hackintosh-sequoia
The efi I use to run macos on Lenovo Thinkpad t440P

Working
- intel wifi with itlwm (use heliport app to connect)
- intel bluetooth
- keyboard and trackpad with gesture support
- suspend resume with hibernation disabled
- graphics (requires oclp root patches)
- battery (with new 6 cell one, battery life is actually quite good)
- cpu pm, fan
- graphical boot menu with chime
- usb map
- sound in macos

Broken
- iServices and continuity (I did not bother trying to make them work since I don't need them)
- natively supported wifi card requires bios mod with ch341a programmer to remove whitelist

Notes:
- generate a serial number with gensmbios before using config.plist, use MacBookPro11,2 smbios
- get your own copy of macos by making it on a mac or using macrecovery.py
- macos installation will fail with recommmended smbios, solution is to use a newer, supported smbios such as MacBookPro15,2 during install, and change to MacBookPro11,2 after first reboot, make sure to reset nvram after doing this
- IMPORTANT: if you have issues after the first reboot, try setting Misc > Security > SecureBootModel to Disabled, can be changed back to Default after installation is complete, if you need this change, reset nvram to make sure it applies

Known issues:
- webgl is broken in safari but works with chromium and firefox based browsers
- drm also doesn't workin safari (known problem with hackintosh)
- installation requires ethernet or full (offline) installer created in macos
- USB devices can cause failure to go to sleep, sleep works reliably with no USB devices
- Keyboard and mouse will very ocasionally be disabled after sleep which requires forced power off
- # Make sure to DISABLE security chip in BIOS or you will have issues with sleep

Not tested:
- Nvidia GPU (I do not have nvidia model)
- iGPU other than HD 4600 (make relevant changes to DeviceProperties)

Credits:
- Apple: macOS
- Lenovo: Thinkpad T440p
- Dortania: opencore
- https://github.com/daliansky/OC-little/blob/master/10-PTSWAK综合扩展补丁/SSDT-EXT5-TP-LED.md: ACPI fix I used to make the LED blink properly after sleep, requires YogaSMC.kext
