> 
> 
> 
> ## Level Goal
> 
> The password for the next level is stored somewhere on the server and has all of the following properties:
> 
> - owned by user bandit7
> - owned by group bandit6
> - 33 bytes in size

### Objetivo
Se nos pide encontrar un archivo que se encuentra en cualquier parte del servidor. Este archivo cuenta con las siguientes características:
- Pertenece al usuario bandit7.
- Pertenece al grupo bandit6.
- Pesa 33 bytes.

### La trampa
Si intentamos hacer la búsqueda en todo el servidor (de forma automatizada como se verá mas adelante) la pantalla se nos llenará de mensajes de error diciendo **Permission denied** (Permiso denegado). Esto ocurre porque somos un usuario con pocos privilegios (bandit6) intetando husmear en carpetas de otros usuarios o del sistema operativo. Como el archivo donde se encuentra la contraseña si podrá ser leido por nosotros (es decir que si aparecerá cuando hagamos la búsqueda), se perderá en un montón de mensajes de error.

### El arsenal
En el nivel anterior, conocimos el comando **find**, ahora vamos a potenciarlo usando uno de los conceptos más poderosos de bash: **la redirección de flujos**.
- **/ (El directorio raíz)**: En linux, / es la base de todos. En el nivel anterior se usó '.' que significa aquí, ahora usaremos '/' para decirle a find que busque en todo el servidor.
- **-user** y **-group**: Estas son las nuevas banderas a usar en find. Permiten que podamos filtrar archivos por su dueño (ej: -user bandit7) y a que grupo de permisos pertenece (ej: -group bandit6).
- **2>/dev/null (El agujero negro)**: En linux, los programas tienen canales o salidas por donde se envía texto a la pantalla: el canal 1 sirve para mostrar la salida normal (los resultados de la ejecución de un comando) y en el canal 2 salen los errores. 
    - El símbolo '>' sirve para desviar esa salida.
    - **/dev/null** es un archivo especial en linux que actúa como agujero negro; todo lo que se envíe ahí se destruye automáticamente.
    - Por lo tanto, al colocar **2>/dev/null** al final de todo nuestro comando, le decimos a bash que ignore los errores y solo nos muestre la salida sin errores.

### Solución paso a paso
- Desde el directorio en el que nos encontramos tras acceder como bandit6 lanzamos el siguiente comando que hemos armado con todo lo mencionado anteriormente (y basado en la premisa de este nivel):
    ```bash
    find / -user bandit7 -group bandit6 -size 33c 2>/dev/null
    ```
    Donde:
    - **find /** 
        - Busca desde la raíz del sistema.
    - **-user bandit7**
        - Solo archivos cuyo propietario sea bandit7.
    - **-group bandit6**
        - Solo archivos cuyo grupo sea bandit6.
    - **-size 33c**
        - Solo archivos cuyo tamaño sea 33 bytes. 
        - La **`c`** significa bytes ("characters").
    - **2>/dev/null**
        - Oculta todos los mensajes de error.
        - Es necesario para este nivel ya que de no añadir el comando será muy dificil ubicar el archivo donde se encuentra la contraseña debido a lo sucia que estará la terminal ocasionado por error de permisos (no tenemos permiso en todos los archivos del sistema).
    - **Salida**
        ```bash
        /var/lib/dpkg/info/bandit7.password
        ```
    - **Lectura de la contraseña**
        - Habiendo ubicado el fichero, procedemos a leerlo para obtener la contraseña:
            ```bash
            bandit6@bandit:~$ cat /var/lib/dpkg/info/bandit7.password
            ```
        - Copiamos la contraseña que nos de la salida del anterior comando, nos deslogueamos de bandit6 y seguimos al siguiente nivel.

---

Contraseña al 22/07/26
<details>

<summary>Password</summary>

Bmnnvf82KzQlfxgAI2d1zYbr1u9pr3E3

</details>

---