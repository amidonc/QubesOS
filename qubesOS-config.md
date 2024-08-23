## QubesOS configuration

### ACPI fix for Reboot & Suspend
&ensp; &ensp; &ensp; &ensp; `vim /etc/default/grub`
&ensp; &ensp; &ensp; &ensp; &ensp; &ensp; added `reboot=acpi` to line `GRUB_CMDLINE_XEN_DEFAULT`

### GPU
#### &ensp; &ensp; Find out which of intel or fbdev driver is in use:
&ensp; &ensp; &ensp; &ensp; `grep -E 'LoadModule.*(fbdev|intel)"' /var/log/Xorg.0.log` <br/>
&ensp; &ensp; &ensp; &ensp; &ensp; &ensp; eg. for intel: <br/>
&ensp; &ensp; &ensp; &ensp; &ensp; &ensp; (II) LoadModule: "intel" <br/>

