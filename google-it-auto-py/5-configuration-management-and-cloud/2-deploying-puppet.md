# 🧩 Deploying Puppet – Cheatsheet

> **Curso:** Configuration Management and the Cloud  
> **Módulo 2:** Deploying Puppet  

---

## 📘 Introducción

**Puppet** es una herramienta de *Configuration Management* que automatiza la configuración y el mantenimiento de sistemas.  
Utiliza un **modelo declarativo** (definís *qué* querés, no *cómo hacerlo*).  

---

## ⚙️ Arquitectura de Puppet

| Componente | Descripción |
|-------------|-------------|
| **Puppet Master (Server)** | Servidor central que almacena los *manifests* y gestiona nodos |
| **Puppet Agent (Client)** | Se ejecuta en cada máquina cliente y aplica las configuraciones |
| **Catalog** | Archivo generado por el master con las configuraciones a aplicar en cada nodo |
| **Facts** | Datos sobre el sistema del agente (OS, IP, RAM, etc.) recolectados automáticamente |
| **Manifests** | Archivos `.pp` donde se definen configuraciones declarativas |

---

## 🔹 Flujo de Ejecución

1. El **agente** envía un reporte de *facts* al **master**  
2. El **master** compila un *catalog* según los facts y los *manifests*  
3. El **agente** aplica los cambios necesarios para cumplir el catálogo  
4. El **agente** envía un *report* de resultados al **master**

```text
Agent → Facts → Master → Catalog → Agent → Report
````

---

## 🧱 Archivos y Estructura

| Archivo / Carpeta               | Descripción                        |
| ------------------------------- | ---------------------------------- |
| `/etc/puppet/`                  | Configuración general              |
| `/etc/puppet/manifests/site.pp` | Archivo principal de configuración |
| `/etc/puppet/modules/`          | Contiene módulos reutilizables     |

---

## 🧩 Ejemplo de Manifest

```puppet
# site.pp
node default {
  package { 'nginx':
    ensure => installed,
  }

  service { 'nginx':
    ensure => running,
    enable => true,
  }

  file { '/var/www/html/index.html':
    ensure  => file,
    content => "Hello from Puppet!",
  }
}
```

🪄 **Qué hace:**

* Instala **nginx**
* Asegura que esté activo y se inicie automáticamente
* Crea un archivo HTML con contenido

---

## 🧰 Comandos Básicos de Puppet

| Comando                          | Descripción                                                |
| -------------------------------- | ---------------------------------------------------------- |
| `puppet apply manifest.pp`       | Aplica un manifest local sin usar master                   |
| `puppet agent -t`                | Ejecuta el agente y aplica configuraciones desde el master |
| `puppet config print all`        | Muestra configuración actual de Puppet                     |
| `puppet module install <nombre>` | Instala un módulo desde Puppet Forge                       |
| `puppet resource <tipo>`         | Muestra o modifica recursos en el sistema                  |

---

## 🔐 Seguridad y Certificados

* Puppet usa **SSL** para autenticar agentes y masters
* Cada agente necesita firmar su certificado en el master

```bash
# En el master:
puppetserver ca list          # Ver certificados pendientes
puppetserver ca sign <certname>  # Firmar certificado
```

---

## 📦 Módulos Puppet

* Un **módulo** agrupa manifests, archivos y plantillas para una función específica.
* Estructura típica:

```
mymodule/
 ├── manifests/
 │   └── init.pp
 ├── files/
 ├── templates/
 ├── README.md
```

Usar en `site.pp`:

```puppet
include mymodule
```

---

## 📚 Referencias

* 📘 [Puppet Official Docs](https://puppet.com/docs/puppet/latest/puppet_index.html)
* 🧱 [Puppet Forge Modules](https://forge.puppet.com/)
* 🐧 [Puppet SSL and Certificates](https://puppet.com/docs/puppet/latest/ssl_and_certificates.html)
