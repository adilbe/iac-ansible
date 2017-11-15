# Description
This ansible project template is an ansible quick start. It's guide you over some guidelines to reach one goal, 
the **Idempotence** 

# Project Tree
Please, notice that:
 - Folders with underscore as prefix are only templates, feel free to choose a suited name
 - Ansible come with a defined tree folder
 
- ansible-project-template
    - inventories   : client inventories
    - roles         : Independent ansible roles 
    - playbook.yml  : A collection of ansible tasks / roles executed on set of ansible groups

# Guidelines
## Idempotence
Idempotence means that, with the same inputs:
- Client variables
- Same playbook
- Operational VMs, 

The play book must achieve the targeted results

## Use handlers
When configuring service, to achieve best performance, avoid restarting services even if the configurantion is not changed. 
An example is given sith the ssh-server ansible role. 

## Only one
One playbook for all clients
One role for all clients

# Prepare your environement
## SSH
### SSH Key Generation
To create your ssh key pair, do as bellow :
```bash

$ ssh-keygen

Generating public/private rsa key pair.
Enter file in which to save the key (/Users/Adil/.ssh/id_rsa): /Users/Adil/.ssh/mapr
Enter passphrase (empty for no passphrase):
Enter same passphrase again:
Your identification has been saved in /Users/Adil/.ssh/mapr
Your public key has been saved in /Users/Adil/.ssh/mapr.pub
The key fingerprint is:
SHA256:jBlLcjavv6tOJXe0ZsFlVWLJTIB9YJPpaZZdDWrhQig Adil@MBP-de-Adil
The key's randomart image is:
+---[RSA 2048]----+
|         ..oOX*+o|
|      E .o.=+==.o|
|    . *.  =.+= . |
|     = O . =* .  |
|      = S =o     |
|       = +       |
|      o          |
|     . .         |
|     .o.+o       |
+----[SHA256]-----+
```

#### Tips
For more readiness, it's a good practice to change default identity in your public key with your email address

```bash
$ cat mapr.pub

ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQXXXXXXXXXX ${your_email.address}@domain.fr

```

### SSH Key Deployement
Deploy your .pub key into the authorized file in the target user in target machine,
```bash
cat ${USER_HOME}/.ssh/authrized_keys
```

### SSH Agent
```bash
to complete
```



# Run a playbook

```bash
ansible-playbook -i inventories/$tenant_name/hosts.ini playbook.yml  --ask-vault-pass
```



