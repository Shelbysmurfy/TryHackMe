# RESOLUCIÓN DE LA MÁQUINA 0day

Abrimos la máquina y vemos su IP.

![image](https://github.com/user-attachments/assets/4b982a84-7c7f-4596-b545-c306c1c7d3c3)

Hacemos un nmap para poder ver los puertos que estan abiertos para la IP seleccionada, para ver servicios, versiones...

![image](https://github.com/user-attachments/assets/d3bf94c5-86cb-40a7-8d61-812c6ef8b085)

Hacemos fuerza bruta con gobuster.

![image](https://github.com/user-attachments/assets/2532ba1c-fa44-4a4e-a32d-462ef3ef5234)

Encontramos un directorio bastante importante, "cgi-bin", el cual tiene una potente vulnerabilidad en versiones antiguas de Bash, llamada ShellShock.

Vamos a usar la herramienta nikto para ver si es vulnerable.

![image](https://github.com/user-attachments/assets/8ff469f2-873c-486b-9c30-7201274b707b)

![image](https://github.com/user-attachments/assets/36065c92-5cea-437d-b960-5437d0e29fae)

Probamos la vulnerabilidad lanzando un "curl" con la ruta del /cgi-bin, y ejecutando el "comando whoami".

![image](https://github.com/user-attachments/assets/c6bd18f2-6394-4b2d-b9fe-763a2847229c)

Hacemos una reverse shell, usando como IP la tun0.

![image](https://github.com/user-attachments/assets/05a41106-48d1-49ce-84d1-f85ad760a7b3)

Encontramos la primera flag, la del user.

![image](https://github.com/user-attachments/assets/586821ef-753c-489d-b7b8-2b8669027487)

![image](https://github.com/user-attachments/assets/70e51f84-07d2-47ed-905b-6374451efbfb)

Encontramos que la versión del sistema tiene un exploit que trata de abusar de los overlays.

![image](https://github.com/user-attachments/assets/ce9cf099-ed40-40fe-b087-8c061e969647)

![image](https://github.com/user-attachments/assets/75e8f4c2-5cba-4ef0-8e4c-e7db4c9f1f9f)

Seguimos los pasos que nos dice el github para poder ejecutar el exploit correctamente.

Github: https://github.com/elit3pwner/CVE-2015-1328-GoldenEye

![image](https://github.com/user-attachments/assets/d6aefd21-500c-4f35-a6e3-eb423b40b7ce)

Intentamos compilar el exploit pero nos da un error "intencionado" en el que el binario "gcc" no encuentra el PATH.

![image](https://github.com/user-attachments/assets/90fcb79e-4848-45f5-8287-34da87b9a51b)

Dado esto nosotros podemos añadir el PATH default y volver a intentar compilar el exploit, y nos funciona correctamente.

![image](https://github.com/user-attachments/assets/c0a6255d-f142-46eb-8999-6346c0cc12f3)

Ejecutamos el exploit y ya somos root.

![image](https://github.com/user-attachments/assets/a001a4ab-1117-449f-a302-a4be0b87d9f8)

Y encontramos la segunda flag, la del usuario root.

![image](https://github.com/user-attachments/assets/e0172f98-3335-4247-b125-b13ec9e6accb)

![image](https://github.com/user-attachments/assets/ddb3dbe3-3f12-4fd9-aadd-9e191b63496c)

