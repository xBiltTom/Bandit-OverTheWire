<aside>
💡

## Objetivo de nivel

La contraseña del siguiente nivel se almacena en un archivo llamado **-** ubicado en el directorio de inicio

</aside>

Tal como dice el objetivo del nivel debemos buscar un archivo llamado “-” dentro del directorio principal (que es el que por defecto nos encontramos al entrar).

Sin embargo esto tiene algo de trampa, ya que si intentamos la estrategia anterior de intentar leer el archivo usando “cat -” notaremos que la terminal se queda congelada o esperando algo. Esto ocurre porque en Bash (y en muchos programas de Linux), el guión por si solo es un caracter especial que significa “lee de la entrada estándar” (es decir, espera a que el usuario escriba algo por teclado), en lugar de buscar un archivo por ese nombre en el disco.

> *Si la terminal se te queda esperando algo, presional ctrl  + c y podrás cancelar el proceso y recuperar el control de la terminal.*
> 

### Cambio de estrategia:

Para evitar que nos pase lo anterior mencionado, en lugar de pasarle solo el guión le pasaremos una ruta.

Existen 2 formas:

- ./[archivo] : En los sistemas basados en Unix, el punto hace referencia al directorio exacto en el que nos encontramos en ese momento.  Al usar “ ./ “antes de un nombre, le estamos diciendo a la terminal:  “Busca este archivo estrictamente aquí dentro”.
- Rutas absolutas: Otra forma es darle la dirección completa desde la raíz del servidor, que en este caso seria /home/bandit1/- (Puedes comprobarlo usando el comando pwd en la terminal).

### Solución:

Entonces escogiendo cualquiera de las 2 alternativas podemos leer el archivo para extraer la contraseña.

1. Forma 1:
    
    ```bash
    cat ./-
    ```
    
2. Forma 2:
    
    ```bash
    cat /home/bandit1/-
    ```
    
    > *Tip: Puedes usar pwd como variable de la para no tener que escribir toda la ruta absoluta:*
    > 
    
    ```bash
    cat $(pwd)/-
    ```
    

---

Es preferible que lo resuelvas por tu cuenta, pero si quieres continuar desde un nivel y olvidaste guardar la password entonces puedes hacer uso de la siguiente (Puede no funcionar si las password desde over the wire cambiaron):
<details>

<summary>Password</summary>

263JGJPfgU6LtdEvgfWU1XP5yac29mFx
</details>

---

Para continuar al siguiente nivel debemos conectarnos vía ssh al usuario nivel 2. Quiere decir que para acceder directamente a cualquier nivel solo debemos hacer :

```bash
ssh bandit[nivel]@bandit.labs.overthewire.org -p 2220
```

Ejemplo, nivel 10:

```bash
ssh bandit10@bandit.labs.overthewire.org -p 2220
```