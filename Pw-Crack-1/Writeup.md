# PW Crack 1

### PW Crack 1

| 100 points

Tags: **Category: General Skillspassword_cracking**

AUTHOR: LT 'SYREAL' JONES

### Description

Can you crack the password to get the flag?Download the password checker [here](https://artifacts.picoctf.net/c/57/level1.py) and you'll need the encrypted [flag](https://artifacts.picoctf.net/c/57/level1.flag.txt.enc) in the same directory too.

[here](https://artifacts.picoctf.net/c/57/level1.py)

[flag](https://artifacts.picoctf.net/c/57/level1.flag.txt.enc)

---

# Encrypted Flag

```python
PW&m#CPPP:KTV_:ZZX[D
```

[level1.flag.txt.enc](PW%20Crack%201%20648fc276c77540f4bda4491f510a5595/level1.flag.txt.enc)

# PW Checker

```python
### THIS FUNCTION WILL NOT HELP YOU FIND THE FLAG --LT ########################
def str_xor(secret, key):
    #extend key to secret length
    new_key = key
    i = 0
    while len(new_key) < len(secret):
        new_key = new_key + key[i]
        i = (i + 1) % len(key)        
    return "".join([chr(ord(secret_c) ^ ord(new_key_c)) for (secret_c,new_key_c) in zip(secret,new_key)])
###############################################################################

flag_enc = open('level1.flag.txt.enc', 'rb').read()

def level_1_pw_check():
    user_pw = input("Please enter correct password for flag: ")
    if( user_pw == "e9e8"):
        print("Welcome back... your flag, user:")
        decryption = str_xor(flag_enc.decode(), user_pw)
        print(decryption)
        return
    print("That password is incorrect")

level_1_pw_check()
```

In line 19 we can find a if statement 

```python
if( user_pw == "e9e8"):
```

By Entering it as the flag we can obtain the flag easily

```bash
$ python3 level1.py 
Please enter correct password for flag: e9e8
Welcome back... your flag, user:
picoCTF{545h_r1ng1ng_ccbfafcb}
```

# FLAG

```bash
picoCTF{545h_r1ng1ng_ccbfafcb}
```
