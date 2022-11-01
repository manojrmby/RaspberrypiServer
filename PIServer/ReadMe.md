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
    