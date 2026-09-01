# MacBook Neo support

The `neo` branch is the normal read/write `asahi-bless` CLI, based on upstream
0.4.4. It does not introduce read-only/read-write modes or alternate binaries.

MacBook Neo's J700 NVRAM partition contains 29 banks. Upstream commit
`70b16a288cfc6795bc1b145255325f59f000be28` supplies the arbitrary-bank parser
used here. A 29-bank regression test keeps that device ABI covered.

Non-mutating `--list-volumes` and `--get-boot` operations open the NVRAM MTD
read-only. Mutating operations retain upstream's read/write open and normal
erase/program behavior.

The matching T8140 QSPIMC Linux driver and J700 device tree live in the
`nvram-qspi` branch of `aurora-silicon/linux`.
