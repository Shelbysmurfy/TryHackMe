# RESOLUCIÓN DE LA MÁQUINA MR ROBOT CTF 

## TASK 1 - CONNECT TO OUR NETWORK

![image](https://github.com/user-attachments/assets/2313923b-b000-44a9-94a9-496ff1f8a98d)

## TASK 2 - HACK THE MACHINE

###WHAT IS KEY 1?

![image](https://github.com/user-attachments/assets/c80c3a7d-0388-4bb3-81e4-f928a5b6aec8)

![image](https://github.com/user-attachments/assets/d004dca2-6559-411f-9ea5-a2111cf87b1c)

![image](https://github.com/user-attachments/assets/0f1c59cb-1b84-4de9-a5ae-51b91bf1feee)

Ataque de fuerza bruta con burpsuite, con  el diccionario que nos hemos encontrado en el burpsuite, vemos que el usuario Elliot tiene un longitud diferente.

![image](https://github.com/user-attachments/assets/94be16d9-a83a-44a5-9655-a8097c90fdf2)

En el wordpress ahora podemos ver que lo que está mal es la contraseña, pero el usuario es correcto.

![image](https://github.com/user-attachments/assets/effd9c34-4ae6-490a-b934-8083b8859846)

El diccionario que tenemos es demasiado grande, hacemos un sort | uniq para que no se repitan las palabras que hay dentro de el y el tamaño se reduce muchíssimo.

![image](https://github.com/user-attachments/assets/b6cd4873-4fb3-439a-a551-983f95046718)

Ahora con la herramienta wpscan buscamos la contraseña de este usuario.

![image](https://github.com/user-attachments/assets/583d0ade-92c6-4d61-beb0-9529732b16ac)

![image](https://github.com/user-attachments/assets/f0870f8c-eebc-4145-bbda-03801a932e06)

Inyectamos código malicioso en /appearance/editor/404.php

![image](https://github.com/user-attachments/assets/2343f6da-2e1a-4632-96a8-42c3f3b84546)

Hacemos una reverse shell.

![image](https://github.com/user-attachments/assets/d5780cfc-4a60-464c-9564-85a3d6706abb)

En el directorio home nos encontramos con esto: 

![image](https://github.com/user-attachments/assets/0a7471b1-57a1-4523-95e7-48cfd58e2be8)
Máquina Nivel Fácil

Desencriptamos el md5.

![image](https://github.com/user-attachments/assets/117565c1-7d38-4a8f-a21e-50767d6ec366)

Entramos con las credenciales obtenidas.

![image](https://github.com/user-attachments/assets/496e6c92-5a73-477b-a492-a82e167a5106)

### WHAT IS KEY 2?

![image](https://github.com/user-attachments/assets/bcd9292d-d210-42dc-ac8d-c607ee689f71)

![image](https://github.com/user-attachments/assets/9a543ec4-7c14-4b28-8dab-b6ff1136ffe4)

En los permisos SUID vemos el binario nmap, vamos al GTFObins y seguimos lo que nos dice.

![image](https://github.com/user-attachments/assets/f3be5470-5494-46b5-a75e-c49a3a16de6c)

### WHAT IS KEY 3?

![image](https://github.com/user-attachments/assets/5744f279-4e8e-41b3-b746-5c1452304a23)

![image](https://github.com/user-attachments/assets/b43bdc02-7a65-4313-ad3a-9dbb92963ce3)

