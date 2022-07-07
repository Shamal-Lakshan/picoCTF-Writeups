# login

### login

| 100 points

Tags: **Category: Web Exploitation**

AUTHOR: BROWNIEINMOTION

### Description

My dog-sitter's brother made this website but I can't get in; can you help?[login.mars.picoctf.net](https://login.mars.picoctf.net/)

In order to find the flag we should go to the inspector —> Network and scan for requests(Supply some dummy text) then 3 requets will appear (logn.mars.picoctf.net && index.js && config.json)

In the index.js file we can find a string which looks like base 64 

```jsx
(async()=>{
    await new Promise((e=>window.addEventListener("load", e))),
    document.querySelector("form").addEventListener("submit", (e=>{
        e.preventDefault();
        const r = {
            u: "input[name=username]",
            p: "input[name=password]"
        }
          , t = {};
        for (const e in r)
            t[e] = btoa(document.querySelector(r[e]).value).replace(/=/g, "");
        return "YWRtaW4" !== t.u ? alert("Incorrect Username") : "cGljb0NURns1M3J2M3JfNTNydjNyXzUzcnYzcl81M3J2M3JfNTNydjNyfQ" !== t.p ? alert("Incorrect Password") : void alert(`Correct Password! Your flag is ${atob(t.p)}.`)
    }
    ))
}
)();
```

 

```jsx
"cGljb0NURns1M3J2M3JfNTNydjNyXzUzcnYzcl81M3J2M3JfNTNydjNyfQ"

"--------Maybe Base64-------"
```

After decoding the string we can find the flag. 

```jsx
picoCTF{53rv3r_53rv3r_53rv3r_53rv3r_53rv3r}
```
