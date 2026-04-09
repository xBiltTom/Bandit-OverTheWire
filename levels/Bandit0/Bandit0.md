<aside>
💡

El objetivo de este nivel es que inicies sesión en el juego usando SSH. El host al que necesitas conectarte es **bandit.labs.overthewire.org**, en el puerto 2220. El nombre de usuario es **bandit0** y la contraseña es **bandit0**. Una vez Inicia sesión, ve a la página [de Nivel 1](https://overthewire.org/wargames/bandit/bandit1.html) para descubrir cómo superar Nivel 1.

</aside>

El primer nivel pide que el usuario se conecte mediante ssh al host de overthewire usando bandit0 como usuario y bandit0 como contraseña, y además nos da un puerto específico.

Para conectarnos mediante ssh debemos hacer lo siguiente:

```bash
ssh usuario@host -p [PUERTO]
```

Entonces, para cumplir con lo que pide el enunciado:

```bash
ssh bandit0@bandit.labs.overthewire.org -p 2220
```

Al darle enter nos pedirá una contraseña, que tal como dicta el enunciado es “bandit0”. En la terminal no se muestra lo que se ingresa por teclado pero si se escribe correctamente la contraseña tendremos un mensaje grande de éxito:

![image.png](/levels/Bandit0/img/bandit0img01.png)