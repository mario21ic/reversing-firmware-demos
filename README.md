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

## Example 2
```
wget https://www.downloads.netgear.com/files/GDC/JWNR2010V3/JWNR2000v3_JWNR2010v3_JWNR2000Tv3-v1.0.0.32.zip
unzip JWNR2000v3_JWNR2010v3_JWNR2000Tv3-v1.0.0.32.zip
binwalk JWNR2000v3_JWNR2010v3_JWNR2000Tv3-v1.0.0.32.img
dd if=JWNR2000v3_JWNR2010v3_JWNR2000Tv3-v1.0.0.32.img skip=950272 of=linux bs=1
file linux
unsquashfs linux
sudo unsquashfs -f linux
ll squashfs-root/
find .|less
binwalk JWNR2000v3_JWNR2010v3_JWNR2000Tv3-v1.0.0.32.img
echo $((950272-128))
dd if=JWNR2000v3_JWNR2010v3_JWNR2000Tv3-v1.0.0.32.img skip=128 of=linux2.lzma bs=1 count=950144
linux2.lzma
lzma -d < linux2.lzma > something
binwalk something
```

Based on 
* https://www.youtube.com/watch?v=GIU4yJn2-2A
* https://stackoverflow.com/questions/36778409/binwalk-compressed-data-is-corrupt
* https://www.youtube.com/watch?v=oqk3cU7ekag

Files were downloaded from http://support.dlink.com.au/download/download.aspx?product=DCS-932L

