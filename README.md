# Install a pre-compiled version
You can install a precompiled version using:
```bash
wget https://github.com/thomasfaingnaert/rtdm_pruss_irq/releases/download/v1.0/rtdm_pruss_irq.ko
sudo cp rtdm_pruss_irq.ko /lib/modules/`uname -r`/extra
sudo depmod -a
sudo modprobe rtdm_pruss_irq
```

To check if the module is loaded, run:
```bash
lsmod | grep rtdm_pruss_irq
```

# Build from source
1. Make sure you are running a Xenomai kernel. You can verify this by executing:
```bash
uname -a
```
This should output something similar to `Linux beaglebone 4.9.88-ti-xenomai-r107 #1 SMP PREEMPT Sat Mar 24 09:29:27 UTC 2018 armv7l GNU/Linux`.

2. Download the latest Xenomai source from https://xenomai.org/downloads/xenomai/stable/latest/, e.g. using:
```bash
wget https://xenomai.org/downloads/xenomai/stable/latest/xenomai-3.0.6.tar.bz2
tar -xvf xenomai-3.0.6.tar.bz2
```

3. Build the Xenomai libraries:
```bash
cd xenomai-3.0.6
./configure -enable-smp
make
sudo make install
```

4. Install the Linux headers for your kernel version:
```bash
sudo apt-get install linux-headers-$(uname -r)
```

5. Install the Beaglebone PRU Package:
```bash
git clone https://github.com/beagleboard/am335x_pru_package
cd am335x_pru_package
make
sudo make install
```

6. Finally, clone and build the kernel module:
```bash
git clone https://github.com/thomasfaingnaert/rtdm_pruss_irq
cd rtdm_pruss_irq
make
sudo make install
sudo modprobe rtdm_pruss_irq
lsmod | grep rtdm_pruss_irq
```
