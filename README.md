# apple-bce

Buffer Copy Engine fork for Intel Macs with a T2 chip.

## Required repositories

The suspend fix is a set of three parts. You will need to replace stock apple-bce with this fork. Additionally you will need the following forks:

- `t2-upower`: `https://github.com/deqrocks/t2-upower`
- `t2-kbd-tb`: `https://github.com/deqrocks/t2-kbd-tb`

## Required kernel parameters

These kernel parameters have to be set in Linux commandline:

- `pm_async=off`
- `pcie_ports=auto`

## Tested Macs

- `MacBookAir8,1`
- `MacBookAir9,1`
- `MacBookPro15,1`
- `MacBookPro16,1`
- `MacBookPro16,2`
- `MacBookPro16,4`
- `iMac19,1`
- `Macmini8,1`

## Build

```bash
make
```

## Deploy

```bash
sudo make install
sudo depmod -a
sudo dracut -f # or rebuild initramfs with whatever your distro needs
sudo reboot
```
Don't forget to build and install the other two repos mentioned above.

## Support

If this work helps you and you want to support it:

https://www.paypal.com/paypalme/negmaster

## Credits

- MCMrArm https://github.com/MCMrARM
- Antoine Sidem https://github.com/clanoftheducks
