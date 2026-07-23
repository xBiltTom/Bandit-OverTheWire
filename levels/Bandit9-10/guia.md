> ## Level goal
> The password for the next level is stored in the file data.txt in one of the few human-readable strings, preceded by several ‘=’ characters.

### Objetivo
El enunciado nos dice que la contraseña se encuentra en el archivo data.txt, en una de las pocas líneas que se pueden leer por humanos (En su mayoría cuenta con datos binarios e ilegibles). Esta cadena de texto tiene la peculiaridad de estar precedida por varios `=`, algo así como `===== password...`.

### La trampa
Como este archivo mayormente cuenta con datos binarios, si usamos `cat` para leer el texto destrozaremos nuestra terminal. También si intentamos hacer `grep "===" data.txt` directamente es muy probable que la salida sea algo como `Binary file data.txt matches (El archivo binario coincide)` pero no mostrará nada de texto ya que por seguridad el comando `grep` evita imprimir binarios en pantalla.

### El arsenal
Para solucionar esto, necesitamos una herramienta que haga el trabajo sucio de separar la basura binaria del texto legible por humanos para luego pasarle esa salida a `grep` quien se encargará de encontrar entre las líneas que se pueden leer por humanos aquella o aquellas que coincidan con la secuencia `===` para poder dar con la contraseña.
- **`strings (Extractor de cadenas)`**: Su trabajo es extraer de cualquier archivo (sin importar el tipo) todas las secuencias de caracteres que sean texto legible por humanos ignorando el resto.
- **`grep`**: Pasaremos la salida del uso del anterior comando usando el pipe `|` para que se encargue de buscar la línea de texto legible por humanos que cuente con la coincidencia mencionada en el enunciado de este nivel.

### Solución paso a paso.
1. Tras ingresar como `bandit9` usamos `ls` para verificar la existencia del archivo data.txt dentro del directorio principal.
2. Luego, ejecutamos el siguiente comando:
    ```bash
    strings data.txt | grep "==="
    ```
    - En la salida nos saldrán las coincidencias que se tuvo con la secuencia `===` dentro de las únicas líneas legibles por humanos.
3. Copiamos la contraseña y seguimos al siguiente nivel.

---
### Contraseña al 22/07/26

<details>

<summary>Ver</summary>

B0s2khmbT9u0geKuOoVGW3JZKhndE3BG

</details>

---