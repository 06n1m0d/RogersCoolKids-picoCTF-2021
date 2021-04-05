# Disk, disk, sleuth! II

First, Since the file is zipped we unzip it with any tool like 7zip or WinZip to see the image files.
We check the details of the disk image just to see what we find. It returned:

`DOS Partition Table
Offset Sector: 0
Units are in 512-byte sectors`

       Slot      Start        End          Length       Description
`000:  Meta      0000000000   0000000000   0000000001   Primary Table (#0)
001:  -------   0000000000   0000002047   0000002048   Unallocated
002:  000:000   0000002048   0000262143   0000260096   Linux (0x83)`


After inspecting the first two parts, they don’t seem to have anything relating to the flag.
Let’s check partition 002 which starts from 2048. We can get here by doing:

`fls -o 2048 dds2-alpine.flag.img`

This can then show us the contents of the partition and then we can see where to go next.
The results from `fls -o 2048 dds2-alpine.flag.img’ are`:

`d/d 11: lost+found
r/r 12: .dockerenv
d/d 20321:      bin
d/d 4065:       boot
d/d 6097:       dev
d/d 2033:       etc
d/d 26417:      home
d/d 8129:       lib
d/d 14225:      media
d/d 16257:      mnt
d/d 18289:      opt
d/d 16258:      proc
d/d 18290:      root
d/d 16259:      run
d/d 18292:      sbin
d/d 12222:      srv
d/d 16260:      sys
d/d 18369:      tmp
d/d 12223:      usr
d/d 14229:      var
V/V 32513:      $OrphanFiles`

Now, a good place to start would be ‘root’ since it pretty much controls everything, and experiences from past CTFs show that problem writers usually put it there.
Now, to check this we can do:

`fls -o 2048 dds2-alpine.flag.img 18290`

And then we see:

`r/r 18291:`      `down-at-the-bottom.txt`

And now to open this file we can use the icat command which is:

`icat -o 2048 dds2-alpine.flag.img 18291`

And then we get the flag
