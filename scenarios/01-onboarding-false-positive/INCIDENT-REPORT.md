# Incident Report — Alerts 8814 and 8818

**Time of Activity:** 11/13/2026 23:22:16 and 11/13/2026 23:28:15

**List of Related Entities:**

- Usuario / Recipient: `j.garcia@thetrydaily.thm`
- Sender: `onboarding@hrconnex.thm`
- Subject: `Action Required: Finalize Your Onboarding Profile`
- URL: `https://hrconnex.thm/onboarding/15400654060/j.garcia`
- Related alerts: `8814`, `8818`

**Reason for Classifying as False Positive:** Las alertas se generaron porque dos correos entrantes dirigidos a `j.garcia@thetrydaily.thm` contenían un enlace externo. El remitente y la URL utilizaban el mismo dominio (`hrconnex.thm`), no había archivos adjuntos y no se identificaron redirecciones ni suplantación. Además, un correo interno enviado por `h.harris@thetrydaily.thm` confirmó que `hrconnex.thm` era el nuevo proveedor externo de Recursos Humanos encargado de la configuración de cuentas y documentación de incorporación. Por lo tanto, los mensajes eran comunicaciones legítimas de onboarding.

**Reason for Not Escalating the Alert:** No se requiere escalamiento debido a que el contexto empresarial fue validado mediante comunicaciones internas y no se identificaron indicadores maliciosos. Las alertas 8814 y 8818 contienen el mismo remitente, destinataria, asunto y URL, por lo que deben correlacionarse como eventos repetidos del mismo proceso legítimo.

**List of Related Indicators:**

- Sender Email: `onboarding@hrconnex.thm`
- Sender Domain: `hrconnex.thm`
- URL: `https://hrconnex.thm/onboarding/15400654060/j.garcia`
- Email Subject: `Action Required: Finalize Your Onboarding Profile`
- Recipient: `j.garcia@thetrydaily.thm`

