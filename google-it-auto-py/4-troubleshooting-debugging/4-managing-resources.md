# 🗂️ Managing Resources – Cheatsheet

> **Curso:** Google IT Automation with Python  
> **Curso 4:** Troubleshooting and Debugging Techniques  
> **Módulo 4:** Managing Resources  

---

## 📘 Introducción

- **Resource Management** (gestión de recursos) se refiere a manejar memoria, archivos, conexiones y otros recursos del sistema de manera eficiente.  
- Objetivo: evitar errores por recursos agotados y optimizar el rendimiento de programas y sistemas.

---

## 🔹 Conceptos Clave

- **Memory Leaks:** memoria ocupada que no se libera  
- **Handles/Connections:** archivos, bases de datos o sockets abiertos que deben cerrarse  
- **Garbage Collection:** liberación automática de memoria en Python  

---

## 🔹 Buenas Prácticas en Python

### Archivos y Conexiones

- Usar **context managers (`with`)** para asegurar cierre de recursos:

```python
with open("archivo.txt", "r") as f:
    contenido = f.read()
# El archivo se cierra automáticamente al salir del bloque
````

* Para bases de datos o sockets, siempre cerrar conexiones:

```python
conn = open_db_connection()
try:
    # operaciones
finally:
    conn.close()
```

### Memoria

* Liberar objetos que ya no se usan
* `gc` → módulo para control del garbage collector
* Evitar almacenar grandes cantidades de datos innecesarios

---

## 🔹 Monitoreo de Recursos

* **CPU y memoria:** `psutil`, `top`, `htop`, Task Manager
* **Uso de disco:** verificar espacio disponible para operaciones de I/O
* **Logs:** registrar consumo de recursos y errores

```python
import psutil

print(psutil.cpu_percent())
print(psutil.virtual_memory())
```

---

## 🔹 Herramientas Recomendadas

| Herramienta | Uso                                                 |
| ----------- | --------------------------------------------------- |
| `with`      | Manejo seguro de archivos y recursos                |
| `psutil`    | Monitoreo de CPU, memoria y procesos                |
| `gc`        | Gestión manual de garbage collection                |
| Logging     | Registrar eventos y errores relacionados a recursos |

---

## 📚 Referencias

* 🐍 [Python Docs – Context Managers](https://docs.python.org/3/reference/datamodel.html#with-statement-context-managers)
* 🐍 [psutil Documentation](https://psutil.readthedocs.io/en/latest/)
* 🐍 [Python Docs – Garbage Collection](https://docs.python.org/3/library/gc.html)
