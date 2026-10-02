# 🛡️ Wazuh SIEM + n8n: Automatización SOAR y Respuesta a Incidentes

Este repositorio contiene flujos de trabajo (workflows) de **n8n** diseñados para funcionar como una capa ligera de **SOAR (Security Orchestration, Automation, and Response)** integrada con **Wazuh SIEM/XDR**. 

El objetivo del proyecto es automatizar la detección, el filtrado de falsos positivos y la notificación en tiempo real de incidentes críticos en entornos de **Active Directory / Windows Server**, así como la generación de reportes periódicos de vulnerabilidades (Threat Hunting) utilizando **Telegram** y **Correo Electrónico (SMTP)**.

---

## 🏗️ Arquitectura de la Solución

```text
+-------------------+       Webhook (JSON)       +-------------------+      Filtro / Reglas     +------------------------+
|                   | -------------------------> |                   | -----------------------> |  Alertas en Tiempo Real|
|   Wazuh Manager   |                            |   n8n Automation  |                          |  (Telegram & Email)    |
|  & Wazuh Indexer  | <------------------------- |     Platform      | -----------------------> +------------------------+
|                   |     Consulta API / SSH     |                   |    Cron / Programado     |  Reporte Diario CVEs   |
+-------------------+                            +-------------------+                          |  (HTML Email Report)   |
                                                                                                +------------------------+
