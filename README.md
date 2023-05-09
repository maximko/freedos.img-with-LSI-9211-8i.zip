# freedos.img-with-LSI-9211-8i.zip

This is a dd-ready drive image with FreeDOS and all the files from LSI-9211-8i.zip to flash your Dell H200 RAID controller to a dumb HBA (IT firmware). May also be used to flash other SAS2008-based controllers.

## Usage
1. Download the image and unpack it:

```wget https://raw.githubusercontent.com/maximko/freedos.img-with-LSI-9211-8i.zip/master/FreeDOS-1.1-memstick-2-2048M-LSI-9211-8i.zip.img.zst && zstdmt -d FreeDOS-1.1-memstick-2-2048M-LSI-9211-8i.zip.img.zst```

2. Write the image to a drive using dd as usual:

```dd if=FreeDOS-1.1-memstick-2-2048M-LSI-9211-8i.zip.img of=/dev/null bs=1M status=progress```

3. Boot FreeDOS and change directory to ```lsi/```

```cd lsi```

4. Follow [this guide](https://techmattr.wordpress.com/2016/04/11/updated-sas-hba-crossflashing-or-flashing-to-it-mode-dell-perc-h200-and-h310/) to perform crossflash
5. Carefully read [this post](https://www.truenas.com/community/resources/detailed-newcomers-guide-to-crossflashing-lsi-9211-9300-9305-9311-9400-94xx-hba-and-variants.54/) in case of troubles

## Notes
- You also can remotely mount this image using Virtual Media or similar feature. I've successfully used it with Avocent MPU2016 IP-KVM
- I had no luck to flash my H200 using Dell R510 server no matter of PCIe slot or bios settings. I did that using non-raid pcie slot of my Fujitsu RX200-S8
- If you want to boot from attached drives you also need to flash ```x64sas2.rom``` and/or ```mptsas2.rom``` (mind the ```-b``` option insted of ```-f```). Look for it somewhere in ```FIRMWARE/```:

```sas2flsh.exe -o -b x64sas2.rom```

```sas2flsh.exe -o -b mptsas2.rom```

## Sources
- [LSI-9211-8i.zip](https://www.mediafire.com/download/6mtie10d9ud6675/LSI-9211-8i.zip) found in [this awesome guide](https://www.truenas.com/community/resources/detailed-newcomers-guide-to-crossflashing-lsi-9211-9300-9305-9311-9400-94xx-hba-and-variants.54/)
- [FreeDOS-1.1-memstick-2-2048M.img](https://myhq.it/sites/myhq.it/files/FreeDOS-1.1-memstick-2-2048M.img.bz2) backed up from [this site](https://web.archive.org/web/20160224081331/http://www.chtaube.eu/computers/freedos/bootable-usb/) found in [archlinux wiki bios flashing article](https://wiki.archlinux.org/title/Flashing_BIOS_from_Linux#Pre-built_images)

## Everything else
Feel free to open an issue if you need any help. Hit that ⭐ button and follow me for more cool repos.