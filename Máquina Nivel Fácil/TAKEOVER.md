# RESOLUCIÓN DE LA MÁQUINA TAKEOVER

## TASK 1 - HELP US

Hacemos fuerza bruta con ffuf.

![image](https://github.com/user-attachments/assets/22654561-c041-4b54-b5a1-69c30447eb04)

Si queremos usar el parámetro support, antes tenemos que añadirlo al /etc/hosts.

Esto lo podemos ver clicando al candado de la url, y dándole a "view certificate".

![image](https://github.com/user-attachments/assets/fab2ad5c-e559-402f-8bf0-e235dd8fa3dc)

Copiamos el DNS Name que hemos visto al /etc/hosts

![image](https://github.com/user-attachments/assets/eb0c260f-4f70-4bfc-b729-5c48d0d30717)

### What's the value of the flag?

Ponemos esto en la url: http://secrethelpdesk934752.support.futurevera.thm

![image](https://github.com/user-attachments/assets/1abca35e-c7d1-4e87-9a50-a6b4dfa4c0cf)

![image](https://github.com/user-attachments/assets/a6ae9088-33c0-4658-bb83-6b877c734939)


