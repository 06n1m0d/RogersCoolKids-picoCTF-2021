# Play Nice 

We start by putting `nc mercury.picoctf.net 19860` into the webshell.

We then get 2 things:
- Here is the alphabet: `lsi28c14ot0vbf7nagh3mpjuxy5kwz6edqr9`
- Here is the encrypted message: `1x5hqlod8x7oa88h0de1b5r6xja5sd`

Looking at the alphabet and encrypted, we can obviously tell this is a cipher. Puzzled, we look at the file `playfair.py`.

Like in many challenges, the names of files and challenges are a clue to what the answer could be. A quick google search shows nothing for Play Nice Cipher Decoder however, when we google Play Fair Cipher Decoder we find some interesting results. On this [website](https://www.dcode.fr/playfair-cipher), we see that we can enter the alphabet and find the flag! 

![image1](https://user-images.githubusercontent.com/71709994/113524961-c4c7b000-9577-11eb-843f-c4a67e219f66.png)

Above is where we enter the text that we want to decode which is `1x5hqlod8x7oa88h0de1b5r6xja5sd`

Now, we need to add the alphabet here:

![image3](https://user-images.githubusercontent.com/71709994/113525067-6d760f80-9578-11eb-82fe-c0053338275d.png)

And then, we simply press the decode button and we get:

![image1](https://user-images.githubusercontent.com/71709994/113525102-a9a97000-9578-11eb-84ea-a785fd8e92f7.png)

Now, we need to make this into lowercase and submit it as a flag and we are done.

> picoCTF{}
