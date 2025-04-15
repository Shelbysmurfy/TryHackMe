# RESOLUCIÓN DE LA MÁQUINA DAILY BUGLE

Abrimos la máquina y vemos su IP.

![image](https://github.com/user-attachments/assets/895258e1-c5f2-4f9e-b62c-3df56fb39c9c)

Hacemos un nmap para poder ver los puertos que estan abiertos para la IP seleccionada, para ver servicios, versiones...

![image](https://github.com/user-attachments/assets/7340ec53-adc7-43a1-aadb-140617bc122e)

## TASK 1

![image](https://github.com/user-attachments/assets/9ae140e3-6871-4fea-b33e-897a29b705eb)

![image](https://github.com/user-attachments/assets/8378a8e5-d690-4d9c-9f5c-eee36d1ee75d)

## TASK 2

Hacemos fuerza bruta con dirsearch.

![image](https://github.com/user-attachments/assets/2c07f642-2423-47e2-9aaa-89a5801f5773)
![image](https://github.com/user-attachments/assets/587a2f0a-8395-4cb0-a57f-275cb45b56f1)

En el archivo "README.txt", encontramos la versión de Joomla.

![image](https://github.com/user-attachments/assets/84a22c1e-846a-48fe-879d-687fd4ea3b67)

![image](https://github.com/user-attachments/assets/792b4b53-a36b-4b46-b9c9-33909a956140)

Buscamos posibles exploits para esta versión y encontramos esto: 

![image](https://github.com/user-attachments/assets/f3dae326-2926-43bf-a45d-26aaebac38d5)

Buscamos un github para el CVE que tenemos "2017-8917", y ejecutamos este en nuestra máquina.

Github: https://github.com/stefanlucas/Exploit-Joomla

![image](https://github.com/user-attachments/assets/461f2540-63f3-4ebe-988f-37963fed0d16)

Obtenemos unas credenciales, entre ellas un hash. Así que vamos a utilizar la herramienta "John the Ripper" para crackearlo.

![image](https://github.com/user-attachments/assets/fa78b20e-bd31-4fcb-aa67-8b0e3de321ea)

Nos conectamos al servicio de joomla con las credenciales obtenidas "jonah:spiderman123".



