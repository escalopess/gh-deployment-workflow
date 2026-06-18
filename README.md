# GitHub Actions Deployment Workflow

El objetivo principal es poner en práctica los conceptos de Integración y Despliegue Continuo (CI/CD).

**Este proyecto es la solución a:** 🔗 [Roadmap.sh - GitHub Actions Deployment Workflow](https://roadmap.sh/projects/github-actions-deployment-workflow)

---

## 🚀 Sobre el Proyecto

Este proyecto despliega automáticamente una página web en GitHub Pages cada vez que hay cambios en el archivo `public/index.html`.

**¿Cómo funciona?**
1. Cambias el archivo `public/index.html`
2. Haces `git push` al branch `main`
3. ✅ El workflow se ejecuta automáticamente
4. ✅ Tu sitio se despliega en GitHub Pages sin hacer nada más

---

## 🛠️ Tecnologías Utilizadas

* **HTML5:** Para la estructura de la web estática.
* **GitHub Actions:** Para automatizar el flujo de trabajo (CI/CD).
* **GitHub Pages:** Como entorno de alojamiento (hosting) para visualizar la web.

---

## 📁 Estructura del Proyecto

```
gh-deployment-workflow/
├── .github/
│   └── workflows/
│       └── deploy.yml          # El workflow que hace la magia
├── public/
│   └── index.html              # Tu sitio web
└── README.md
```

---

## ⚙️ Cómo funciona el Flujo de Trabajo (Workflow)

El despliegue está totalmente automatizado. El flujo de trabajo está configurado para que:

1. **Escuche** cualquier evento de tipo `push` hacia la rama `main`
2. **Condición clave:** Solo se ejecuta si hay modificaciones en el archivo `public/index.html`
3. **Si se cumple lo anterior,** la Action toma el código y lo publica automáticamente en GitHub Pages

### Pasos que ejecuta el Workflow:

| Paso | Función |
|------|---------|
| **Checkout** | Descarga el código del repositorio a la máquina temporal |
| **Setup Pages** | Prepara GitHub Pages para recibir archivos |
| **Remove old artifacts** | Borra despliegues anteriores |
| **Upload artifact** | Sube la carpeta `public` |
| **Deploy** | Despliega el sitio en GitHub Pages |

---

## 📝 Configuración del Workflow

El archivo `.github/workflows/deploy.yml` contiene:

```yaml
on:
  push:
    branches:
      - main
    paths:
      - 'public/index.html'    # Solo se ejecuta si cambias esto
```

**Permisos necesarios:**
```yaml
permissions:
  contents: read          # Leer código
  pages: write           # Escribir en GitHub Pages
  id-token: write        # Autenticación segura
```

---

## ✨ Aprendizajes Clave

### Error encontrado: `Failed to load artifacts`

- **Problema:** El workflow intentaba borrar artefactos que no existían en la primera ejecución
- **Solución:** Se agregó `continue-on-error: true` para que continúe aunque falle ese paso

```yaml
- name: Remove old artifacts
  uses: geekyeggo/delete-artifact@v2
  with:
    name: github-pages
  continue-on-error: true  # Continúa aunque no encuentre artefactos
```

---

## 🚀 Cómo usar el Proyecto

### 1. Edita tu HTML:
```bash
# Edita public/index.html con tu editor favorito
nano public/index.html
```

### 2. Haz push:
```bash
git add public/index.html
git commit -m "Actualizar contenido"
git push
```

### 3. ¡Listo! 
- El workflow se ejecuta automáticamente
- Tu sitio se actualiza en GitHub Pages
- Puedes ver el progreso en la sección **Actions**

---

## 📊 Monitorear el Workflow

Ve a la sección **Actions** de tu repositorio para:
- Ver el historial completo de ejecuciones
- Revisar logs detallados si algo falla
- Ejecutar manualmente el workflow si lo necesitas

🔗 **URL del Workflow:** https://github.com/escalopess/gh-deployment-workflow/actions/workflows/deploy.yml

---

## 🌐 Ver en vivo

Puedes ver el resultado del despliegue automático aquí: 
🔗 **https://escalopess.github.io/gh-deployment-workflow/**

---

## 🎓 Conceptos Aprendidos

- ✅ Crear y configurar workflows en GitHub Actions
- ✅ Entender triggers (cuándo se ejecuta un workflow)
- ✅ Usar acciones predefinidas de GitHub
- ✅ Debuggear errores en workflows
- ✅ Automatizar deployment en GitHub Pages
- ✅ Entender el flujo de CI/CD completo

---

## 📚 Recursos Útiles

- [GitHub Actions Documentation](https://docs.github.com/en/actions)
- [GitHub Pages Documentation](https://docs.github.com/en/pages)
- [Workflow File Syntax](https://docs.github.com/en/actions/using-workflows/workflow-syntax-for-github-actions)
- [Roadmap.sh - GitHub Actions Deployment Workflow](https://roadmap.sh/projects/github-actions-deployment-workflow)

---

**Proyecto completado** ✅ - Deployment automático con GitHub Actions y GitHub Pages
