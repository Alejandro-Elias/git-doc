# Git: Estructura y Conceptos Clave

---

## Directorios y Archivos Importantes en Git

- **objects**  
  Carpeta donde se guarda todo el contenido de la base de datos de Git.

- **refs**  
  Contiene referencias a los objetos commits.

- **HEAD**  
  Apunta a la rama actual, es decir, dónde estamos parados trabajando.

- **index**  
  Área temporal donde se guardan los cambios preparados antes de hacer commit. Solo existe si hay cambios staged.

---

## Objetos en Git

Cada objeto tiene un **hash único** generado a partir de su contenido. Son **inmutables**, no pueden ser modificados.

### Tipos de objetos:

- **Blob**  
  - Representa el contenido de un archivo en un momento dado.  
  - No guarda información sobre el nombre del archivo, solo su contenido.

- **Tree**  
  - Representa el estado del directorio en un momento dado.  
  - Contiene referencias a blobs y a otros trees, junto con nombres y permisos.

- **Commit**  
  - Representa un conjunto de cambios en un momento específico.  
  - Registra quién hizo los cambios, cuándo y por qué.  
  - Cada commit apunta al commit anterior, permitiendo recorrer la historia del proyecto.  
  Ejemplo:  
  `"first commit" <- "second commit" <- "third commit" ...`

---

## Refs

- Son **nombres simbólicos** que apuntan a un commit específico para facilitar el acceso.
- Directorios importantes:
  - `.git/refs` — contiene todas las referencias del repositorio.
  - `.git/refs/stash` — referencias a la pila de cambios guardados con `git stash`.
  - `.git/refs/heads` — ramas locales con el hash del último commit.
  - `.git/refs/remotes` — ramas remotas, se actualizan con `git fetch`.

---

## Tags

- Son referencias a un commit específico.
- Se usan para marcar momentos importantes en el proyecto.
- Son estáticos, siempre apuntan al mismo commit y no se mueven.
- Para crear un tag:  
```
  git tag <nombre-del-tag> [<hash-opcional>]
```
  ---

### Cómo moverse a commits anteriores

    ```
    git checkout <hash-del-commit>
    git checkout <tag>
    git checkout HEAD^
    git checkout HEAD~1
    git checkout main^
    ```