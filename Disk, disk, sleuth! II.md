# Disk, disk, sleuth! II

First, Since the file is zipped we unzip it with any tool like 7zip or WinZip to see the image files.
We check the details of the disk image just to see what we find. It returned:

![picoctf1](https://user-images.githubusercontent.com/71709994/113600058-1702e280-9605-11eb-906a-6c52749d267e.jpg)

After inspecting the first two parts, they don’t seem to have anything relating to the flag.
Let’s check partition 002 which starts from 2048. We can get here by doing:

`fls -o 2048 dds2-alpine.flag.img`

This can then show us the contents of the partition and then we can see where to go next.
The results from `fls -o 2048 dds2-alpine.flag.img’ are`:

![picoctf2](https://user-images.githubusercontent.com/71709994/113600066-19fdd300-9605-11eb-8201-e04f328033f0.jpg)

Now, a good place to start would be ‘root’ since it pretty much controls everything, and experiences from past CTFs show that problem writers usually put it there.
Now, to check this we can do:

`fls -o 2048 dds2-alpine.flag.img 18290`

And then we see:

`r/r 18291:`      `down-at-the-bottom.txt`

And now to open this file we can use the icat command which is:

`icat -o 2048 dds2-alpine.flag.img 18291`

And then we get the flag.

![picoctf3](https://user-images.githubusercontent.com/71709994/113600071-1bc79680-9605-11eb-80af-014ec33d4426.jpg)

> Flag: picoCTF{f0r3ns1c4t0r_n0v1c3_f5565e7b}
