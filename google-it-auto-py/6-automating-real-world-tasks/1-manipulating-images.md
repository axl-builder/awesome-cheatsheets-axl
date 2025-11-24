> 💼 **Course 6 – Automating Real-World Tasks with Python**

Y vamos módulo por módulo, en el mismo formato profesional que las anteriores.
Arrancamos con el primero 👇

---

````markdown
# 🖼️ Automating Real-World Tasks with Python – Cheatsheet  
## Módulo 1: Manipulating Images

---

## 🎯 Introducción

En este módulo aprenderás a **procesar, editar y automatizar tareas con imágenes** utilizando Python.  
Esto incluye redimensionar, rotar, convertir formatos y preparar imágenes para uso web o informes automatizados.

---

## 🧰 Herramienta principal: PIL / Pillow

El módulo usa la librería **Pillow** (una mejora moderna de PIL - Python Imaging Library).

### Instalación
```bash
pip install pillow
````

### Importación

```python
from PIL import Image
```

---

## 🧠 Conceptos clave

### 📂 Abrir una imagen

```python
img = Image.open("foto.jpg")
img.show()
```

### 💾 Guardar una imagen

```python
img.save("nueva_foto.png")
```

> Podés cambiar el formato automáticamente según la extensión.

### 🔄 Conversión de formatos

```python
img = Image.open("foto.jpg").convert("RGB")
img.save("foto_convertida.png")
```

### 📏 Redimensionar imágenes

```python
nueva = img.resize((128, 128))
nueva.save("foto_redimensionada.jpg")
```

### 🔃 Rotar o voltear

```python
rotada = img.rotate(90)     # grados
invertida = img.transpose(Image.FLIP_LEFT_RIGHT)
```

### 🧩 Recortar (Crop)

```python
caja = (100, 100, 400, 400)
recorte = img.crop(caja)
```

---

## 🖼️ Procesamiento por lotes (Batch Processing)

Automatizar tareas con múltiples archivos:

```python
import os
from PIL import Image

ruta = "imagenes/"
for archivo in os.listdir(ruta):
    if archivo.endswith(".jpg"):
        img = Image.open(os.path.join(ruta, archivo))
        img = img.resize((128, 128)).convert("RGB")
        img.save(f"{ruta}/procesadas/{archivo}.png")
```

> 💡 Ideal para generar versiones web de imágenes o preparar datasets.

---

## 🔍 Metadatos

Algunas imágenes contienen información adicional (EXIF):

```python
from PIL import ExifTags

for etiqueta, valor in img._getexif().items():
    if etiqueta in ExifTags.TAGS:
        print(f"{ExifTags.TAGS[etiqueta]}: {valor}")
```

---

## ⚙️ Errores comunes

| Error                                 | Causa                              | Solución                                         |
| ------------------------------------- | ---------------------------------- | ------------------------------------------------ |
| `OSError: cannot identify image file` | Archivo corrupto o ruta incorrecta | Verificar extensión y path                       |
| Imagen deformada al redimensionar     | Cambia la proporción original      | Usar `thumbnail()` o calcular escala manualmente |

---

## 💡 Tips profesionales

* Usar `os.path` o `pathlib` para compatibilidad entre SOs.
* Combinar Pillow con **automation scripts** para procesar miles de imágenes.
* Integrar con **APIs o PDF generators** para informes visuales.

---

## 📚 Referencias

* 🧩 [Pillow Documentation](https://pillow.readthedocs.io/en/stable/)
* 🧰 [Image Module Reference](https://pillow.readthedocs.io/en/stable/reference/Image.html)
* 🪄 [Working with EXIF Data](https://pillow.readthedocs.io/en/stable/reference/Image.html#PIL.Image.Image._getexif)

