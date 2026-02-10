# Learning-and-troubleshooting

#1 connection to the legserv with visual code 

## Issue 1: The code for the connection is hard to put in place :

after I have downlaod the ressource pack I try to join the serveur with that code on the wiki :

First step I need to look if the legcompute alone is enought to connect. 

```BASH

alexis@legcompute3.unine.ch

```
I need the Password but it doesn't work ... I use 2 the first one is what i use to connect to the legcompute with Thomas (bioinfo25) and the second one what i receved by email(LEGcompute_76491).

I need to find that passeword, on the mail with the passeword I can change the password so I will and it connect with bioinfo25 i need to change it anyway -> Agostinibear12

I'm trying again the legcompute connection: it works !!!

I will use the code given on the wiki :

```Bash

# Mac/Linux
nano ~/.ssh/config

# Add this configuration:
Host *
    UseKeychain yes                    # Mac only
    AddKeysToAgent yes

Host legmagic
    HostName 139.162.173.39
    Port 22
    User alexis
    ForwardAgent yes

Host legcompute-remote
    HostName localhost
    Port 2223
    User alexis
    ProxyJump legmagic
    ForwardAgent yes

Host legcompute
    HostName legcompute3.unine.ch
    User alexis

```
  
I notice that the main way to access is the last one because i don't need legmagic:

```Bash

Host legcompute
    HostName legcompute3.unine.ch
    User alexis

```
Wirdly it doesn't work when i use this pack... 

When i'm looking the output 2 mains errors are present : 

the first one :

```R

bash: line 1: powershell: command not found
...
Failed to parse remote port from server output
Resolver error

```
