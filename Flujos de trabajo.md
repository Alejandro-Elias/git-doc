## 🚀Flujos de trabajo en Git

### 🔀 **Git Flow**

🗂️ Estructura de ramas

Git Flow propone una estructura clara y organizada para gestionar ramas dentro de un proyecto. Las ramas principales son:

main 🟢: Rama principal del proyecto. Contiene el código estable y listo para producción. Solo se debe enviar código completamente probado y seguro.

develop 🧪: Rama de desarrollo. Todas las nuevas funcionalidades se integran aquí antes de pasar a main.

🔧 Flujo de trabajo paso a paso

            +-----------------+          +------------------+
            |     Feature     |<--------|     Develop      |
            +-----------------+          +------------------+
                     |                          |
                     |     Pull Request         |
                     v                          v
            +-----------------+          +------------------+
            |     Develop     |--------->|     Release      |
            +-----------------+          +------------------+
                                                |
                                          Pull Request
                                                v
                                        +---------------+
                                        |     Main      |
                                        +---------------+

Ramas de funcionalidad (feature branches) 🛠️:

Se crean desde develop.

Son temporales y se usan para desarrollar nuevas características.

Una vez finalizadas, se integran en develop mediante pull request.

Deben probarse antes de realizar el merge.

Ramas de release 🚀:

Se crean desde develop cuando hay un conjunto de funcionalidades listas para producción.

Se utilizan para ajustes finales, pruebas y correcciones antes del despliegue.

Las correcciones pequeñas pueden ir en ramas fix que luego se integran a release.

Cuando todo está aprobado, se hace merge explícito a main (aunque técnicamente pueda usarse fast-forward).

Los cambios también deben reflejarse en develop para evitar divergencias.

Ramas de hotfix 🔥:

Se crean directamente desde main para resolver problemas urgentes en producción.

Son la única excepción donde se parte desde main.

Una vez solucionado el problema, se integran a main y también a develop mediante pull request.

⚠️ Consideraciones

Git Flow es útil para proyectos con ciclos largos y planificación formal.

Sin embargo, puede ser complejo y burocrático.

Requiere mantenimiento constante y puede complicar la integración continua (CI) y el despliegue continuo (CD).

Es propenso a desincronizaciones si no se sigue con disciplina.

---

### 🌳 **Trunk-Based Development (Desarrollo Basado en el Tronco)**

📌 Características

Se trabaja directamente sobre la rama principal del proyecto: main.

Regla de oro: el código en main siempre debe estar estable y listo para desplegar.

🔄 Flujo de trabajo

```
+-----------+     +------------------------+
|   Main    |<----|  Feature / Hotfix PR   |
+-----------+     +------------------------+
        ^                     ^
        |                     |
    Tag de Release     Ramas pequeñas
                         (1-2 días)
```

Se crean ramas pequeñas a partir de main para trabajar en cambios.

Estas ramas se integran rápidamente mediante pull request.

✅ Buenas prácticas

Las ramas deben ser de corta duración:

⏱️ 1 a 2 días máximo.

👥 1 o 2 personas como máximo.

Ventajas:

🔄 Minimiza conflictos.

⚡ Acelera el desarrollo.

🚀 Facilita despliegues frecuentes.

El entorno de CI ejecuta pruebas automáticas antes de permitir el merge a main.

Los lanzamientos (releases) se etiquetan con tags directamente sobre main.

Si ocurre un error en producción:

Se crea una rama hotfix desde main, se corrige y se hace pull request.

Se genera un nuevo tag.

🎯 Ventajas

Sencillez y rapidez.

Compatible con Integración y Despliegue Continuo.

Menor burocracia.

Menor riesgo de desincronización entre ramas.

📌 Conclusión

Ambos enfoques tienen sus pros y contras:

Git Flow

Trunk-Based Development

✅ Organizado y formal

✅ Rápido y ágil

❌ Burocrático y complejo

❌ Requiere disciplina en testing

✅ Útil para versiones formales

✅ Ideal para despliegues frecuentes

❌ Puede generar desincronización

❌ Menos apto para equipos desorganizados

La elección depende del equipo, el proyecto y la cultura de desarrollo. Para equipos ágiles y despliegues frecuentes, Trunk-Based suele ser la mejor opción. Para empresas con lanzamientos planificados y varios entornos, Git Flow puede seguir siendo útil.

