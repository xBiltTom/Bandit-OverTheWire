<aside>
💡

Objetivo del nivel:
La contraseña para el siguiente nivel se encuentra en un archivo llamado readme, ubicado en el directorio principal. Usa esta contraseña para iniciar sesión en bandit1 mediante SSH. Cuando encuentres la contraseña de un nivel, usa SSH (en el puerto 2220) para acceder a él y continuar el juego.

</aside>

El nivel nos pide ubicar la contraseña en un archivo llamado readme en el directorio principal. Para verificar que eso es cierto podemos hacer ls para listar los archivos en el directorio que nos encontramos.

![image.png](/levels/Bandit0-1/img/bandit0-1img.png)

Tras haber confirmado la existencia del archivo procedemos a usar el comando cat que permite leer archivos:

```bash
cat [archivo]
```

Entonces:

```bash
cat readme
```

El archivo cuenta con un mensaje de felicitaciones y lo que mas nos interesa, la contraseña del siguiente nivel en el final del texto.

Es preferible que lo resuelvas por tu cuenta, pero si quieres continuar desde un nivel y olvidaste guardar la password entonces puedes hacer uso de la siguiente (Puede no funcionar si las password desde over the wire cambiaron):

<details>

<summary>Pass …</summary>

ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If

</details>

El objetivo del nivel nos indica que para pasar el siguiente nivel debemos hacer lo mismo que hicimos para entrar al juego. Es decir conectarnos mediante ssh al usuario nivel, en este caso sería bandit1. Entonces la conexión sería de la siguiente manera:

```html
ssh bandit1@bandit.labs.overthewire.org -p 2220
```