## Example 1
```
wget http://files.dlink.com.au/products/DCS-932L/REV_A/Firmware/dcs932l_v1.14.04.bin
file dcs932l_v1.14.04.bin
binwalk dcs932l_v1.14.04.bin
# check last past
binwalk -e dcs932l_v1.14.04.bin

cd _dcs932l_v1.14.04.bin.extracted/
file 50040
binwalk 50040
# check last past

dd if=50040 skip=4038656 bs=1 of=mistery.lzma
unlzma mistery.lzma
file mistery
bindwalk mistery

mkdir cpio
cpio -idm --no-absolute-filename < ../mistery
```

Based on https://www.youtube.com/watch?v=GIU4yJn2-2A https://stackoverflow.com/questions/36778409/binwalk-compressed-data-is-corrupt
File was downloaded from http://support.dlink.com.au/download/download.aspx?product=DCS-932L
