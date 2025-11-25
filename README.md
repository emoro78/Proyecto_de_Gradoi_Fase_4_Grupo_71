# Laboratorio Virtual de Ciberseguridad  
**Arquitectura Conceptual para la Gestión de Datos Sensibles**  
**Secretaría de Informática – Alcaldía de Funza, Cundinamarca**  
**Proyecto de Grado – Ingeniería de Sistemas – UNAD**  
Octubre 2024  

**Autores:**  
- Edwin Montoya Romero  
- José Argemiro Romero Suárez  
- Sergio Quintero Cuervo  
**Tutor:** Rubén Darío Ordóñez Mantilla  

---

### Descripción del Repositorio
Este repositorio contiene la **prueba de concepto funcional (TRL 3)** del laboratorio virtual desarrollado en la **Fase 4** del proyecto de grado.  
Se implementó una arquitectura de ciberseguridad 100 % con software libre y costo $0 COP, utilizando tres máquinas virtuales Ubuntu Server 24.04 interconectadas mediante una red privada Tailscale (VPN basada en WireGuard).

### Objetivo del Laboratorio
Validar de forma práctica la viabilidad técnica de la arquitectura conceptual propuesta en la Fase 3, demostrando:
- Control perimetral con firewall estricto  
- Protección en capa de aplicación (WAF + Reverse Proxy)  
- Almacenamiento seguro de datos sensibles (PostgreSQL con acceso restringido)  
- Comunicación cifrada punto a punto entre todos los nodos  

### Topología del Laboratorio
```
Internet
   └── Tailscale VPN (red 100.64.0.0/10)
        ├── VM1 – Firewall Perimetral        (Edwin Montoya)       → 100.x.x.10
        ├── VM2 – WAF + Reverse Proxy        (Sergio Quintero)     → 100.x.x.20
        └── VM3 – Base de Datos Segura       (José Romero)         → 100.x.x.30
```

### Estructura del Repositorio
```
cybersec-funza-lab/
├── README.md                        ← Este archivo
├── firewall/                        ← Componente Edwin Montoya
│   ├── configure_firewall.sh
│   └── screenshots/
├── waf-reverse-proxy/               ← Componente Sergio Quintero
│   ├── configure_waf.sh
│   ├── nginx.conf
│   └── screenshots/
├── database/                        ← Componente José Romero
│   ├── configure_postgresql.sh
│   ├── create_secure_db.sql
│   └── screenshots/
├── video_demo/
│   └── demo_laboratorio.mp4         ← Video explicativo completo
└── docs/
    └── Informe_Fase4_Resumen.pdf    ← Resumen oficial de la fase 4
```

### Requisitos Previos
- VirtualBox, VMware o cualquier hipervisor  
- 3 máquinas virtuales con Ubuntu Server 24.04 LTS  
- Conexión a internet (solo para instalación inicial)  
- Clave de autenticación Tailscale (se genera gratis en https://login.tailscale.com)

### Cómo Replicar el Laboratorio (paso a paso)

1. **Crear las 3 VMs** con Ubuntu Server 24.04 (mínimo 1 GB RAM cada una)
2. **En cada VM**, instalar y conectar Tailscale:
   ```bash
   curl -fsSL https://tailscale.com/install.sh | sh
   sudo tailscale up --auth-key=TU_CLAVE_GENERADA
   ```
3. **Ejecutar el script correspondiente** en cada máquina:
   - VM Firewall → `firewall/configure_firewall.sh`
   - VM WAF → `waf-reverse-proxy/configure_waf.sh`
   - VM Base de datos → `database/configure_postgresql.sh`

¡En menos de 15 minutos tendrás el laboratorio 100 % funcional!

### Video Demostrativo Completo
[Ver en YouTube → https://youtu.be/kg4cvf1tewM](https://youtu.be/kg4cvf1tewM)

### Tecnologías Utilizadas (100 % Open Source – Costo $0)
| Componente               | Herramienta utilizada               |
|--------------------------|-------------------------------------|
| Firewall perimetral      | UFW + reglas estrictas              |
| Red privada segura       | Tailscale (WireGuard)               |
| WAF + Reverse Proxy      | Nginx + ModSecurity + OWASP CRS     |
| Base de datos segura     | PostgreSQL 16 + cifrado + pg_hba    |

### Resultados Alcanzados
- Comunicación cifrada entre todas las máquinas  
- Bloqueo efectivo de inyecciones SQL y XSS por el WAF  
- Acceso a la base de datos solo desde red Tailscale  
- Trazabilidad completa del tráfico  
- Replicable en cualquier entidad pública sin inversión económica  

### Licencia
**MIT License** – Uso libre con fines académicos, investigativos y gubernamentales.  
Se permite la réplica total o parcial citando a los autores y a la UNAD.

**¡Listo para descargar, ejecutar y presentar en la sustentación!**  
Éxitos con la defensa del proyecto de grado – este laboratorio es la prueba irrefutable de que la propuesta no solo es teórica, sino completamente viable y funcional.
