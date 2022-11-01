# Copy PI Sd card To USB
 https://www.helping.ninja/how-to-migrate-raspberry-pi-sd-card-to-a-usb-ssd-speedtest/

  # Speed Test 
   dd if=/dev/zero of=/tmp/speedtest1.img bs=20M count=5 oflag=direct
  # Git Install & clone code

   sudo apt install git
   git clone https://github.com/billw2/rpi-clone.git
  # copy clone file to local 
   cd rpi-clone
   sudo cp rpi-clone rpi-clone-setup /usr/local/sbin 
  # list of Disk 
    lsblk
  # Copy Disk 
    sudo rpi-clone sda





   # Disk Backup And Restore 
    https://www.makeuseof.com/tag/easily-clone-restore-linux-disk-image-dd/

      When you're ready to copy, type the command below. Note, it will erase any pre-existing data on the second drive, so make sure to back up any data beforehand.

      dd if=/dev/sdX of=/dev/sdY

      Now, let's make sense of what's going on. dd is the command. if is the input, as in the location you want to copy. of is the output or the location you're replacing with your copy.

      sdX and sdY refer to the drives you are interacting with. Drives are often given a name such as /dev/sda, /dev/sdb, or /dev/sdc. You can find out the names using a partition editor. Or, since you're already in the terminal, you can use the lsblk command.

      Creating a Disk Image
      Another way to clone a drive is to create a disk image that you can move around and restore as you would do with a bootable USB.

      Creating image files allows you to save multiple backups to a single destination, such as a large portable hard drive. Again, this process only requires one command:

      dd if=/dev/sdX of=path/to/your-backup.img
      To save space, you can have dd compress your backup.

      dd if=/dev/sdX | gzip -c > path/to/your-backup.img.gz
      This command shrinks your backup into an IMG.GZ file, one of the many compression formats Linux can handle.

      Restoring a Drive With dd
      What good are the backups if you can't use them? When you're ready to restore an image with dd, you have two options. If you used the first approach, simply swap the two destinations.

      dd if=/dev/sdY of=/dev/sdX
      When restoring from an image file, the same concept applies:

      dd if=path/to/your-backup.img of=/dev/sdX
      If your image file is compressed, then things get a little different. Use this command instead:

      gunzip -c /path/to/your-backup.img.gz | dd of=/dev/sdX
      To be clear, gunzip is "g unzip," as in the opposite of "g zip." This command decompresses your backup. Then dd replaces the existing drive with this image.

      Parameters to Consider
      You can alter your command by sticking a parameter at the end. By default, dd can take a while to transfer data. You can speed up the process by increasing the block size. Do so by adding bs= at the end.

      dd if=/dev/sdX of=/dev/sdY bs=64
      This example increases the default block size from 512 bytes to 64 kilobytes.

      conv=noerror tells dd to continue despite any errors that occur. The default behavior is to stop, resulting in an incomplete file. Keep in mind that ignoring errors isn't always safe. The resulting file may be corrupted.

      conv=sync adds input blocks with zeroes whenever there are any read errors. This way data offsets remain in sync.

      You can combine these last two as conv=noerror,sync if you so desire. There is no space after the comma.

      Getting to Know dd
      In case you're interested, dd's name refers to a statement in IBM's Job Control Language. If you don't understand what's going on there, no sweat. That doesn't make the command any harder to use.

      Need more information to help with dd? The wiki page is pretty thorough. There's also a great write-up on the Arch Linux wiki. Again, it doesn't matter if you're using Arch or not. dd works the same way regardless of your Linux operating system.

      If it turns out dd isn't for you, you're not out of luck. There are other ways to clone a hard drive!

