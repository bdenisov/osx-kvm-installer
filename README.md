# osx-kvm-installer

## OSX-KVM

```
cd ~
git clone --depth 1 --recursive https://github.com/kholia/OSX-KVM.git
cd OSX-KVM/
./fetch-macOS-v2.py
sudo apt-get install dmg2img qemu-utils qemu-system-x86
dmg2img -i BaseSystem.dmg BaseSystem.img
qemu-img create -f qcow2 mac_hdd_ng.img 20G

# сеть 
sudo apt-get install uml-utilities virt-manager bridge-utils

sudo ip tuntap add dev tap0 mode tap
sudo ip link set tap0 up promisc on
sudo brctl addif virbr0 tap0

sudo ip link set dev virbr0 up
sudo ip link set dev tap0 master virbr0

./OpenCore-Boot.sh
```


## Install brew

```
curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh
/bin/bash -c ./install.sh
```


## Install usbfluxd

```
sudo brew install 
	build-essential \
	checkinstall \
	git \
	autoconf \
	automake \
	libtool-bin
sudo brew install python3-dev
cd ~
git clone https://github.com/libimobiledevice/libplist.git
cd ~/libplist

./autogen.sh
make
sudo make install


sudo brew install make automake autoconf libtool pkg-config gcc libimobiledevice usbmuxd

cd ~
git clone https://github.com/corellium/usbfluxd.git
cd ~/usbfluxd

./autogen.sh
make
sudo make install

cd ~/usbfluxd/usbfluxd/
sudo cp usbfluxd /usr/local/sbin/
export PATH=/usr/local/sbin:${PATH}
```

