
- ### Link to article: [Link](https://www.siberoloji.com/how-to-build-a-custom-debian-iso-image-on-debian-12-bookworm/)


- ### Install needed packages

	```
	sudo apt install live-build debootstrap squashfs-tools xorriso isolinux syslinux-utils wget
	```
	
- ### Create work directory

	```
	  mkdir ~/debian-custom-iso
	  cd ~/debian-custom-iso
	```


- ### Configure build

	```
	lb config \
	  --distribution trixie \
	  --binary-images iso-hybrid \
	  --archive-areas "main contrib non-free non-free-firmware" \
	  --debian-installer live
	```
	
- ### Configure custom package

	```
	$EDITOR custom.list.chroot
	cp custom.list.chroot config/package-lists/custom.list.chroot
	```

- ### Make other customizations


- ### Start building
	
	```
	sudo lb build
	```

- ### Create bootable USB
	```
	sudo dd if=live-image-amd64.hybrid.iso of=/dev/sdX bs=4M status=progress && sync
	```  	
	
- ### Clean build (optional)

	```
	sudo lb clean
	```