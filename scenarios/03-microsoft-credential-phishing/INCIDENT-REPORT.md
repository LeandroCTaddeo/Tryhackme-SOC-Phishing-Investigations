# Incident Report — Alert 8817

**Time of Activity:** 11/13/2026 23:27:47

**List of Affected Entities:**

- Usuario / Recipient: `c.allen@thetrydaily.thm`
- Workstation IP: `10.20.2.25`

**Reason for Classifying as True Positive:** El usuario (`c.allen@thetrydaily.thm`) recibió un correo de phishing para robo de credenciales que suplantaba a Microsoft desde un dominio falso (`no-reply@m1crosoftsupport.co`). El dominio reemplazaba la letra `i` por el número `1`. A las 23:28:56, el usuario hizo clic en el enlace malicioso (`https://m1crosoftsupport.co/login`) y el firewall permitió la conexión saliente HTTPS (`Action: allowed`) mediante la regla `Allow-Internet` desde el host `10.20.2.25` hacia `45.148.10.131`.

**Reason for Escalating the Alert:** El acceso permitido a una página falsa de inicio de sesión crea un riesgo alto de compromiso de credenciales. Se requiere escalamiento inmediato para determinar si el usuario introdujo información, forzar el cambio de contraseña, revocar sesiones activas e investigar el endpoint `10.20.2.25` ante un posible acceso no autorizado o descarga de contenido malicioso.

**Recommended Remediation Actions:**

- Restablecer inmediatamente la contraseña y revocar todas las sesiones y tokens activos del usuario `c.allen@thetrydaily.thm`.
- Verificar y aplicar Multi-Factor Authentication (MFA) en la cuenta de `c.allen` y revisar los registros de autenticación en busca de inicios de sesión sospechosos.
- Bloquear el dominio `m1crosoftsupport.co`, la URL `https://m1crosoftsupport.co/login` y la IP de destino `45.148.10.131` en todos los firewalls y proxies web.
- Bloquear al remitente `no-reply@m1crosoftsupport.co` y eliminar el correo de todas las bandejas de entrada de la organización.
- Aislar y escanear el host `10.20.2.25` para descartar la descarga de malware secundario.

**List of Attack Indicators:**

- Sender Email: `no-reply@m1crosoftsupport.co`
- Malicious Domain: `m1crosoftsupport.co`
- Malicious URL: `https://m1crosoftsupport.co/login`
- Destination IP: `45.148.10.131`
- Email Subject: `Unusual Sign-In Activity on Your Microsoft Account`
- Spoofed IP en el cuerpo del correo: `102.89.222.143`
- Source IP: `10.20.2.25`

