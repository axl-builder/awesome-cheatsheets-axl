# ☁️ **Cheatsheet – Cloud Services (Google IT Automation – Curso 5)**

### *Configuration Management and the Cloud*

---

## 📘 **1. Conceptos Fundamentales de Cloud Computing**

### 🔹 ¿Qué es la nube?

La **computación en la nube** permite usar recursos de TI (VMs, almacenamiento, redes, bases de datos, etc.) a través de Internet, sin administrar hardware directamente.

### 🔹 Ventajas clave

* **Escalabilidad**: crecer o reducir recursos bajo demanda.
* **Elasticidad**: ajuste automático según la carga.
* **Alta disponibilidad**: redundancia y failover.
* **Pago por uso**: sin inversiones iniciales.
* **Automatización**: scripts, APIs, herramientas como Puppet o Terraform.

### 🔹 Modelos de despliegue

* **IaaS**: Infraestructura como servicio (VMs, discos, redes).
* **PaaS**: Plataformas administradas (App Engine, Cloud SQL).
* **SaaS**: Software listo para usar (Gmail, Drive).

---

## 🧩 **2. Google Cloud Platform (GCP) – Componentes esenciales**

### 🔸 Compute Engine (VMs)

* Máquinas virtuales configurables.
* SSH remoto.
* Snapshots, imágenes, discos persistentes.

### 🔸 Cloud Storage

* Buckets.
* Versioning.
* Ciclo de vida de objetos.

### 🔸 Networking

* Firewalls.
* Reglas de acceso.
* IPs internas y externas.

### 🔸 Identity & Access Management (IAM)

* Roles: owner, editor, viewer, custom.
* Permisos granulares.

### 🔸 Logging & Monitoring

* Stackdriver / Cloud Logging.
* Métricas, alertas, paneles.

---

## 🗂️ **3. Administración de Configuración (Configuration Management)**

### 🔹 ¿Qué es CM?

Proceso para garantizar que **todos los sistemas mantengan un estado deseado**.
Evita la deriva y permite reproducibilidad.

### 🔹 Beneficios

* Configuraciones consistentes.
* Menos errores humanos.
* Reproducible en múltiples entornos.
* Automatización continua.

### 🔹 Herramientas

* **Puppet (enfoque principal del curso)**
* Chef
* Ansible
* Terraform (infraestructura)

---

## 🎭 **4. Puppet + Cloud: El flujo de trabajo**

1. **El agente envía facts** al master.
2. **El master compila el catálogo** usando facts + manifests.
3. **El catálogo se envía al agente.**
4. **El agente aplica el catálogo** y realiza cambios si son necesarios.
5. **El agente reporta resultados** al master.

### Archivos clave

* `/etc/puppetlabs/code/environments/production/manifests/site.pp`
* `/etc/puppetlabs/puppet/puppet.conf`
* Módulos: `/etc/puppetlabs/code/environments/production/modules/`

### Recursos Puppet más usados

* `file`
* `package`
* `service`
* `user`
* `group`
* `exec`

---

## 🧪 **5. Crear y administrar VMs (Compute Engine)**

### 🔹 Crear una VM

```bash
gcloud compute instances create vm1 --zone=us-east1-c --machine-type=e2-micro
```

### 🔹 Obtener la IP externa de una VM

```bash
gcloud compute instances describe vm1 \
  --zone=us-east1-c \
  --format='get(networkInterfaces[0].accessConfigs[0].natIP)'
```

### 🔹 Conectarse por SSH

```bash
ssh -i <CLAVE.pem> user@<IP>
```

### 🔹 Listar VMs

```bash
gcloud compute instances list
```

### 🔹 Eliminar una VM

```bash
gcloud compute instances delete vm1 --zone=us-east1-c
```

---

## 🔐 **6. Cloud IAM – Gestión de usuarios y permisos**

### Listar roles disponibles

```bash
gcloud iam roles list
```

### Añadir permisos a un usuario

```bash
gcloud projects add-iam-policy-binding myproject \
 --member="user:email@example.com" \
 --role="roles/compute.admin"
```

### Ver quién tiene acceso

```bash
gcloud projects get-iam-policy myproject
```

---

## 📦 **7. Storage – Buckets y objetos**

### Crear un bucket

```bash
gsutil mb gs://mi-bucket/
```

### Subir archivos

```bash
gsutil cp archivo.txt gs://mi-bucket/
```

### Descargar archivos

```bash
gsutil cp gs://mi-bucket/archivo.txt .
```

### Listar contenido

```bash
gsutil ls gs://mi-bucket/
```

### Eliminar archivo

```bash
gsutil rm gs://mi-bucket/archivo.txt
```

---

## 🔄 **8. Automatización en la nube (Python + APIs + Scripts)**

### Ejemplo: listar instancias desde Python

```python
from googleapiclient import discovery
compute = discovery.build('compute', 'v1')
instances = compute.instances().list(project='myproject', zone='us-east1-c').execute()
```

### Automatización típica

* Crear VMs automáticamente.
* Gestionar snapshots.
* Monitorear estado de instancias.
* Aplicar cambios masivos con Puppet.

---

## 🛠️ **9. Troubleshooting en la nube**

### Problemas comunes

| Problema                          | Solución                                                                      |
| --------------------------------- | ----------------------------------------------------------------------------- |
| No te podés conectar por SSH      | Verificar firewall, reglas de puertos, IP correcta, llave privada `chmod 600` |
| El Puppet agent no aplica cambios | `puppet agent -t` + verificar facts                                           |
| VM no responde                    | Reinicio, revisar logs, serial console                                        |
| Bucket no accesible               | Verificar IAM + políticas de objeto                                           |

### Logs importantes

* **Puppet**: `/var/log/puppetlabs/`
* **Compute Engine**: serial console
* **gcloud**: `~/.config/gcloud/logs/`

---

## 🧭 **10. Buenas prácticas**

* Usá **infraestructura como código** (Puppet, Terraform).
* Mantené entornos separados: dev / staging / production.
* Definí roles IAM mínimos necesarios.
* Automatizá backups y snapshots.
* Usá metadatos para inicializar VMs.
* Asegurate de borrar recursos para evitar costos.

---

## 📚 **Recursos del curso**

* Google IT Automation – Curso 5
* Documentación Puppet
* Documentación Google Cloud
* Laboratorios Qwiklabs / SkillsBoost

