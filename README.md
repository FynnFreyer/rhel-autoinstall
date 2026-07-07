# rhel-autoinstall

Build a USB that automatically installs a preconfigured RHEL system from a pen drive.

```bash
# TODO: change these vars according to your needs
src_iso=isos/Rocky-10.2-x86_64-minimal.iso
dest_iso=out/rocky-10.2-ptenets.iso
dest_device=/dev/sdX

# create the ISO and write it to $dest_device
sudo mkksiso --ks ptenets-ks.cfg "$src_iso" "$dest_iso" \
  && sudo dd if="$dest_iso" of="$dest_device" bs=4M status=progress \
  && sudo sync
```
