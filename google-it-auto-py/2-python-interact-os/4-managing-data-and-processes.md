# 🐍 Python Cheatsheet – Managing Data and Processes

**Curso:** Google IT Automation with Python
**Módulo:** Managing Data and Processes with Python
**Tema:** Manejo de datos, subprocesos y automatización del sistema

---

## 📘 Introducción

Python permite interactuar con el sistema operativo, ejecutar comandos, procesar datos y automatizar tareas mediante módulos clave:

* **os** → archivos, directorios y entorno del sistema
* **sys** → argumentos desde terminal y ejecución del script
* **subprocess** → ejecutar comandos externos
* **shutil** → copiar, mover y borrar archivos/directorios

---

## 📂 Working with the OS – módulo `os`

### Obtener información del sistema

```python
import os

print(os.name)         # 'posix', 'nt', etc.
print(os.getcwd())     # directorio actual
print(os.listdir())    # archivos del directorio actual
```

### Crear, renombrar y eliminar directorios

```python
os.mkdir("nueva_carpeta")
os.makedirs("carpeta1/carpeta2")  # crea jerarquía
os.rename("vieja_carpeta", "nueva_carpeta")
os.rmdir("nueva_carpeta")         # solo si está vacía
```

### Variables de entorno

```python
print(os.environ.get("HOME"))
os.environ["MY_VAR"] = "123"
```

---

## 🧩 System Arguments – módulo `sys`

### `sys.argv`: argumentos desde la terminal

```python
import sys

# python script.py arg1 arg2
print(sys.argv)      # ['script.py', 'arg1', 'arg2']

arg1 = sys.argv[1]   # acceder al primer argumento
```

### `sys.exit()`: terminar ejecución

```python
import sys

if len(sys.argv) < 2:
    print("Faltan argumentos")
    sys.exit(1)   # código de error
```

---

## ⚙ Running Commands – módulo `subprocess`

### Ejecutar un comando y obtener la salida

```python
import subprocess

result = subprocess.run(["ls", "-l"], capture_output=True, text=True)
print(result.stdout)
```

### Manejo de errores

```python
result = subprocess.run(
    ["cat", "archivo.txt"],
    capture_output=True,
    text=True
)

if result.returncode == 0:
    print("Éxito:", result.stdout)
else:
    print("Error:", result.stderr)
```

### Ejecutar en modo shell

```python
subprocess.run("echo Hola Mundo", shell=True)
```

⚠ **Advertencia:** usar `shell=True` con cuidado por seguridad.

---

## 🧰 File and Directory Operations – módulo `shutil`

| Función                 | Descripción                | Ejemplo                           |
| ----------------------- | -------------------------- | --------------------------------- |
| `shutil.copy(src, dst)` | Copiar archivo             | `shutil.copy("a.txt", "b.txt")`   |
| `shutil.move(src, dst)` | Mover archivo/directorio   | `shutil.move("a.txt", "backup/")` |
| `shutil.rmtree(path)`   | Borrar directorio completo | `shutil.rmtree("folder")`         |

---

## 📄 Reading and Writing Files (Recap)

```python
import csv

with open("data.csv") as f:
    reader = csv.DictReader(f)
    for row in reader:
        print(row["name"], row["age"])
```

---

## 🔹 Good Practices

* Usar `with open()` para manejar archivos.
* Usar `subprocess.run()` con `capture_output=True` y `text=True`.
* Validar argumentos con `sys.argv` y devolver códigos de error significativos.
* Combinar `os` + `shutil` para operaciones complejas de archivos.
* Manejar excepciones al trabajar con archivos o procesos externos.

---

## 📚 Referencias oficiales

* Python `os` module
* Python `sys` module
* Python `subprocess` module
* Python `shutil` module
* Real Python – Working with Files and Directories


