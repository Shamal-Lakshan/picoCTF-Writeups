# Scavenger Hunt

### Scavenger Hunt

| 50 points

Tags: **Category: Web Exploitation**

AUTHOR: MADSTACKS

### Description

There is some interesting information hidden around this site [http://mercury.picoctf.net:39698/](http://mercury.picoctf.net:39698/). Can you find it?

First, By viewing the page source we can find the first part of the flag

```html
<!doctype html>
<html>
  <head>
    <title>Scavenger Hunt</title>
    <link href="https://fonts.googleapis.com/css?family=Open+Sans|Roboto" rel="stylesheet">
    <link rel="stylesheet" type="text/css" href="mycss.css">
    <script type="application/javascript" src="myjs.js"></script>
  </head>

  <body>
    <div class="container">
      <header>
		<h1>Just some boring HTML</h1>
      </header>

      <button class="tablink" onclick="openTab('tabintro', this, '#222')" id="defaultOpen">How</button>
      <button class="tablink" onclick="openTab('tababout', this, '#222')">What</button>

      <div id="tabintro" class="tabcontent">
		<h3>How</h3>
		<p>How do you like my website?</p>
      </div>

      <div id="tababout" class="tabcontent">
		<h3>What</h3>
		<p>I used these to make this site: <br/>
		  HTML <br/>
		  CSS <br/>
		  JS (JavaScript)
		</p>
	<!-- Here's the first part of the flag: picoCTF{t -->
      </div>

    </div>

  </body>
</html>

```

### First Part Of The Flag

```html
picoCTF{t
```

Part 2 of the flag can be found in the Inspector —> Sources —> mycss.css

```css
div.container {
    width: 100%;
}

header {
    background-color: black;
    padding: 1em;
    color: white;
    clear: left;
    text-align: center;
}

body {
    font-family: Roboto;
}

h1 {
    color: white;
}

p {
    font-family: "Open Sans";
}

.tablink {
    background-color: #555;
    color: white;
    float: left;
    border: none;
    outline: none;
    cursor: pointer;
    padding: 14px 16px;
    font-size: 17px;
    width: 50%;
}

.tablink:hover {
    background-color: #777;
}

.tabcontent {
    color: #111;
    display: none;
    padding: 50px;
    text-align: center;
}

#tabintro { background-color: #ccc; }
#tababout { background-color: #ccc; }

/* CSS makes the page look nice, and yes, it also has part of the flag. Here's part 2: h4ts_4_l0 */
```

### Flag

```css
h4ts_4_l0
```

# Finding the next flag

By running a dirsearch scan on the webite we can find osme hidden directories

[GitHub - maurosoria/dirsearch: Web path scanner](https://github.com/maurosoria/dirsearch)

```bash
python3 dirsearch.py -u http://mercury.picoctf.net:39698/ -e*
```

![dirsearch.png](Scavenger%20Hunt%20c89a095cb2b345e89362a3b1330cc0c5/dirsearch.png)

```bash
larnzlort@larnzlort-MS-7994:~/Downloads/PICO-ctf/Scavenger-hunt/dirsearch$ python3 dirsearch.py -u http://mercury.picoctf.net:39698/ -e*

  _|. _ _  _  _  _ _|_    v0.4.2.1
 (_||| _) (/_(_|| (_| )

Extensions: php, jsp, asp, aspx, do, action, cgi, html, htm, js, json, tar.gz, bak | HTTP method: GET
Threads: 25 | Wordlist size: 15365

Output File: /home/larnzlort/Downloads/PICO-ctf/Scavenger-hunt/dirsearch/reports/mercury.picoctf.net-39698/-_22-02-06_09-29-06.txt

Log File: /home/larnzlort/Downloads/PICO-ctf/Scavenger-hunt/dirsearch/logs/last_scan.log

Target: http://mercury.picoctf.net:39698/

[09:29:06] Starting: 
[09:29:18] 403 -    9B  - /.%2e/%2e%2e/%2e%2e/%2e%2e/etc/passwd
[09:29:18] 200 -   62B  - /.DS_Store
[09:29:30] 200 -   95B  - /.htaccess
[09:29:30] 200 -   95B  - /.htaccess/
[09:33:07] 200 -  961B  - /index.html
[09:34:25] 200 -  124B  - /robots.txt

Task Completed
larnzlort@larnzlort-MS-7994:~/Downloads/PICO-ctf/Scavenger-hunt/dirsearch$
```

```bash
curl http://mercury.picoctf.net:39698/robots.txt

User-agent: *
Disallow: /index.html
# Part 3: t_0f_pl4c
# I think this is an apache server... can you Access the next flag?
```

### 3rd part of the flag

```bash
t_0f_pl4c
```

# Finding the 4th part

```bash
curl http://mercury.picoctf.net:39698/.htaccess

# Part 4: 3s_2_lO0k
# I love making websites on my Mac, I can Store a lot of information there
```

### 4th part of the flag

```bash
3s_2_lO0k
```

# Further Explorations ;)

```bash
curl http://mercury.picoctf.net:39698/.DS_Store

Congrats! You completed the scavenger hunt. Part 5: _fa04427c}
```

### 5th/Final part of the flag

```bash
_fa04427c}
```

# Wraping it all up

```bash
picoCTF{th4ts_4_l0t_0f_pl4c3s_2_lO0k_fa04427c}
```
