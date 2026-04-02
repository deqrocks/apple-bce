# apple-bce

Buffer Copy Engine fork for Intel Macs with a T2 chip.

## Required repositories

- `t2-upower`: `https://github.com/deqrocks/t2-upower`
- `t2-kbd-tb`: `https://github.com/deqrocks/t2-kbd-tb`

## Required kernel parameters

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
```

## Support

If this work helps you and you want to support it:

https://www.paypal.com/paypalme/negmaster

## Credits

- MCMrArm https://github.com/MCMrARM
- Antoine Sidem https://github.com/clanoftheducks
