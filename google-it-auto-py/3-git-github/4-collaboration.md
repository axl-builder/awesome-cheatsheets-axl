# 💻 Git & GitHub Cheatsheet – Collaboration

> **Curso:** Introduction to Git and GitHub  
> **Módulo:** Collaboration  
> **Tema:** Colaboración en proyectos usando GitHub

---

## 📘 Introducción

La colaboración en GitHub implica trabajar con **otros desarrolladores** sin sobrescribir su trabajo.  
Conceptos clave:

- **Fork** → copia de un repositorio en tu cuenta  
- **Pull Request (PR)** → propuesta de cambios a la rama principal de otro repositorio  
- **Merge** → integrar cambios de una rama a otra  
- **Conflict** → cuando dos cambios afectan la misma línea de código  

---

## 🔹 Fork y Clonar Repositorios

```bash
git clone https://github.com/tu-usuario/repositorio.git
git remote add upstream https://github.com/original/repositorio.git
git remote -v   # Ver remotos
````

* `upstream` → apunta al repositorio original del cual hiciste fork

---

## 🔹 Mantener Fork Sincronizado

```bash
git fetch upstream
git checkout main
git merge upstream/main
git push origin main
```

* Trae cambios del repositorio original a tu fork local
* Mantener fork actualizado evita conflictos futuros

---

## 🔹 Trabajar con Ramas y Pull Requests

```bash
git checkout -b feature1
# Hacer cambios
git add .
git commit -m "Agregar feature"
git push -u origin feature1
```

* Crear **Pull Request** en GitHub desde tu rama hacia el repositorio original
* Revisiones de código permiten colaboración segura
* Merge de PR integra los cambios a la rama principal

---

## 🔹 Manejo de Conflictos

* Conflictos ocurren al modificar la misma línea en ramas diferentes
* Resolver manualmente los archivos con `<<<<<<<`, `=======`, `>>>>>>>`
* Marcar como resuelto:

```bash
git add archivo_resuelto
git commit -m "Resolver conflicto"
```

---

## 🔹 Buenas Prácticas de Colaboración

* Usar **branches** por feature o bug
* Sincronizar repositorio antes de crear cambios
* Revisar PR de compañeros y dejar comentarios constructivos
* Hacer commits frecuentes y descriptivos
* Resolver conflictos inmediatamente

---

## 📚 Referencias oficiales

* 🐙 [GitHub Docs – Fork a repository](https://docs.github.com/en/get-started/quickstart/fork-a-repo)
* 🐙 [GitHub Docs – About Pull Requests](https://docs.github.com/en/pull-requests)
* 📘 [Pro Git Book – Collaboration](https://git-scm.com/book/en/v2/Git-Branching-Branches-in-a-Nutshell)

```
