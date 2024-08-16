#### Install the Debian 12 Minimal Template
First, you need to install the Debian 12 minimal template if you haven’t already:
```
sudo qubes-dom0-update qubes-template-debian-12-minimal
```

#### Basic Configuration
After installing the template, you can configure it by installing essential packages. Open a terminal in the Debian 12 minimal template and run:
```
qvm-run -u root <DISTRO_NAME>-<RELEASE_NUMBER>-minimal xterm
sudo apt install qubes-core-agent-networking qubes-core-agent-dom0-updates qubes-core-agent-passwordless-root
```
These packages are necessary for networking and updates.

#### Additional Useful Packages
Depending on your needs, you might want to install additional packages. Here are some common ones:
```
sudo apt install qubes-core-agent-passwordless-root qubes-core-agent-nautilus gnome-terminal
```

#### Minimizing the Template
To further minimize the template, you can remove non-essential packages (apt-get autopurge them):
```
sudo apt-get autopurge aptitude cpio cron debconf-i18n eatmydata fdisk gnupg gpgv haveged ifupdown iproute2 iputils-ping isc-dhcp-client isc-dhcp-common less libbpf1 libcap2-bin libglib2.0-bin libglib2.0-data libjansson4 libmnl0 libnewt0.52 libnftables1 libnftnl11 libregexp-ipv6-perl libtext-charwidth-perl libxtables12 logrotate mawk nano netbase nftables perl perl-modules-5.36 tasksel vim-common vim-tiny whiptail xterm
```

Be cautious with this step, as removing some packages might affect the functionality you need.

After that, the administrative tasks, e.g. installing software, can be done through qvm-console-dispvm.
It is important to note that if the template will be used for networking AppVMs, netbase must be installed (qubes-core-agent-networking will not work without it). It is not required in the template itself (for package installation).

#### Reducing RAM Usage
For non-networked qubes, you can deactivate unnecessary network services:
```
sudo systemctl mask systemd-networkd.service
sudo systemctl mask systemd-networkd.socket
sudo systemctl mask systemd-networkd-wait-online.service
```

For headless service VMs, disable audio and GUI:
```
qvm-prefs <your-qube> audiovm ''
qvm-prefs <your-qube> guivm ''
```
This will require using qvm-run with the --no-gui option1.

#### Final Steps
After making these changes, restart the template to apply the configurations:
```
sudo reboot
```
