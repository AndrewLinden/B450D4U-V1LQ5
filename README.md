# ASRock Rack B450D4U-V1LQ5
## Modded bios
Instant Flash will not work with modded bios. Flashing with CH341 works. Note that the bios chip is socketed.
### Version m2
- Unsuppressed "Platform First Error Handling"
### Version m1
- Unsuppressed "UMC Common Options" menu for ECC mode activation

## Notes about B450D4U-V1LQ5
### CPU support
With 2.xx BIOS fully supported CPUs seem to be Matisse and Vermeer.

Pinnacle Ridge, Cezanne and probably Renoir will boot but have these known problems:
- back USB ports won't work. No solution found yet, workaround to use onboard USB3 header.
- Onboard VGA will not initialize pre-os with bios default settings, but system will POST and try to boot. If boot succeeds (with blank screen) the OS can initialize the AST2510 VGA and picture appears on monitor. Solution: add temporarily GPU and set in bios "Video OPROM launch policy" to "UEFI only" OR disable CSM altogether. Note that after these changes in BIOS system might not POST with GPU installed - just remove the GPU, VGA will now work.
- OS will report overcurrent on USB ports. Solution: disable (the not existing) USB ports in bios.

### ECC support
ECC is supposed to be activated by bios automatically when ECC memory is installed. However ECC did not activate with the modules that I used. Also I did not manage to reliably activate ECC by setting bios "ECC Enable" setting to "Enabled" with setup_var.efi

With my modded bios ECC can be activated in bios:

Advanced -> AMD CBS -> UMC Common Options -> DDR4 Common Options -> Common RAS -> ECC Configuration
