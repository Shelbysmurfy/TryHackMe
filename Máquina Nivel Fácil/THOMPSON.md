# RESOLUCIÓN DE LA MÁQUINA THOMPSON

Abrimos la máquina y vemos su IP.

![image](https://github.com/user-attachments/assets/6e0dc32e-5c04-475c-9b3a-24d5979ba430)

Hacemos un nmap para poder ver los puertos que estan abiertos para la IP seleccionada, para ver servicios, versiones...

![image](https://github.com/user-attachments/assets/85da43d1-7a02-447b-ab63-583d59181b5d)

Hacemos fuerza bruta con gobuster.

![image](https://github.com/user-attachments/assets/308ab698-0a92-4216-bb0f-c6757e39571f)

Si introducimos el directorio /manager vemos un login desplegable.

![image](https://github.com/user-attachments/assets/fae94295-bede-43ec-b44f-027ca7216233)

Como no sabemos las credenciales le damos a "cancel", y al darle nos muestra esto: 

![image](https://github.com/user-attachments/assets/5ef59e55-6d19-49bc-93ec-42d1ecc2737d)

Introducimos las credenciales que nos muestra "tomcat:s3cret" y ganamos acceso.

![image](https://github.com/user-attachments/assets/e0b15088-c6b4-4794-a995-778a583e1428)

Vemos una subida de archivos.war, así que vamos a crear un archivo malicioso.war con msfvenom.

![image](https://github.com/user-attachments/assets/3ece9227-2c71-4599-82eb-23c3d5d93d85)

Lo subimos.

![image](https://github.com/user-attachments/assets/fd4271c5-8119-46d4-aa06-813200393c31)

Y si lo abrimos mientras estamos en escucha con netcat ganamos acceso correctamente.

![image](https://github.com/user-attachments/assets/321c8ecd-fc78-4749-95d3-a981025cae00)

Nos vamos al directorio /home/jack y encontramos la primera flag, la del user.

![image](https://github.com/user-attachments/assets/5e32c6b9-7c3b-466e-b17f-4360cd98cba0)

![image](https://github.com/user-attachments/assets/43103f0a-2885-48e6-a4d9-9c59b2d18cda)

En el encontramos dos archivos, uno de ellos podemos editarlo, y al parecer lo que se introduce en este se muestra en el otro archivo que tiene permisos root.

Así que vamos a ejecutar en el archivo que podemos editar "cat /root/root.txt", y si todo va bien veremos en el otro archivo el resultado de este comando.

Y efectivamente conseguimos la segunda flag, la del root.

![image](https://github.com/user-attachments/assets/fb2364a6-2866-4573-ade6-39ba1f30bcdc)

![image](https://github.com/user-attachments/assets/724a92d1-8690-4965-9e03-ea79e6259aa6)

