# Estructura del Laboratorio:

lab-cybersec/
├─ README.md
├─ LICENSE
├─ .gitignore
├─ docker-compose.yml
├─ nginx/
│  ├─ nginx.conf
│  ├─ sites-enabled/
│  │  └─ default.conf
│  └─ modsecurity/
│     ├─ modsecurity.conf
│     └─ crs/   (submodule / instructions to clone OWASP CRS)
├─ app/
│  ├─ index.php
│  └─ dockerfile
├─ db/
│  ├─ init_db.sql
│  └─ dockerfile (opcional)
├─ scripts/
   ├─ ufw-setup.sh
   ├─ tailscale-install.sh
   ├─ generate-auth-key-instructions.md
   └─ post-deploy-checks.sh

# Laboratorio Virtual de Ciberseguridad — Prototipo TRL-3 (Simulado)

Repositorio para el prototipo virtual del proyecto de grado — Fase 4 (Desarrollo de la propuesta ingenieril).
Incluye servicios para: Perímetro (UFW), Proteccion Web (Nginx + ModSecurity), Aplicación PHP y PostgreSQL (datos).

> **Aviso:** este repositorio incluye scripts y configuraciones tanto para **simulación** (docker-compose) como para **instalación en VM** (scripts bash). En el informe principal se declara la naturaleza simulada de las evidencias.

## Contenido
- `docker-compose.yml` — Levanta Nginx (WAF), PHP-FPM app y PostgreSQL.
- `nginx/` — Configuración de Nginx y ModSecurity (CRS).
- `app/` — Aplicación PHP mínima que consulta la base `seguridad_ciudadana`.
- `db/init_db.sql` — SQL de inicialización con datos de prueba.
- `scripts/ufw-setup.sh` — Script para configurar UFW en la VM perimetral (Edwin).
- `scripts/tailscale-install.sh` — Guía y script para instalar Tailscale en VMs.
- `docs/` — Recursos, evidencia simulada y notas.

## Requisitos
- Docker & docker-compose (para ejecución local simulada).
- En despliegue real: 3 VMs Ubuntu Server (Edwin, Sergio, José) con acceso a Internet.
