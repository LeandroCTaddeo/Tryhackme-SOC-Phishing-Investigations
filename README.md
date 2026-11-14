# TryHackMe SOC Investigation Portfolio

Documentación de escenarios investigados en un laboratorio SOC de TryHackMe. El objetivo de este repositorio es mostrar el proceso de triage, correlación de eventos, clasificación y respuesta ante alertas de seguridad.

> Los dominios, usuarios, direcciones IP y eventos pertenecen a un entorno de laboratorio.

## Escenarios

| Escenario | Alertas | Clasificación | Resultado |
|---|---:|---|---|
| [Correo legítimo de onboarding](scenarios/01-onboarding-false-positive/README.md) | 8814 y 8818 | Falso positivo | Dominio y URL legítimos; alertas correlacionadas |
| [Phishing de Amazon y bloqueo de firewall](scenarios/02-amazon-phishing/README.md) | 8815 y 8816 | Verdadero positivo | El usuario hizo clic; la conexión fue bloqueada |
| [Robo de credenciales mediante suplantación de Microsoft](scenarios/03-microsoft-credential-phishing/README.md) | 8817 | Verdadero positivo | El usuario accedió al sitio; conexión permitida y escalada |

## Estructura del repositorio

```text
tryhackme-soc-portfolio/
├── README.md
├── SPLUNK-EVIDENCE-GUIDE.md
└── scenarios/
    ├── 01-onboarding-false-positive/
    │   ├── README.md
    │   ├── INCIDENT-REPORT.md
    │   └── evidence/
    ├── 02-amazon-phishing/
    │   ├── README.md
    │   ├── INCIDENT-REPORT.md
    │   └── evidence/
    └── 03-microsoft-credential-phishing/
        ├── README.md
        ├── INCIDENT-REPORT.md
        └── evidence/
```

Cada `README.md` explica la investigación y presenta las evidencias. Cada `INCIDENT-REPORT.md` reproduce el formato operativo utilizado para cerrar la alerta en el SOC.

## Metodología

1. Revisión de los datos del correo y sus indicadores.
2. Análisis del remitente, dominio, URL y técnicas de ingeniería social.
3. Búsqueda de actividad relacionada en los registros de firewall o proxy.
4. Correlación por usuario, equipo, URL, IP y tiempo.
5. Clasificación como verdadero o falso positivo.
6. Escalamiento y recomendaciones de remediación.

## Herramientas utilizadas

- SIEM y búsqueda de eventos: Splunk
- Gestión y análisis de alertas: laboratorio SOC de TryHackMe
- Fuentes de telemetría: correo electrónico y firewall

