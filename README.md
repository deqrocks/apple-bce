# apple-bce

Buffer Copy Engine fork for Intel Macs with a T2 chip with stateful and no-state resume support.

## Required kernel parameters

These kernel parameters have to be set in Linux commandline:

- `mem_sleep_default=deep` This is S3. S2 and 4 should also work
- `pcie_ports=auto` as override for hardcoded arguments (if exist)


## Notes for dGPU models

On dGPU Macs, suspend may still fail or resume may take very long unless the iGPU is set as the default GPU.

- Follow the iGPU setup from `https://wiki.t2linux.org/guides/hybrid-graphics/#enabling-the-igpu`
- On Fedora, rebuild both grub and initramfs after changing kernel parameters or module config
- If resume still hangs, try `modprobe.blacklist=amdgpu`
- Blacklisting `amdgpu` can make suspend work, but you will lose normal dGPU use and external monitor support
- `apple-gmux` can be used to force the iGPU as default:

```bash
echo "options apple-gmux force_igd=y" | sudo tee /etc/modprobe.d/apple-gmux.conf
```

Switch back to the dGPU default by changing `y` to `n` and rebooting.

## Tested Macs

- `MacBookAir8,1`
- `MacBookAir9,1`
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
sudo reboot
```

Rebuild grub if your distro uses grub.

Rebuild initramfs if your distro includes these modules there.

Example for Fedora / dracut-based distros:

```bash
sudo dracut -f
```

Don't forget to build and install the other two repos mentioned above.

## Support

If this work helps you and you want to support it:

https://www.paypal.com/paypalme/negmaster

## Credits

- MCMrArm https://github.com/MCMrARM
- Antoine Sidem https://github.com/clanoftheducks
