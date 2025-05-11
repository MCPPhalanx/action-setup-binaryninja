This directory contains Linux executables for Binary Ninja.

Archives are created by running the following command:

```bash
read BN_PASSWORD
7za a -snl -mhe=on -p"$BN_PASSWORD" binaryninja.7z binaryninja/ license.dat
```
