# Very Very Hidden

What we can do since this is a .pcap file is that we can use Wireshark. Now after we open the .pcap file in Wireshark we can extract the HTTP Packets to get our images!

![image5](https://user-images.githubusercontent.com/71709994/113639317-7f21ea80-963e-11eb-8194-514da1523223.png)

Then we get two images of ducks:

![evil_duck](https://user-images.githubusercontent.com/71709994/113639687-55b58e80-963f-11eb-9020-8b65343c5414.png)
![duck](https://user-images.githubusercontent.com/71709994/113639691-58b07f00-963f-11eb-8ef1-7c4ac94e50c1.png)

After this we can save the `evil_duck.png` since they are the same file but it seems like there is something hidden in there…

Now, what do we do? Well, we can google, “hidden powershell script in image” since that is the smartest way to find it. And after that we get some results which are tools such as this [one](https://github.com/imurasheen/Extract-PSImage)!
Now, following the instructions on the github page we can extract the script from the file.
After this, we notice this ^ in the script, this means that this is a xor operator. Then, we can xor the first part with the second part to find the flag!

> Flag: 
