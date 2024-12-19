# RESOLUCIÓN DE LA MÁQUINA CORRIDOR

## TASK 1 - ESCAPE THE CORRIDOR

Abrimos la web.

![image](https://github.com/user-attachments/assets/7129baf2-ddf5-40dd-917b-837b63660c3e)

Vamos al código fuente y vemos esto: 

![image](https://github.com/user-attachments/assets/299af054-c71a-4ee5-90b1-86616777141a)

Todo esto son hashes encriptados en md5, ya que tienen 32 carácteres.

![image](https://github.com/user-attachments/assets/e6d02483-8a73-4811-a3b7-890d5af6650e)

Si los intentamos desencriptar nos devuelven carácteres del 1 al 13.

![image](https://github.com/user-attachments/assets/635cfa6d-b806-4366-b406-3bbae6f1ad30)

Si probamos a encriptar otros números como el 0, que va antes del 1, y que no está aquí nos devuelve esto: 

![image](https://github.com/user-attachments/assets/e187880c-4d72-444b-ac3c-d2f59bdc6912)

Y si ahora introducimos el hash en la url, nos devuelve la flag que buscamos.

![image](https://github.com/user-attachments/assets/7445b2b0-e5ab-4055-96c1-11c9457a4519)

### What is the flag?

![image](https://github.com/user-attachments/assets/d8e6c725-11d0-47de-85a6-c634c0be81ed)
