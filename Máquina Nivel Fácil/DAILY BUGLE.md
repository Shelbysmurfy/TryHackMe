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

![image](https://github.com/user-attachments/assets/72636187-db46-4e27-b602-afaa991c6823)

Nos vamos al apartado de templates, luego entramos en protostar y creamos un archivo.php nuevo donde introducimos el pentest monkey.

![image](https://github.com/user-attachments/assets/36c29dc3-9b6e-4ee6-b209-c7fc83e22d86)

Seguidamente vamos a la ruta de este mientras estamos en escucha con netcat, y ganamos acceso correctamente.

![image](https://github.com/user-attachments/assets/b28a9a90-09d2-4e26-a4bf-abf70bcc1e24)

![image](https://github.com/user-attachments/assets/932de372-fc33-48d9-8ad3-330ec71dadfb)

Vamos a /var/www/html, tenemos un archivo "configuration.php", que si lo habrimos vemos unas credenciales "root:nv5uz9r3ZEDzVjNu".

![image](https://github.com/user-attachments/assets/3a3f77f8-b779-4a5a-8b68-13ee3d245e12)

Nos intentamos conectar como usuario jjameson, ya que es el único que tenemos en la máquina víctima, con la contraseña obtenida y ganamos acceso.

![image](https://github.com/user-attachments/assets/7b6fe670-1daf-4432-b97b-6751a3946b68)

Hacemos ls y vemos la primera flag, la del user.

![image](https://github.com/user-attachments/assets/54bc84f6-f5e8-4f74-99c9-395f9f92398d)

![image](https://github.com/user-attachments/assets/0fe69e13-a793-4301-8d84-84b249a1d418)

Hacemos sudo -l y vemos esto: 

![image](https://github.com/user-attachments/assets/0dec3ae9-053d-44c4-b82f-0d2709af938c)

Vamos al GTFObins y haremos los que nos indica.

![image](https://github.com/user-attachments/assets/b6471ef6-6d61-4630-a322-b399654f4430)

Vamos a escalar privilegios a root con la parte "b".

![image](https://github.com/user-attachments/assets/6b0a5e1e-831f-4d25-b2cf-e6dc994c5b40)

Y encontramos la segunda flag, la del usuario root.

![image](https://github.com/user-attachments/assets/4d377ac0-c5ef-410b-9d6a-2bf6b6728ed7)

![image](https://github.com/user-attachments/assets/64923791-c879-4edf-8b09-e05d2763da21)

