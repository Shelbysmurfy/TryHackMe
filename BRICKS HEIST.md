# RESOLUCIÓN DE LA MÁQUINA TryHack3M: BRICKS HEIST

Abrimos la máquina y vemos su IP.

![image](https://github.com/user-attachments/assets/56e1cd9a-aa1f-46ca-a49c-80ff8a2263df)
![image](https://github.com/user-attachments/assets/bcb8a310-6b10-4f94-9288-b04fbfa1238c)

Hacemos un nmap para poder ver los puertos que estan abiertos para la IP seleccionada.

![image](https://github.com/user-attachments/assets/b6111f20-7621-4eaa-8819-5c49015eaa29)

Ahora hacemos un escaneo de los puertos que hemos visto que estan abiertos para saber servicios,versiones...

![image](https://github.com/user-attachments/assets/81c6e405-678b-40db-ba9a-6ec8541898f1)

Miramos el robots.txt, y vemos esto: 

![image](https://github.com/user-attachments/assets/6cd20870-482b-42d9-ae1d-eba74fbe7b40)

Tenemos un login de wordpress.

![image](https://github.com/user-attachments/assets/78972238-fcef-4f6b-97d0-e9480b4882b1)

Vamos a hacer un wpscan.

![image](https://github.com/user-attachments/assets/d2d2a3c4-e088-4fcb-8711-c6fae99d98f7)

Vemos una versión de bricks.

![image](https://github.com/user-attachments/assets/2b1ab0b2-2b69-4d0f-9f0a-f321e3a49396)

Buscamos un posibles exploit para este versión de bricks "https://github.com/K3ysTr0K3R/CVE-2024-25600-EXPLOIT"

![image](https://github.com/user-attachments/assets/96d0c257-2e9a-4f65-8254-b5b3aa5514ae)

Nos traemos el exploit que hemos encontrado a nuestra máquina.

![image](https://github.com/user-attachments/assets/7b590e53-675c-44be-913a-b31fcd541e29)

Lo ejecutamos.



