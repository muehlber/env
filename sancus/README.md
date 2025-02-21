# Utils

## Sancus images

- `sancus64.mcs` is the Sancus image with 64 bits of security
  - Node key: `deadbeefcafebabe`
  - Vendor key (if ID is 0x1234 (4660)):  `4078d505d82099ba`
- `sancus128.mcs` is the Sancus image with 128 bits of security
  - Node key: `deadbeefcafebabec0defeeddefec8ed`
  - Vendor key (if ID == 0x1234 (4660)): `0b7bf3ae40880a8be430d0da34fb76f0`
- Commands:
  - Get vendor key: `sancus-crypto --gen-vendor-key <vendor_id_hex> --key <node_key>`
  - Get module key: `sancus-crypto <elf_file> --gen-sm-key <module_name> --key <vendor_key>`

## Reactive application

- `reactive.elf` is the latest Reactive application
  - Led driver with secure I/O. Module key: `c9dc7ac6fb1efced0a2152b75c1276c7`
- `reactive_debug.elf` is the same, but with debug outputs
  - Led driver with secure I/O. Module key: `330f65212b8e85a6272e7dbfb7790626`
- Commands:
  - Load application: `sancus-loader -device <device> <elf_file>`
  - Screen session: `screen <device> <baud_rate>`
    - Baud rate for this application and Sancus image is 57600
  - Check input/output IDs of modules in ELF
    - Check inputs of led_driver: `readelf -s --wide reactive.elf | grep led_driver_io`
    - This is useful for connections with outputs/inputs of modules embedded in the ELF (such as led_driver)
