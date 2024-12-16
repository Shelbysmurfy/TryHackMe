# RESOLUCIÓN DE LA MÁQUINA STARTUP

## TASK 1 - WELCOME TO SPICE HUT!

Abrimos el servicio ftp y vemos que tiene el mismo contenido que el parámetro /files, en el puerto 80.

Subimos un archivo malicioso, para poder hacer una reverse shell.

![image](https://github.com/user-attachments/assets/1d7111e9-852d-4c5f-a0aa-6c68a091786b)

![image](https://github.com/user-attachments/assets/7117402d-a54f-42c4-9e7f-ed12232a0055)

![image](https://github.com/user-attachments/assets/d0049eb0-83f7-47a4-9ec6-0e8bab73fdbf)

### What is the secret spicy soup recipe?

![image](https://github.com/user-attachments/assets/9d1e4d27-98d2-4ff5-aef2-5152d5b7d8a7)

![image](https://github.com/user-attachments/assets/3e6d62ce-f1fd-4c87-9cbc-8f5f2c38ce6e)

Seguidamente nos pasamos el archivo suspicious.pcapng a nuestra máquina, para poder leerlo con wireshark.

![image](https://github.com/user-attachments/assets/8b19ddd7-b570-4069-b3b0-d0a20c693547)

En wireshark encontramos una posible contraseña de un usuario.

![image](https://github.com/user-attachments/assets/deba1ad8-5036-49bd-831f-aea84194d1f1)

Nos conectamos como lennie con las contraseña obtenida anteriormente.

![image](https://github.com/user-attachments/assets/83eb9c24-079d-4e6b-bb41-83d693cde8e0)

### What are the contents of user.txt?

![image](https://github.com/user-attachments/assets/75978267-12d7-4945-9327-0a65c7a16b69)

![image](https://github.com/user-attachments/assets/1a447deb-2d9a-40d7-9286-d413da01da0a)

Hacemos un find para encontrar archivos que tengan como grupo lennie.

![image](https://github.com/user-attachments/assets/2b6c27b2-8f8f-49dd-99a1-b5e16e085570)

![image](https://github.com/user-attachments/assets/aee46af3-9321-4907-bce6-d6eff7cde78f)

Vamos a ver el contenido del archivo que hemos encontrado.

![image](https://github.com/user-attachments/assets/f300949a-2dfc-42db-9c1b-2effee576ffc)

Hacemos una reverse shell y ya somos root.

![image](https://github.com/user-attachments/assets/9384789c-ac3c-49a0-9ad1-9dc79b236d85)

### What are the contents of root.txt?

![image](https://github.com/user-attachments/assets/5c6266c2-154a-4344-89ad-82957efcecb5)

![image](https://github.com/user-attachments/assets/e098ce8c-8fbf-4a58-b6f9-e3ad92b18379)





