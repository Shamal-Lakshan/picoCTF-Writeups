# PW Crack 2

### PW Crack 2

| 100 points

Tags: **Category: General Skillspassword_cracking**

AUTHOR: LT 'SYREAL' JONES

### Description

Can you crack the password to get the flag?Download the password checker [here](https://artifacts.picoctf.net/c/22/level2.py) and you'll need the encrypted [flag](https://artifacts.picoctf.net/c/22/level2.flag.txt.enc) in the same directory too.

[here](https://artifacts.picoctf.net/c/22/level2.py)

[flag](https://artifacts.picoctf.net/c/22/level2.flag.txt.enc)

---

# Encrypted Flag

[https://www.notion.so](https://www.notion.so)

# Checker

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

flag_enc = open('level2.flag.txt.enc', 'rb').read()

def level_2_pw_check():
    user_pw = input("Please enter correct password for flag: ")
    if( user_pw == chr(0x63) + chr(0x30) + chr(0x30) + chr(0x30) ):
        print("Welcome back... your flag, user:")
        decryption = str_xor(flag_enc.decode(), user_pw)
        print(decryption)
        return
    print("That password is incorrect")

level_2_pw_check()
```

We can find a if statement in line 18

But its with some HEX Characters

we can simply decrypt them using python console

The Result of the decode is 

```python
Python 3.8.10 (default, Nov 26 2021, 20:14:08) 
[GCC 9.3.0] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> chr(0x63) + chr(0x30) + chr(0x30) + chr(0x30)
'c000'
>>>
```

```python
c000
```

Now we can simply submit this and get the flag 

```python
$ python3 level2.py 
Please enter correct password for flag: c000
Welcome back... your flag, user:
picoCTF{tr45h_51ng1ng_a3e28409}
```

# Flag

```python
picoCTF{tr45h_51ng1ng_a3e28409}
```
