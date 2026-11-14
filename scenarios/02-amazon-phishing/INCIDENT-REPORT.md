# Incident Report — Alerts 8815 and 8816

**Time of Activity:** 11/13/2026 23:25:29 (email) and 11/13/2026 23:26:43 (firewall)

**List of Affected Entities:**

- Usuario / Recipient: `h.harris@thetrydaily.thm`
- Workstation / Source IP: `10.20.2.17`
- Sender: `urgents@amazon.biz`
- Destination IP: `67.199.248.11`

**Reason for Classifying as True Positive:** El usuario (`h.harris@thetrydaily.thm`) recibió un correo de phishing que suplantaba a Amazon desde `urgents@amazon.biz` y contenía una URL acortada (`http://bit.ly/3sHkX3da12340`). Aproximadamente un minuto después, el host `10.20.2.17` generó una petición HTTP hacia la URL y la IP de destino `67.199.248.11`, incluida en la blacklist. El firewall identificó la conexión y la bloqueó mediante la regla `Blocked Websites`, confirmando que el usuario interactuó con el enlace malicioso.

**Reason for Escalating the Email Alert (8815):** La alerta de correo requirió escalamiento porque el usuario hizo clic en el enlace. Era necesario correlacionar la actividad con los registros de firewall, comprobar si otros usuarios habían recibido la misma campaña y descartar exposición de credenciales o descargas maliciosas.

**Reason for Not Escalating the Correlated Firewall Alert (8816):** No se requiere un escalamiento adicional a Nivel 2 para la alerta de firewall porque la conexión fue bloqueada correctamente (`Action: blocked`) y la revisión de los eventos del host `10.20.2.17` no mostró actividad maliciosa posterior. La alerta quedó contenida y correlacionada con el incidente de correo 8815.

**Recommended Remediation Actions:**

- Mantener bloqueadas la URL `http://bit.ly/3sHkX3da12340` y la IP `67.199.248.11` en firewalls y proxies.
- Bloquear el remitente `urgents@amazon.biz` en el email gateway.
- Eliminar el correo de phishing de la bandeja de `h.harris@thetrydaily.thm` y de otros posibles destinatarios.
- Buscar otros mensajes que compartan remitente, asunto, URL o infraestructura.
- Mantener monitoreo temporal sobre el host `10.20.2.17`.
- Realizar concientización de seguridad con el usuario `h.harris`.

**List of Attack Indicators:**

- Malicious URL: `http://bit.ly/3sHkX3da12340`
- Destination IP: `67.199.248.11`
- Sender Email: `urgents@amazon.biz`
- Sender Domain: `amazon.biz`
- Email Subject: `Your Amazon Package Couldn't Be Delivered – Action Required`
- Source IP: `10.20.2.17`

