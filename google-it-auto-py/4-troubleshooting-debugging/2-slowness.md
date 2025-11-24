# 🐌 Slowness – Cheatsheet

> **Curso:** Google IT Automation with Python  
> **Curso 4:** Troubleshooting and Debugging Techniques  
> **Módulo 2:** Slowness  

---

## 📘 Introducción

- Los problemas de **slowness** (lentitud) afectan la experiencia del usuario y el rendimiento del sistema.  
- Objetivo: identificar la causa de la lentitud y optimizar el código o los recursos.  

---

## 🔹 Identificación de Lentitud

Síntomas comunes:

- Respuestas tardías del programa o sistema  
- Alta utilización de CPU o memoria  
- Bloqueos temporales o delays en la ejecución  

Técnicas de diagnóstico:

- Medición de tiempo de ejecución (`time`, `timeit`)  
- Perfilado de funciones (`cProfile`, `profile`)  
- Monitoreo de recursos (`psutil`, `top`, `htop`)  

```python
import time

start = time.time()
# Código a medir
end = time.time()
print(f"Tiempo de ejecución: {end - start} segundos")
````

---

## 🔹 Posibles Causas de Lentitud

| Causa                          | Descripción                                               |
| ------------------------------ | --------------------------------------------------------- |
| Bucles innecesarios o anidados | Iteraciones repetitivas y costosas                        |
| Operaciones de E/S             | Lectura/escritura frecuente de archivos o base de datos   |
| Consumo excesivo de memoria    | Objetos grandes en memoria o leaks                        |
| Operaciones complejas          | Algoritmos ineficientes o búsqueda de datos no optimizada |

---

## 🔹 Técnicas de Optimización

* Evitar bucles anidados innecesarios
* Reducir operaciones de I/O
* Usar estructuras de datos eficientes (listas, diccionarios, sets)
* Aplicar **profiling** para detectar funciones críticas

```python
import cProfile

def funcion_lenta():
    for i in range(1000000):
        pass

cProfile.run("funcion_lenta()")
```

* Cachear resultados si es posible
* Monitorear memoria y liberar recursos no utilizados

---

## 🔹 Herramientas Recomendadas

* **Python modules:** `time`, `timeit`, `cProfile`, `psutil`, `tracemalloc`
* **Sistema operativo:** `top`, `htop`, `task manager`
* Logs para seguimiento de tiempos y errores

---

## 📚 Referencias

* 🐍 [Python Docs – timeit](https://docs.python.org/3/library/timeit.html)
* 🐍 [Python Docs – cProfile](https://docs.python.org/3/library/profile.html)
* 🐍 [psutil Documentation](https://psutil.readthedocs.io/en/latest/)

```
