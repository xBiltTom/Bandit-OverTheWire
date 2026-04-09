---

<aside>
💡

## Level Goal

The password for the next level is stored in a file called located in the home directory`--spaces in this filename--`

</aside>

---

El objetivo del nivel nos dice que la contraseña para el siguiente nivel se encuentra en un archivo dentro del directorio principal llamado `--spaces in this filename--` . Esto nivel combina tanto lo visto en el nivel pasado con los guiones y ahora adiciona los espacios.

### Estrategia

Para vencer esto usaremos la estrategia del nivel 1 con la nueva para el nivel 2:

- **Para neutralizar el guión:** Usaremos la ruta para inhibir los efectos del guión en la terminal. Esto obliga a bash a entender que estamos apuntando a una ruta física, y no a una opción del comando.
- **Para neutralizar los espacios:** Debemos envolver el nombre en comillas “[nombre_archivo]” o usar la barra invertida ( \ ) antes de cada espacio:

### Solución.

Combinando la primera estrategia y sumando cualquiera de los caminos de la segunda estrategia tendremos:

```bash
cat ./"--spaces in this filename"
```

O

```bash
cat ./--spaces\ in\ this\ filename--
```

Tras ello podremos acceder a la contraseña para acceder al siguiente nivel:

---

Es preferible que lo resuelvas por tu cuenta, pero si quieres continuar desde un nivel y olvidaste guardar la password entonces puedes hacer uso de la siguiente (Puede no funcionar si las password desde over the wire cambiaron):
<details>

<summary>Password</summary>

MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx
</details>

---