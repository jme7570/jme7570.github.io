# jme7570.github.io

			Arch Linux assignment 

Installing arch Linux 

First you must go to the wiki provided on Harvey click that which will take you to the arch Linux wiki pages.

Next scroll down to Acquire an installation image
Click the download link
Scroll down to united states and click which ever one you choose 
Once installed you will need to go to VMware

Installing VMware 
Register then go to the VMware Workstation 16 Pro to download and request a key to access. This will give you access to run and perform your arch Linux on. 


Creating your own arch Linux on VMware workstation 16 pro
Create new virtual machine
Click normal hit next
Iso- which is the one you downloaded form arch Linux
Linux kernel 64bit 
Name your arch Linux mine is jme7570 arch project 3 
Set size to 20 for disk space 
Customize hardware 2 gigs is all you really need
Leave as highest version click next
 Linux 5 64 bit kernel 

Number or processors 1 
Number or course processors is 2
Select 2GB unless you don’t have enough room 

Create new virtual disk recommended 20 Gigs 
Don’t allocate right away or else it will take up all space 
Hit finish.

Turing on VM
Turn on and run boot into bios mode
To save to files on vs you need to us on command line firmware= “efi”

Verify boot mode 
ls /sys/firmware/efi/efivars
then you want to use  ip link
to make sure you are connected to the internet
if there is 5 pings that means it is working correctly and you have internet 

Update the system clock
timedatectl status

Partition the disks
Cfdisk /dev/sda
First partion should be 1M
if you need help hit the m and will list it all for you 
select the gpt then go into partion window type being bios boot 
new one then set it to 4G and  type should be linux swap
third partion is remaining space for linux filesystem slect write then click yes to save


Format the Partitions
mkfs.ext4 /dev/sda3
mkswap /dev/sda2 enable it by swapon -a
mount /dev/sda3 /mnt
you should see if set up correctly “lost+found”


select the mirrors
nano /etc/pacman.conf
pacman -Syy
pacstrap /mnt base linux linux-firmware vim grub zsh openssh sudo
may take awhile to download just wait a little

check for internet
ping archlinux.org
pacstrap /mnt dhcpcd
configuration files 
genfstab /mnt
genfstab /mnt >> /mnt/etc/fstab


change root user 
arch-chroot /mnt
root@archiso /
to add a user you will need to useradd -m -G sudo codi as well as useradd -m -G sudo james
change password is passwd. For coid it will be “GraceHopper1906” and for james it will be “help”

config the grub 
grub-install /dev/sda
grub-mkconfig -o /boot/grub/grub.cfg


Time zone
ln -sf /usr/share/zoneinfo/tulsa /etc/localtime

to check it 
hwclock --systohc

Base packages 
Pacman -S db
Pacman -S man-pages
Pacman -S texinfo
Pacman -S sudo 

Ready to reboot your system 

 Installing a ZSH 
Pacman -S curl wget git zsh if you haven’t done so 

Install SSH 
Pacman -S openssh if you haven’t done so 

Installing the GNOME for your desktop ENiroment (GUI)

Sudo pacman -Syu
Sudo reboot
Sudo pacman -S xorg xorg-server
Slecet all default and click y 

Now for he enivorment 
sudo pacman -S gnome
enter and default and click y to install

start and enabe gdm.service
sudo systemctl start gdm.servie
sudo systemctl enable gdm.service


choose a DM display manager
sudo pacman -S lxdm
sudo systemctl stop gdm.service
sudo systemctl disable gdm.service

now we start 
sudo systemctl start lxdm.service
sudo systemctl enable lxdm.service

Reboot system 
Exit out then do 
Sudo Reboot 

How to add color coding 
$ echo $TERM 
Xterm-256color

Export TERM=xterm-256color
Source ~/.bashrc

ANSI color codes 
Printf ‘\033[2J’
Backgroung I did printf ‘\033[107m


