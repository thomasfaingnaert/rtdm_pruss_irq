# Building
```bash
sudo apt-get install linux-headers-$(uname -r)
git clone https://github.com/thomasfaingnaert/rtdm_pruss_irq
make
sudo make install
sudo modprobe rtdm_pruss_irq
lsmod | grep rtdm
```
