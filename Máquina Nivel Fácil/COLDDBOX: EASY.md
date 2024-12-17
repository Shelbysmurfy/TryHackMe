# RESOLUICIÓN DE LA MÁQUINA COLDDBOX: EASY

## TASK 1 - BOOT2ROOT

Vamos al directorio /hidden, que lo encontramos gracias a hacer fuerza bruta con gobuster.

![image](https://github.com/user-attachments/assets/2c0a094e-161f-4eb2-bd18-78df67fc3b1f)

Encontramos tres usuarios válidos, vamos a crear un archivo con ellos, y vamos a hacer un wpscan, con el rockyu.

![image](https://github.com/user-attachments/assets/4953b62d-8d83-4722-9b7b-98ab08cd4374)

Entramos en el wordpress con las credenciales obtenidas.

![image](https://github.com/user-attachments/assets/ecd752f8-b0ee-4137-b40f-782f0b477943)

Añadimos código malicioso en un archivo .php, dentro de el apartado appearance / themes 

![image](https://github.com/user-attachments/assets/e86b1c0f-c6bb-42a5-8b02-86c4b5227c23)

Hacemos una reverse shell para ganar acceso a la máquina víctima.

![image](https://github.com/user-attachments/assets/306a6479-8082-4b3a-9ced-589ae6d5a11d)

Vemos los permisos SUID y encontramos el binario find, gracias a el ganamos acceso como root.

![image](https://github.com/user-attachments/assets/4d527cb6-b7da-41bd-9234-fe810b95e6f9)

### USER.TXT

![image](https://github.com/user-attachments/assets/5c966a16-d1f0-464d-83b7-7ff014952b8e)

![image](https://github.com/user-attachments/assets/5c922766-a95b-4513-a06f-ce889db60c85)

### ROOT.TXT

![image](https://github.com/user-attachments/assets/c0159e1e-30c6-4c1d-8aec-9e3d8978fcca)

![image](https://github.com/user-attachments/assets/9e031161-1275-47cf-bac7-304467976073)
