# Logon

### logon

| 100 points

Tags: **Category: Web Exploitation**

AUTHOR: BOBSON

### Description

The factory is hiding things from all of its users. Can you login as Joe and find what they've been looking at? `https://jupiter.challenges.picoctf.org/problem/15796/` ([link](https://jupiter.challenges.picoctf.org/problem/15796/)) or http://jupiter.challenges.picoctf.org:15796

## Checking the web

The web has a simple login form.

we can input two texts to the username and password fields to check the cookies.

ex-

Username - username

Password - password

After entering the above values we can see a message 

> Success: You logged in! Not sure you'll be able to see the flag though.
> 

![logon-after-creds.png](Logon%2073e462a91ef341549eff215963f4cf97/logon-after-creds.png)

## Checking the cookies

Now lets check the cookies using the inspector,

We can see that there are 3 cookies

- admin
- username
- password

![logon-cookies.png](Logon%2073e462a91ef341549eff215963f4cf97/logon-cookies.png)

By changing the value of the **admin** cookie to **True**, and refreshing the page we can obtain the flag.

![logon-flag.png](Logon%2073e462a91ef341549eff215963f4cf97/logon-flag.png)

# Flag

```bash
picoCTF{th3_c0nsp1r4cy_l1v3s_6edb3f5f}
```
