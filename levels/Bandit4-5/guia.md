---

> 
> 
> 
> ## Level Goal
> 
> The password for the next level is stored in the only human-readable file in the **inhere** directory. Tip: if your terminal is messed up, try the “reset” command.
> 

El enunciado nos dice que la contraseña se encuentra en el único archivo legible por humanos dentro del directorio “inhere”. Es decir que dentro de esta carpeta habrá varios archivos pero solo uno de ellos es texto puro. Los demás pueden ser binarios o basura.

Si usamos la adivinación como estrategia y vamos probando archivo por archivo ( con cat ) para ver cual es el correcto, la terminal intentará imprimir caracteres de contro binarios. Esto suele romper la consola, ya sea cambiando los colores, los márgenes o mostrando símbolos extraños. Por eso el enunciado nos da el tip de que si nuestra terminal se vuelve loca, debemos escribir el comando reset para que todo vuelva a la normalidad.

Al entrar dentro del directorio usando “cd” veremos 10 archivos que comienzan con un guión y llevan la serie -file00, -file01 … -file09.

## Estrategia:

Para evitar romper nuestra terminal tenemos que inspeccionar los archivos antes de abrirlos. Para ello usamos 2 herramientas clave:

- file (Analizador de tipos): Este comando inspecciona el interior de un archivo y te dice qué tipo de datos contiene( por ejemplo , si es un texto, un archivo comprimido, una imagen, etc.) Se usa así:
    
    ```bash
    file [nombre_archivo]
    ```
    
- * (El comodín o Wildcard): En bash, el asterisco significa “todo”. En lugar de ejecutar el comando file diez veces ( una por cada archivo ), podemos usar el comodín para aplicarlo a todos los archivos del directorio de golpe.

### Solución paso a paso:

Partiendo desde home:

1. Usa “ls” para ver qué hay dentro de home y verificar la existencia de la carpeta inhere. Usa “cd inhere” para entrar dentro de la carpeta.
2. Dentro del directorio “inhere” ejecuta un “ls” rápido para listar a todos los archivos. Veremos los diez archivos enumerados: -file00, -file01, …, -file09.
3. Ahora debemos ejecutar file para verificar el tipo de archivo de cada uno de los archivos dentro del directorio. Hay que recordar que como estos empiezan con un guión no podemos ejecutar el comando directamente sino que debemos ayudarnos de alguna de las estrategias con las que logramos pasar los niveles donde había este tipo de inconveniente. Entonces procedemos a realizar lo siguiente:
    
    ```bash
    file ./*
    ```
    
    > *Esto le dice a Bash: “Ejecuta file” en TODOS los elementos dentro de este directorio ‘ ./ ‘ “. Hay que tener en cuenta que solo surtirá efecto en los archivos que no están ocultos, es decir los que cuyo nombre no empiezen con punto.*
    > 
4. Tras aplicar el comando se nos arrojará el resultado en una lista:
    
    ```bash
    bandit4@bandit:~/inhere$ file ./*
    ./-file00: data
    ./-file01: data
    ./-file02: data
    ./-file03: DOS executable (COM), start instruction 0x8c887e10 c3ee96c9
    ./-file04: data
    ./-file05: data
    ./-file06: data
    ./-file07: ASCII text
    ./-file08: data
    ./-file09: data
    ```
    
    Como podemos ver la mayoría dice que su tipo de archivo es data (datos legibles), pero solo una dirá ASCII text siendo este nuestro objetivo.
    
5. Ahora usamos el siempre confiable cat para leer el contenido de ese archivo y acceder a la contraseña que nos dará el acceso al siguiente nivel:
    
    ```bash
    cat ./-file07
    ```
    
6. Copiamos la contraseña, salimos usando exit y procedemos a conectarnos como bandit5:
    
    ```bash
    ssh bandit5@bandit.labs.overthewire.org -p 2220
    ```
    

---

Es preferible que resuelvas el reto por tu cuenta, pero si quieres continuar desde el siguiente nivel y olvidaste guardar la contraseña entonces puedes hacer uso de la siguiente (Puede no funcionar si las contraseñas desde over the wire cambiaron):

<details>

<summary>Password</summary>

4oQYVPkxZOOEOO5pTW81FB8j8lxXGUQw

</details>

---