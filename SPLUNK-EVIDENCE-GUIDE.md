# Guía para reunir evidencias en Splunk

Usa primero búsquedas amplias. Si el laboratorio exige un índice o `sourcetype`, conserva el prefijo que ya aparezca en las búsquedas del playbook.

Antes de tomar cada captura:

1. Ajusta el rango de tiempo al período del escenario.
2. Deja visibles la consulta, la línea temporal y los campos principales.
3. Expande uno o dos eventos representativos.
4. Evita incluir pestañas, cuentas o información personal ajena al laboratorio.

## Escenario 1: onboarding legítimo

Busca por destinataria, remitente y dominio:

```spl
"j.garcia@thetrydaily.thm" OR "onboarding@hrconnex.thm" OR "hrconnex.thm"
```

Captura los resultados que permitan comprobar si hubo conexiones al dominio y si fueron permitidas o bloqueadas. Si no aparece actividad, captura también el resultado sin coincidencias junto con la consulta y el rango temporal.

## Escenario 2: phishing de Amazon

Actividad del equipo y del usuario:

```spl
"10.20.2.17" OR "h.harris@thetrydaily.thm"
```

URL, IP y remitente:

```spl
"bit.ly/3sHkX3da12340" OR "67.199.248.11" OR "urgents@amazon.biz"
```

En el evento importante deben verse, si existen, los campos equivalentes a hora, IP de origen, IP de destino, URL, puerto, acción y regla del firewall.

## Escenario 3: phishing de Microsoft

Actividad del equipo y del usuario:

```spl
"10.20.2.25" OR "c.allen@thetrydaily.thm"
```

Dominio, IP y remitente:

```spl
"m1crosoftsupport.co" OR "45.148.10.131" OR "no-reply@m1crosoftsupport.co"
```

Busca el evento que Splunk muestra a las `00:25:59.875` y captura los campos que demuestren la conexión permitida, especialmente la acción `allowed`, la regla `Allow-Internet`, el origen `10.20.2.25` y el destino `45.148.10.131`.

