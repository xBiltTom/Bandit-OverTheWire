---

<aside>
💡

## Level Goal

The password for the next level is stored in a hidden file in the **inhere** directory.

</aside>

---

El enunciado nos dice que la contraseña para el siguiente nivel se encuentra guardado dentro de un archivo oculto en el directorio llamado “inhere”.

En los sistemas Linux/Unix, cualquier archivo o carpeta cuyo nombre empieze con un punto (por ejemplo: .archivo_secreto) se considera “oculto”. Es decir que si usamos el comando de toda la vida para listar los archvos “ls” no funcionará ya que está diseñado para ignorar este tipo de archivos y mantener la vista limpia.

### Estrategia

Primero debemos movernos al directorio donde se encuentra el archivo oculto. Para movernos entre directorios hacemos uso del comando cd  (que significa change directory) de la siguiente forma:

```bash
cd [nombre_directorio]
```

Al momento de entrar a este nivel estamos en home por defecto, si hacemos “ls” veremos que la salida nos arroja “inhere”. Entonces para acceder a el debemos de hacer:

```bash
cd inhere
```

Tras haber entrado podemos intentar hacer “ls” y nos daremos cuenta que por lo explicado al inicio el archivo oculto no aparece. Para poder listar archivos ocultos debemos hacer uso del siguiente comando:

```bash
ls -a
```

> *Los comandos en Linux aceptan “banderas” (flags) que modifican su comportamiento, generalmente representadas con un guión. La bandera -a le dica a ls que sea completamente transparente y te muestre absolutamente todo, incluyendo los archivos ocultos.*
> 

Cuando hacemos uso de ls -a, siempre veremos un punto ( . ) y dos puntos ( . . ). El punto representa el directorio actual donde nos encontramos y los dos puntos representan el directorio padre ( la carpeta anterior ). Por ello es que cuando hacemos “cd ..” podemos brincar hacia atrás. Pero para nuestro ejercicio actual debemos centrarnos en el archivo con 3 puntos que aparecerá con el nombre “…Hiding-From-You”.

## Solución paso a paso:

Partiendo desde home al momento de entrar al nivel.

1. Escribe ls para confirmar que la carpeta inhere se encuentra en home.
2. Con “cd inhere” entramos dentro dentro de la carpeta. 
(Puedes notar que tu *prompt* cambiará de `~$` a `~/inhere$`, indicando tu nueva ubicación).
3. Ejecuta ls -a para revelar los archivos ocultos dentro del directorio.
4. Procedemos a usar cat para la lectura de archivos:
    
    ```bash
    cat ...Hiding-From-You
    ```
    
5. Copia la contraseña revelada.
6. Ejecuta exit para volver a la máquina local.
7. Conéctate al siguiente nivel usando el bandit4:
    
    ```bash
    ssh bandit4@bandit.labs.overthewire.org -p 2220
    ```
    

---

Es preferible que lo resuelvas por tu cuenta, pero si quieres continuar desde un nivel y olvidaste guardar la password entonces puedes hacer uso de la siguiente (Puede no funcionar si las password desde over the wire cambiaron):

<details>

<summary>Password</summary>

2WmrDFRmJIq3IPxneAaMGhap0pFhF3NJ

</details>

---