El objetivo principal es poner en práctica los conceptos de Integración y Despliegue Continuo (CI/CD).

## 🚀 Sobre el Proyecto

Este proyecto despliega automáticamente una página web en GitHub Pages cada vez que hay cambios en archivo index.html


## 🛠️ Tecnologías Utilizadas

* **HTML5:** Para la estructura de la web estática.
* **GitHub Actions:** Para automatizar el flujo de trabajo (CI/CD).
* **GitHub Pages:** Como entorno de alojamiento (hosting) para visualizar la web.

## ⚙️ Cómo funciona el Flujo de Trabajo (Workflow)

El despliegue está automatizado. El flujo de trabajo está configurado para que:
1.  Escuche cualquier evento de tipo `push` hacia la rama `main`.
2.  **Condición clave:** Solo se ejecuta si hay modificaciones en el archivo `index.html`.
3.  Si se cumple lo anterior, la Action toma el código y lo publica automáticamente en GitHub Pages.

## 🌐 Ver en vivo

Puedes ver el resultado del despliegue automático aquí: [Inserta aquí la URL de tu GitHub Pages cuando la tengas]
