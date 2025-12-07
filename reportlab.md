

# 📄 **ReportLab Cheatsheet — Generación de PDFs en Python**

> **Librería:** `reportlab`
> **Uso principal:** Crear PDFs programáticamente usando Python
> **Componentes clave:** Platypus (layout), estilos, tablas, imágenes, gráficos

---

## 🧱 **Estructura Básica de un PDF con ReportLab**

```python
from reportlab.platypus import SimpleDocTemplate, Paragraph, Spacer
from reportlab.lib.styles import getSampleStyleSheet

doc = SimpleDocTemplate("output.pdf")   # Nombre del archivo
styles = getSampleStyleSheet()          # Estilos predefinidos

story = []                              # Lista de elementos

story.append(Paragraph("Título del PDF", styles["Title"]))
story.append(Spacer(1, 12))             # Espaciador

doc.build(story)                        # Genera el PDF
```

---

## 🎨 **Estilos (Styles)**

```python
styles = getSampleStyleSheet()
title = styles["Title"]
normal = styles["Normal"]
heading = styles["Heading1"]
```

Crear un estilo personalizado:

```python
from reportlab.lib.styles import ParagraphStyle
from reportlab.lib.enums import TA_CENTER

custom_style = ParagraphStyle(
    name='CenteredStyle',
    parent=styles['Normal'],
    fontSize=14,
    alignment=TA_CENTER
)
```

---

## 🔤 **Paragraph (Texto en formato HTML simple)**

ReportLab soporta una especie de *mini HTML*:

```python
Paragraph("<b>Negrita</b> y <i>Cursiva</i>", styles["Normal"])
Paragraph("Texto con salto de línea<br/>otra línea.", styles["Normal"])
Paragraph("Lista:<br/>• Item 1<br/>• Item 2", styles["Normal"])
```

---

## 🧱 **Spacer (Espaciado vertical)**

```python
from reportlab.platypus import Spacer

Spacer(width=1, height=12)   # 12 puntos ≈ 1 línea
```

---

## 🖼️ **Insertar Imágenes**

```python
from reportlab.platypus import Image

img = Image("ruta/imagen.png", width=200, height=150)
story.append(img)
```

---

## 📊 **Tablas (Table)**

```python
from reportlab.platypus import Table, TableStyle
from reportlab.lib import colors

data = [
    ["Producto", "Cantidad", "Precio"],
    ["CPU", "3", "$300"],
    ["RAM", "8GB", "$80"]
]

table = Table(data)

table.setStyle(TableStyle([
    ('BACKGROUND', (0,0), (-1,0), colors.grey),
    ('TEXTCOLOR', (0,0), (-1,0), colors.white),
    ('ALIGN',(0,0),(-1,-1),'CENTER'),
    ('GRID', (0,0), (-1,-1), 1, colors.black)
]))
```

---

## 🥧 **Gráficos (Charts) — Pie Chart**

```python
from reportlab.graphics.shapes import Drawing
from reportlab.graphics.charts.piecharts import Pie

drawing = Drawing(200, 150)
pie = Pie()

pie.data = [15, 30, 45, 10]
pie.labels = ["A", "B", "C", "D"]

drawing.add(pie)

story.append(drawing)
```

---

## 🏗️ **Construcción Final del PDF**

```python
doc = SimpleDocTemplate("reporte.pdf")

story = [
    Paragraph("Reporte de Inventario", styles["Title"]),
    Spacer(1, 20),
    table,
    Spacer(1, 20),
    drawing
]

doc.build(story)
```

---

## 🔧 **Configuración de Página**

```python
from reportlab.lib.pagesizes import letter, A4

doc = SimpleDocTemplate("archivo.pdf", pagesize=A4)
```

Unidades útiles:

```python
from reportlab.lib.units import inch, cm

1 * inch   # 72 puntos
1 * cm     # 28.34 puntos
```

---

## 📌 **Usos Comunes**

### ✔ Crear reportes automáticos

### ✔ Insertar gráficos simples

### ✔ Generar documentos con tablas

### ✔ PDF generado desde scripts (como en los labs)

---

## 🧪 **Ejemplo “Estilo Lab de Google”**

```python
from reportlab.platypus import SimpleDocTemplate, Paragraph, Spacer, Table
from reportlab.lib.styles import getSampleStyleSheet

report = SimpleDocTemplate("/tmp/report.pdf")
styles = getSampleStyleSheet()

title = "A Complete Inventory of My Computer"
paragraph = Paragraph(title, styles["h1"])

table_data = [["ID", "Name", "Value"],
              [1, "CPU", "$300"],
              [2, "RAM", "$80"]]
table = Table(table_data)

story = [paragraph, Spacer(1, 20), table]

report.build(story)
```

