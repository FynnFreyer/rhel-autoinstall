# rhel-autoinstall

Build a USB that automatically installs a preconfigured RHEL system from a pen drive.

## Steps

1. Download the base ISO file, e.g., from [here](https://rockylinux.org/download).
2. Install the `mkksiso` utility from the `lorax` package.
3. Edit the [`sample-ks.cfg`](sample-ks.cfg) file to your needs.
4. Change the variables in the following code block and execute the commands.

```bash
# TODO: change these vars according to your needs
src_iso=isos/Rocky-10.2-x86_64-minimal.iso
dest_iso=out/rocky-10.2-custom.iso
dest_device=/dev/sdX

# create the ISO and write it to $dest_device
sudo mkksiso --ks ptenets-ks.cfg "$src_iso" "$dest_iso" \
  && sudo dd if="$dest_iso" of="$dest_device" bs=4M status=progress \
  && sudo sync
```
