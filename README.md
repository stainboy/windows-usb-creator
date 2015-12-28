# Windows USB Creator

## Use Windows7-USB-DVD-Download-Tool.exe to create bootable USB stick
- login a Windows machine (e.g. Windows 10)
- goto page https://github.com/stainboy/windows-usb-creator/releases and download the binary
- extract the tool and run it

## Use raw tools to create bootable USB stick
- login a Linux machine (e.g. Ubuntu)
- insert USB stick (e.g. /dev/sdb)
- `sudo fdisk /dev/sdb`
- `o`
- `n -> p`
- `a`
- `w`
- `sudo mkdosfs /dev/sdb1 -s 16 -F 32`
- `sudo mount /path/to/windows-installer.iso /mnt/cdrom`
- `sudo mount /dev/sdb1 /mnt/usb`
- `sudo cp -r /mnt/cdrom/* /mnt/usb/`
- remove the USB stick
- login a Windows machine (e.g. Windows 10)
- insert USB stick (e.g. F:)
- start cmd.exe with administrative privilege
- `F:\boot\bootsect.exe /nt60 F: /force /mbr`
- `sudo lilo -M /dev/sdb mbr` (linux way)

## Burn windows installer ISO into a DVD disk
- login a Windows machine (e.g. Windows 10)
- right click on the windows-installer.iso, choose 'Burn disk image'
