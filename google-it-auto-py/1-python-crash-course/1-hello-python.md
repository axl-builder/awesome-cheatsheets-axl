Perfecto ✅ Con esos nombres podemos armar cada módulo como un bloque de cheatsheet bien estructurado y consistente con el estilo que venimos usando.

Arranquemos con **Módulo 1: Hello Python**:

---

````markdown
# 🐍 Python Cheatsheet – Crash Course on Python

> **Curso:** Crash Course on Python  
> **Módulo 1:** Hello Python  
> **Tema:** Primeros pasos con Python y ejecución de scripts

---

## 📘 Introducción

- Python es **interpretado**, de alto nivel y **tipado dinámico**.  
- Archivos Python → extensión `.py`  
- Bloques de código definidos por **indentación** (no `{}`)  
- Se puede ejecutar desde terminal/cmd:

```bash
python nombreArchivo.py
# o
python3 nombreArchivo.py
````

---

## 🔹 Tu Primer Programa

```python
print("Hello, Python!")
```

* `print()` → muestra texto o variables en pantalla
* Comentarios con `#`

---

## 🔹 Variables y Tipos de Datos

```python
x = 5           # int
pi = 3.14       # float
nombre = "Ana"  # str
activo = True   # bool
```

* Python **detecta automáticamente el tipo**
* No se necesita declarar el tipo explícitamente

---

## 🔹 Entrada del Usuario

```python
nombre = input("Ingresa tu nombre: ")
edad = int(input("Ingresa tu edad: "))
print(f"Hola {nombre}, tienes {edad} años")
```

* `input()` siempre retorna **string** → convertir si se necesita otro tipo
* F-strings para interpolación de variables: `f"{variable}"`

---

## 🔹 Operadores Básicos

| Operador | Función         |
| -------- | --------------- |
| +        | Suma            |
| -        | Resta           |
| *        | Multiplicación  |
| /        | División        |
| //       | División entera |
| %        | Módulo          |
| **       | Potencia        |

---

## 🔹 Buenas Prácticas Iniciales

* Escribir programas pequeños y probarlos frecuentemente
* Nombrar variables de forma descriptiva
* Usar comentarios claros
* Guardar y ejecutar scripts regularmente

---

## 📚 Referencias

* 🐍 [Python Docs – Getting Started](https://docs.python.org/3/tutorial/index.html)
* 📘 [Real Python – Beginner Guide](https://realpython.com/)

```

---