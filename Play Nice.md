# Play Nice 

We start by putting ‘nc mercury.picoctf.net 19860’ into the webshell.

We then get 2 things:

Here is the alphabet: 'lsi28c14ot0vbf7nagh3mpjuxy5kwz6edqr9'

Here is the encrypted message: '1x5hqlod8x7oa88h0de1b5r6xja5sd'

Looking at the alphabet and encrypted, we can obviously tell this is a cipher. Puzzled, we look at the file 'playfair.py'.

Like in many challenges, the names of files and challenges are a clue to what the answer could be. A quick google search shows nothing for Play Nice Cipher Decoder however, when we google Play Fair Cipher Decoder we find some interesting results. On this ![website](https://www.dcode.fr/playfair-cipher), we see that we can enter the alphabet and find the flag! 
