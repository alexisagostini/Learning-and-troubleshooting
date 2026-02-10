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

When i'm looking the output an error is present : 

the first one :

```bash

bash: line 1: powershell: command not found
...
Failed to parse remote port from server output
Resolver error

```
Unfortunatly VS code try to use the powershell commande but there is no powershell...

In linux Powershell is mostly absente and it should use shell. Powershell is mostly use for windows environnement, the problem is that i try to connect with Windows... I should try to connect with linux to avoid to use powershell instead of shell 

I try it with linux and it works. I didn't understand that on the wiki there is no windows access connect...

But it works now ! 

Now let's try to connect with the github serveur 

Create an folder "Projets" to my folder on the serveur 

```BASH
pwd
ls
mkdir -p projets
cd projets
pwd
```

Create a git clone to my folder :

```Bash
git clone https://github.com/alexisagostini/Learning-and-troubleshooting.git
cd Learning-and-troubleshooting
```
Add it to the source controle on the ressource pack
- open folder
- select the destination (~home/alexis/projets/Learning-and-troubleshooting)

test to add a folder to the github:

```bash
Echo "print('Hello')" > fichier1.py
```
