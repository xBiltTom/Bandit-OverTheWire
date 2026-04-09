> 
> 
> 
> ## Level Goal
> 
> The password for the next level is stored in a file somewhere under the **inhere** directory and has all of the following properties:
> 
> - human-readable
> - 1033 bytes in size
> - not executable

### Objetivo

El enunciado nos pide encontrar un único archivo escondido entre un montón de carpetas basándonos estrictamente en las propiedades que se nos menciona: debe ser legible, pesar exactamente 1033 bytes y no ser ejecutable.

### Estrategia

Para realizar esta tarea debemos hacer uso de uno de los comandos más poderosos de bash, el comando find. Este comando busca archivos basándose en las condiciones que nosotros definamos. Su estructura básica es:

```bash
find [ruta_donde_buscar] [condiciones]
```

Vamos con las partes que nos servirán para armar el comando que nos ayudará a cumplir el objetivo del nivel:

[ruta_donde_buscar] :

- Ruta: Si ya entramos en el directorio “inhere” el punto de partida debe ser el punto de siempre ( significa ”desde este directorio”. Si estamos afuera entonces la ruta será: “ ./inhere ”.

[condiciones]:

- -type f : Le dice al comando que ignore las carpetas y se centre estrictamente en archivos. ( “f” viene de file ).
- -size 1033c : Le indica al comando el tamaño exacto. La letra c es fundamental, ya que significa caracteres ( que dentro del contexto de -size equivalen a los bytes, no onfundir en otros aspectos ). Si no se coloca una letra find buscará por defecto en bloques de 512bytes.
    
    Tamaños:
    
    | Sufijo | Significado |
    | --- | --- |
    | `c` | bytes |
    | `k` | KB (1024 bytes) |
    | `M` | MB |
    | `G` | GB |
- -executable : Busca archivos que se puedan ejecutar (como si de un programa se tratase).
- ! (Negación): Al colocarlo delante de una condición la niega. Por lo tanto “ ! -executable ” significa “que no sea ejecutable”.
- -readable : Opcional para este caso, pero significa que buscará archivos donde nuestro usuario tiene permisos de lectura.

### Solución paso a paso

Partiendo de home:

1. Usamos ls para verificar la existencia del directorio “inhere” y entramos a el usando el comando “cd”.
2. Procedemos a armar el comando find combinando la ruta ( que tras entrar a inhere se convierte en “ . ” ) y encadenando las tres condiciones que nos pide cumplir el juego (tipo de archivo, tamaño y que no sea ejecutable) separadas por espacios:
    
    ```bash
    find . -type f -size 1033c ! -executable
    ```
    
3. Procedemos a ejecutar el comando y tras ello, find imprimirá en la pantalla la ruta exacta del único archivo que cumple con las reglas que le pusimos:
    
    ```bash
    bandit5@bandit:~$ ls
    inhere
    bandit5@bandit:~$ cd inhere
    bandit5@bandit:~/inhere$ ls
    maybehere00  maybehere02  maybehere04  maybehere06  maybehere08  maybehere10  maybehere12  maybehere14  maybehere16  maybehere18
    maybehere01  maybehere03  maybehere05  maybehere07  maybehere09  maybehere11  maybehere13  maybehere15  maybehere17  maybehere19
    bandit5@bandit:~/inhere$ find . -type f -size 1033c ! -executable
    ./maybehere07/.file2
    bandit5@bandit:~/inhere$
    ```
    
4. Una vez que find nos ha encontrado la ruta donde está el archivo que buscamos (en este caso es ./maybehere07/ .file2), usamos el confiable comando cat para leer su contenido:
    
    ```bash
    cat ./maybehere07/.file2
    ```
    
5. Copiamos la contraseña que nos muestra el anterior comando, le damos a exit y entramos como bandit6 para seguir con el siguiente nivel.

---

Es preferible que resuelvas el reto por tu cuenta, pero si quieres continuar desde el siguiente nivel y olvidaste guardar la contraseña entonces puedes hacer uso de la siguiente (Puede no funcionar si las contraseñas desde over the wire cambiaron):

<details>

<summary>Password</summary>

HWasnPhtq9AVKe0dmk45nxy20cvUa6EG

</details>

---