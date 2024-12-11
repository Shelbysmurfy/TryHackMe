# RESOPLUCIÓN DE LA MÁQUINA BLUE

Abrimos la máquina y vemos su IP.

![image](https://github.com/user-attachments/assets/e48e886c-9358-4acf-938e-c1d8e6c35a4a)

Hacemos un nmap para poder ver los puertos que estan abiertos para la IP seleccionada.

![image](https://github.com/user-attachments/assets/7efd39f9-b3c3-4a7e-a1c0-f2c69c84e111)

Ahora hacemos un escaneo de los puertos que hemos visto que estan abiertos para saber servicios,versiones...

![image](https://github.com/user-attachments/assets/84d260aa-0aa5-48e7-a6ad-8b72324e3dc7)

Como podemos ver en los resultados del comando que hemos ejecutado, en el puerto 455/tcp, el sistema operativo es Windows 7 Home Basic Service Pack 1 y está configurado en el grupo de trabajo WORKGROUP. Este sistema, con el puerto 445 abierto, es particularmente preocupante ya que es vulnerable a la famosa vulnerabilidad EternalBlue.

Además este puerto es utilizado para compartir archivos y otros recursos en redes Windows mediante el protocolo SMB (Server Message Block).

EternalBlue, que afecta versiones de Windows no actualizadas, explota una vulnerabilidad crítica en el protocolo SMBv1, lo que podría permitir la ejecución remota de código y, en consecuencia, el control completo del sistema afectado.

Aún así ahora ejecutaremos este comando para estar seguros de que es vulnerable.

![image](https://github.com/user-attachments/assets/9bf84180-0718-4ed3-99f6-8db57ca3a1d7)

Como podemos ver si es vulnerable, y por tanto ahora lo que haremos será explotarla a través de la herramienta metasploit.

![image](https://github.com/user-attachments/assets/405f40cf-1891-418d-9b34-719152cd69b0)

Viendo esto lo que haremos será targetear el numero 0.

![image](https://github.com/user-attachments/assets/698544e5-5027-4b7a-9c02-c9e67c1f6aed)

Y una vez dentro lo que hacemos es configurar los los parámetros necesarios para que pueda saber cual es la máquina víctima (RHOSTS), y la mia (LHOST), que es la de tun0.

![image](https://github.com/user-attachments/assets/114bbf40-a8e3-4b3e-a101-6c660db0abef)

Una vez configurados los parámetros ejecutamos el exploit.

![image](https://github.com/user-attachments/assets/72835466-79f5-4887-b414-565529395360)
![image](https://github.com/user-attachments/assets/2021a939-690a-4449-acd6-02c0b5064d39)

Vemos las sessiones abiertas y ejecutamos el comando search para buscar algo en concreto.

![image](https://github.com/user-attachments/assets/bec50e46-51e7-4f26-a1e0-86472b9e9033)

Targeteamos el numero 0 son use.

![image](https://github.com/user-attachments/assets/73ee2e26-42d2-46b5-8dd6-0c21891d03f0)

Usamos el comando options para ver las settings que no tiene valor, y vemos q hay q añadir un valor en session.

![image](https://github.com/user-attachments/assets/ea9a4efc-7d59-43bc-82de-3830bbd66f4c)

![image](https://github.com/user-attachments/assets/9dd8aef4-a18b-4c44-b1ee-9f1177b1b371)

Lo runeamos y vemos que ahora tenemos dos sessiones creadas.

![image](https://github.com/user-attachments/assets/3f64c271-2198-4453-8061-b206ae6d2ee8)

Ejecutamos la session 2.

![image](https://github.com/user-attachments/assets/94d82e75-9526-4d6c-8def-337295a45da6)

Usamos el comando ps desde meterpreter para ver los procesos que estan corriendo.

![image](https://github.com/user-attachments/assets/706334d3-6c23-4563-a53a-9c5e6059861a)

Usaremos el proceso winlogon.exe, ya que es muy comun.

![image](https://github.com/user-attachments/assets/3b8ad080-4388-4c9f-aba1-9c8ed1599eef)

Hacemos un hashdump.

![image](https://github.com/user-attachments/assets/c2356b3d-b54a-4c05-a727-ee6142b0bb63)

Del usuario default que es jon, cogemos la ultima parte que esta entre (::), la copiamos en crackstation y obtenemos una credencial.

![image](https://github.com/user-attachments/assets/9f987b35-2e6d-475b-8eb1-cc287746eb53)

Seguido de esto seguimos las pistas que nos dan en TryHackMe y encontramos las tres flags.

![image](https://github.com/user-attachments/assets/4d55c573-607c-4e9b-b169-78c8603d7bfa)

![image](https://github.com/user-attachments/assets/771913e4-08cb-442f-9074-071291145716)

![image](https://github.com/user-attachments/assets/516cd408-3b01-454e-85c8-445cb7c68e80)










