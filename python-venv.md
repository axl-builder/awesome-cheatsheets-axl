# Cheatsheet: Entornos Virtuales en Python 3

## ¿Qué son?
Los entornos virtuales aíslan dependencias de Python por proyecto, evitando conflictos entre versiones de paquetes.

---

## venv (Incluido en Python 3.3+)

### Crear entorno virtual
```bash
python -m venv nombre_entorno
python3 -m venv nombre_entorno
```

### Activar entorno

**Linux/Mac:**
```bash
source nombre_entorno/bin/activate
```

**Windows:**
```cmd
nombre_entorno\Scripts\activate
```

**PowerShell:**
```powershell
nombre_entorno\Scripts\Activate.ps1
```

### Desactivar entorno
```bash
deactivate
```

### Eliminar entorno
```bash
rm -rf nombre_entorno  # Linux/Mac
rmdir /s nombre_entorno  # Windows
```

---

## virtualenv (Paquete externo)

### Instalar
```bash
pip install virtualenv
```

### Crear entorno
```bash
virtualenv nombre_entorno
virtualenv -p python3.9 nombre_entorno  # Versión específica
```

### Activar/Desactivar
Igual que con `venv`

---

## Gestión de Dependencias

### Instalar paquetes
```bash
pip install paquete
pip install paquete==1.2.3  # Versión específica
```

### Listar paquetes instalados
```bash
pip list
pip freeze
```

### Exportar dependencias
```bash
pip freeze > requirements.txt
```

### Instalar desde requirements.txt
```bash
pip install -r requirements.txt
```

### Actualizar paquete
```bash
pip install --upgrade paquete
```

### Desinstalar paquete
```bash
pip uninstall paquete
```

---

## Buenas Prácticas

✅ **Crear un entorno por proyecto**
✅ **Agregar el entorno al .gitignore**
```
venv/
env/
*.pyc
__pycache__/
```
✅ **Usar requirements.txt para compartir dependencias**
✅ **Activar el entorno antes de trabajar**
✅ **Nombrar el entorno como `venv`, `env` o `.venv`**

---

## Verificar entorno activo

### Ver qué Python se está usando
```bash
which python  # Linux/Mac
where python  # Windows
```

### Ver ubicación de pip
```bash
which pip  # Linux/Mac
where pip  # Windows
```

### Variable de entorno
```bash
echo $VIRTUAL_ENV  # Linux/Mac
echo %VIRTUAL_ENV%  # Windows
```

---

## Herramientas Avanzadas

### pipenv
Combina pip + virtualenv + requirements.txt
```bash
pip install pipenv
pipenv install paquete
pipenv shell
```

### poetry
Gestor moderno de dependencias
```bash
pip install poetry
poetry init
poetry add paquete
poetry shell
```

### conda
Para ciencia de datos
```bash
conda create -n nombre python=3.9
conda activate nombre
conda deactivate
```

---

## Troubleshooting

**Error al activar en PowerShell:**
```powershell
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
```

**Paquete no encontrado después de instalar:**
- Verifica que el entorno esté activado
- Confirma con `which python` o `where python`

**Conflictos de versiones:**
- Crea un entorno virtual nuevo y limpio
