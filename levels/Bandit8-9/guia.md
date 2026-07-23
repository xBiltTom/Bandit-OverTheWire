> ## Level Goal
> The password for the next level is stored in the file data.txt and is the only of text that occurs only once.

### El objetivo
El enunciado nos dice que existe un archivo que cuenta con miles de líneas de texto, pero que solo una de ellas no se repite (esa es nuestra contraseña).

### La trampa
En linux existe un comando hecho para este tipo de casos, con el problema que es miope. Es decir, solo se da cuenta de la existencia de líneas repetidas siempre y cuando estas sean contiguas. Por lo tanto, para poder explotar su funcionalidad primero debemos asegurarnos que el texto se encuentre completamente ordenado.

### El arsenal
Para resolver este problema, debemos encadenar herramientas siemples para un resultado complejo:
- **`sort` (Ordenar)**: Este comando lee un archivo de texto y ordena todas sus líneas alfabéticamente. La utilidad en este caso es que al ordenar el texto todas las líneas que se repiten quedaran juntas una debajo de la otra.
- **`uniq -u` (Filtrar únicos)**: El comando `uniq` detecta duplicados contiguos, con `-u` nos aseguramos que solo nos reporte aquellas líneas que nunca se repetieron. Sin aquella bandera saldrían todas las líneas y las que se repiten saldrían una sola vez.
- **| (Pipe o Tubería)**: Al colocar este símbolo entre 2 sentencias, hace que la salida de la sentencia que se encuenta a la izquierda pase como entrada para la sentencia de la derecha. Para nuestro caso devolvemos las líneas de texto ordenados desde la izquierda y hacemos el filtro en la derecha.

### Solución paso a paso
1. Tras ingresar como `bandit8` nos aseguramos de tener el archivo data.txt en el directorio principal.
2. Luego, ejecutamos el comando que hemos estado preparando con lo estudiado anteriormente:
    ```bash
    sort data.txt | uniq -u
    ```
    - Ordena las líneas del texto que se encuentra en el archivo data.txt, aquel texto ordenado se pasa como entrada al comando `uniq` y este devuelve en pantalla aquellas líneas que nunca se repetieron gracia al uso de la bandera `-u`.
3. Tal como el enunciado lo dice, la contraseña aparecerá en pantalla debido a que es la única línea de texto que no se repite en todo el archivo.

---
### Contraseña actual al 22/07/26

<details>

<summary>Ver</summary>

EjmOSvuAu7sGAHqHVcBDPirRe9T03kxl

</details>

---
