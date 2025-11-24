# 💥 Crashing Programs – Cheatsheet

> **Curso:** Google IT Automation with Python  
> **Curso 4:** Troubleshooting and Debugging Techniques  
> **Módulo 3:** Crashing Programs  

---

## 📘 Introducción

- Un **programa crashing** termina inesperadamente, a menudo causando pérdida de datos o interrupciones del servicio.  
- Objetivo: identificar la causa de la caída y aplicar correcciones.

---

## 🔹 Identificación de Caídas

Síntomas comunes:

- Mensajes de error en consola (tracebacks)  
- `Segmentation fault`, `MemoryError` u otras excepciones no manejadas  
- Comportamiento inesperado o congelamiento del programa  

---

## 🔹 Estrategias de Depuración

1. **Revisar tracebacks**  
   - Indican dónde ocurrió el error y la pila de llamadas  
2. **Usar try/except para capturar errores**  

```python
try:
    resultado = 10 / 0
except ZeroDivisionError:
    print("Error: División por cero detectada")
````

3. **Probar partes del código aisladas**

   * Ejecutar funciones individuales para identificar fallas
4. **Revisar logs**

   * Buscar patrones de errores o caídas frecuentes

---

## 🔹 Buenas Prácticas para Evitar Caídas

* Capturar errores conocidos usando `try/except`
* Validar entradas del usuario antes de procesarlas
* Evitar operaciones de memoria intensivas sin control
* Documentar los posibles errores en el código

---

## 🔹 Herramientas Recomendadas

* Python `logging` → registrar errores y eventos
* Depuradores como `pdb` → ejecución paso a paso
* Monitoreo de recursos con `psutil`
* Pruebas unitarias para validar funcionalidades

---

## 📚 Referencias

* 🐍 [Python Docs – Errors and Exceptions](https://docs.python.org/3/tutorial/errors.html)
* 🐍 [Python Docs – Logging](https://docs.python.org/3/library/logging.html)
* 📘 [Real Python – Python Debugging](https://realpython.com/python-debugging-pdb/)

```

