> 
> 
> 
> ## Level Goal
> 
> The password for the next level is stored in the file data.txt next to the word millionth:

### Objetivo
Tenemos un archivo data.txt el cual es gigantesco. Según el enunciado la contraseña está en alguna de las miles de lineas que conforman el texto, justo al lado de la palabra 'millionth'. Si probamos suerte con `cat` lo más probable es que no encontremos la contraseña porque el texto se imprimirá a la volada, e ir buscando con los ojos no es buena idea.

### El arsenal
Para situaciones como esta, no es necesario que abramos el texto e ir buscando línea por línea. Necesitamos de la siguiente herramienta:
- **`grep` (Global Regular Expression Print)**: El trabajo de este comando es permitir escanear el contenido de uno o varios archivos y filtrar únicamente las líneas que coincidan con la palabra o patrón que le pidamos. El resto del texto es ignorado por completo. Su estructura básica es muy sencilla: `grep "palabra a buscar" nombre_del_archivo`.

    >*_Aunque las comillas en la palabra a buscar no siempre son obligatorias para palabras sin espacios, es una excelente práctica usarlas siempre para evitar errores futuros_*

### Solución paso a paso
1. Tras ingresar como `bandit7` hacemos `ls` en el directorio principal para confirmar la existencia del archivo `data.txt`. 
2. Ejecutamos el siguiente comando:
    ```bash
    grep "millionth" data.txt
    ```
    - Esto nos devolverá la línea donde se encuentre alguna coincidencia con la palabra `millionth`.
3. Tal como el enunciado lo dice, la contraseña aparecerá al costado de la palabra buscada, la guardamos y continuamos al siguiente nivel.

---
### Contraseña al 22/07/26

<details>

<summary>Ver</summary>

VR1ljMayciFxbnUokuQmJFw6QC9VKtub

</details>
