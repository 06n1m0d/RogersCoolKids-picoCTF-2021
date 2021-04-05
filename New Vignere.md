# New Vignere

Using the code below, we can brute force and find all the possibilities by shifting the letters/numbers and using the letters/numbers which are allowed. We just keep shifting and looking for the correct cipher.

```python

#!/usr/bin/env python
import string
import itertools

LOWERCASE_OFFSET = ord("a")
ALPHABET = string.ascii_lowercase[:16]

def b16_decode(plain):
    dec = ""
    for i in range(0, len(plain), 2):
        c1, c2 = plain[i:i+2]
        c1_idx = '{0:04b}'.format(ALPHABET.index(c1))
        c2_idx = '{0:04b}'.format(ALPHABET.index(c2))
        dec_bin = '{}{}'.format(c1_idx, c2_idx)
        dec_chr = chr(int(dec_bin, 2))
        dec += dec_chr
    return dec

def unshift(c, k):
    t1 = ord(c) + LOWERCASE_OFFSET
    t2 = ord(k) + LOWERCASE_OFFSET
    return ALPHABET[(t1 - t2) % len(ALPHABET)]

def getpossval(c, vals):
    res = []
    for k in ALPHABET:
        #print(k,'->',unshift('d', k))
        for val in vals:
            if unshift(c, k) == val:
                res.append(k)
    return res

flag_enc = 'bgjpchahecjlodcdbobhjlfadpbhgmbeccbdefmacidbbpgioecobpbkjncfafbe'

possible_keys = []
for i, x in enumerate(flag_enc):
    if i % 2 == 0:
        possible_keys.append(getpossval(x, ['d', 'g']))
    else:
        possible_keys.append(getpossval(x, ['a','b','c','d','e','f','g','h','i','j']))

key = []
for i in range(9):
    all_poss = [x for j, x in enumerate(possible_keys) if j % 9 == i]

    k = set()
    for poss in all_poss:
        k = set(poss).union(k)
    for poss in all_poss:
        k = set(poss).intersection(k)
    key.append(k)

def make_key(poss_key, poss_append):
    new_poss = []
    poss_key = list(poss_key)
    poss_append = list(poss_append)
    for poss in poss_append:
        for key in poss_key:
            new_poss.append(key + poss)

    return new_poss

keys = list(key[0])
for k in key[1:]:
    keys = make_key(keys, k)

for key in keys:
    dec = ''
    for i, c in enumerate(flag_enc):
        dec += unshift(c, key[i % len(key)])

    flag = b16_decode(dec)
    print(flag)
```
And after running this we get the flag: 



Now we can just wrap it with picoCTF{} and we are done.
