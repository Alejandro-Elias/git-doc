## Mejores Prácticas: Commits en Git

📦 ¿Qué es un commit?
Es la unidad básica de trabajo en Git.

Debe contener cambios pequeños y relacionados entre sí.

Se recomienda que el commit haga una sola cosa (cambio atómico).

🧬 ¿Qué es un cambio atómico?
Un cambio atómico es aquel que no puede dividirse en cambios más pequeños sin perder sentido. Por ejemplo:

✅ Agregar una función completa → cambio atómico.

❌ Agregar media función y cambiar el nombre de una variable en otro archivo → no atómico.

🛠️ Buenas prácticas
❌ No uses git add . sin revisar.

✅ Mejor agregá los cambios de forma selectiva, usando:

El control de cambios del IDE.

lazygit (interfaz visual en terminal).

git add -p para interactuar por partes.

📝 Mensajes de commit
Deben ser claros y descriptivos.

Usá el modo imperativo en presente:

✅ Agrega validación de correo

❌ Agregó validación de correo

❌ Agregando validación...

Escribí el qué y no necesariamente el cómo:

✅ Corrige bug en validación de login

❌ Arregla cosas

✏️ Modificar commits
🔧 Antes del push:
``` bash
git commit --amend
```
Permite modificar el último commit (mensaje o contenido).

🧨 Después del push:
```bash
git revert <hash>
```
Crea un nuevo commit que revierte los cambios del anterior.
Es la opción más segura en entornos colaborativos.

⚠️ También se puede:
```bash
git reset HEAD~
```
Deshace el último commit y deja los cambios en staging.

⚠️ No recomendado si ya hiciste push, puede causar conflictos con otros colaboradores.

🚫 ¡Cuidado con el push --force!
⚠️ No uses git push --force a menos que estés completamente seguro.

Puede borrar commits ajenos y causar caos.

Mejor usá:

```bash
git push --force-with-lease
```
Esto fuerza el push solo si nadie más ha subido cambios desde tu último pull. Mucho más seguro.

🧠 Recordá
Hacer commits pequeños, claros y significativos no solo mejora tu código, también mejora tu futuro yo cuando tengas que debuguear algo a las 3AM.