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
ls
git add fichier1.py
git commit -m "add test file"
git push
```
Problem! Name and email was needed for commit

solve:(AI help)

```bash
git config --global username alexis
git config --globam user.email alexis.agostini@unine.ch
git add fichier1.py
git commit -m "add test file"
git push origine main
```
commit can also make manualy one the source control

# Modules

 ## What module exist

 ```bash
module overview
module avail
```
what module when I worked on thomas' courses can i find 

```bash
module spider FastQC
module spider Bwa
module spider Bowtie2
module spider SAMtools
```

Apparently FastQC doesn't existe 

## Load a module

```bash
module load SAMtools BCFtools
samtools --version
bcftools --version
module list #vérification
```
modules are load !

## unload a module 
```bash
module unload Samtools
module list
module purge
module list
```

# Slurm 
## Test of queue
```Bash
squeue
showq
```
Sarai has a lot of work in progess!

I will try in at another moment to avoid to take CPU and Ram 

I anyway enderstood the process, slum is a automatic schedule of calcule. 

## Test slurm:
Test if is works

```bash
Nano test_slurm
```

Inscription in the nano :
```bash
#!/bin/bash
#SBATCH -J test_slurm
#SBATCH -p normal.168h
#SBATCH -c 1 
#SBATCH --mem=4G
#SBATCH -o test_slurm_%j.out

echo "Début du job : $(date)"
hostname
sleep 60
echo "Fin du job : $(date)"
```
First try:

```bash
sbatch test_slurm.sh
```
erreur 

```bash
sbatch: error: Batch job submission failed: Invalid account or account/partition combination specified
```

Let try with an account ? 

```bash
sbatch --account=alexis test_slurm.sh
```
Feedback

```bash
sbatch: error: Batch job submission failed: Invalid account or account/partition combination specified
```

Apparently the acount is not that simple...
Let's see the name of others 

```bash
showq
```
the users nickname look like the person name...

I think i need either a permission or an account. 

I will ask to daniel on monday.
