# Proyecto: Técnicas de Persistencia en Metasploitable3

**Autor:** Álvaro Martínez Cutillas  
**Tipo:** Práctica ofensiva – Post-explotación en Linux

---

## Descripción

Este proyecto documenta diferentes técnicas de persistencia aplicadas en un entorno Linux vulnerable (Metasploitable3). Se utilizaron diversos vectores como servicios del sistema, tareas programadas (cron) y archivos de inicialización de sesión (`.bashrc`) para mantener el acceso remoto persistente hacia el atacante.

---

## Herramientas y tecnologías

- **Kali Linux** (atacante)
- **Metasploitable3** (víctima)
- Shell inversas TCP (`bash`, `/dev/tcp/`)
- Servicios personalizados (`Upstart`)
- Tareas programadas (`cron`)
- Archivos `.bashrc` modificados

---

## Técnicas de Persistencia Implementadas

### 1. Servicio personalizado con Upstart

- Creación de un archivo en `/etc/init/persistente.conf`
- Ejecución de shell inversa persistente al iniciar el sistema
- Difícil de detectar sin monitoreo de servicios

### 2. Cron Job malicioso

- Modificación del `crontab` de root
- Ejecución periódica de shell inversa cada minuto
- Alta efectividad y persistencia

### 3. Modificación de `.bashrc`

- Inserción de comando malicioso en archivo `.bashrc`
- Conexión inversa automática al iniciar sesión el usuario
- Muy simple, pero efectivo y fácil de pasar desapercibido

---

## Impacto

Estas técnicas simulan métodos reales utilizados por actores maliciosos para mantener el control de sistemas vulnerables. Se demostró la capacidad de establecer persistencia sin dejar rastros evidentes, lo cual enfatiza la importancia del monitoreo activo, el control de integridad y las auditorías regulares en sistemas Linux.

---

## Contramedidas recomendadas

- Monitorear `/etc/init/` y crontabs del sistema
- Inspeccionar archivos `.bashrc` de usuarios
- Implementar herramientas como `auditd` y `chkrootkit`
- Uso de SIEM para correlación de eventos sospechosos

------




##  Nota

Este proyecto fue desarrollado exclusivamente con fines educativos y se ejecutó en un entorno de laboratorio simulado. No representa una actividad real de intrusión.
Este proyecto fue realizado como parte de un proceso formativo. La máquina analizada es de acceso público y el contenido aquí compartido es de elaboración propia, con fines educativos y demostrativos.

