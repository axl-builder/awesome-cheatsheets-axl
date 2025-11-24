# 🐛 Troubleshooting Concepts – Cheatsheet

> **Curso:** Google IT Automation with Python  
> **Curso 4:** Troubleshooting and Debugging Techniques  
> **Módulo 1:** Troubleshooting Concepts  

---

## 📘 Introducción

- **Troubleshooting:** proceso sistemático para identificar y resolver problemas en sistemas o aplicaciones.  
- **Debugging:** proceso de encontrar y corregir errores en código.  
- Permite mejorar la **confiabilidad** y el **rendimiento** de sistemas y programas.

---

## 🔹 Tipos de Problemas Comunes

| Tipo de Error       | Descripción | Ejemplo |
|--------------------|------------|---------|
| Sintaxis (SyntaxError) | Error en la escritura del código | `print("Hola"` |
| Lógicos (LogicalError) | Código se ejecuta pero produce resultados incorrectos | `total = precio - descuento` (cuando debería ser suma) |
| Ejecución (RuntimeError) | Error que ocurre al correr el programa | `10 / 0` → `ZeroDivisionError` |

---

## 🔹 Pasos de Troubleshooting

1. **Identificar el problema**  
   - Observar síntomas, mensajes de error y comportamiento inesperado  
2. **Reproducir el problema**  
   - Definir pasos claros para replicarlo de manera consistente  
3. **Aislar la causa**  
   - Dividir el sistema en partes y probar cada componente  
4. **Aplicar solución**  
   - Cambios controlados y documentados  
5. **Verificar la corrección**  
   - Confirmar que el problema se resolvió y no hay efectos colaterales  

---

## 🔹 Herramientas y Técnicas

- Revisar **logs** del sistema o de la aplicación  
- Consola o terminal para pruebas rápidas  
- Python `try/except` para capturar y manejar errores  

```python
try:
    resultado = 10 / 0
except ZeroDivisionError:
    print("División por cero detectada")
````

* Documentación y referencias online
* Comunicación con el equipo para contextos complejos

---

## 📚 Referencias

* 🐍 [Python Docs – Errors and Exceptions](https://docs.python.org/3/tutorial/errors.html)
* 📘 [Real Python – Exception Handling](https://realpython.com/python-exceptions/)

