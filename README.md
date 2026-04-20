# agente-eficiencia-energetica

# 🤖 Agente de IA: Consultor de Eficiencia Energética

<img width="3052" height="1202" alt="image" src="https://github.com/user-attachments/assets/61769437-e70e-477f-bb4d-ff273e8e59e2" />


Este proyecto nace como una solución inteligente para equilibrar el ahorro económico y la salud ambiental en el hogar. Utilizando un agente de IA avanzado, el sistema monitoriza en tiempo real la meteorología y el mercado eléctrico para enviar protocolos de actuación personalizados.

## 🚀 La Misión
El objetivo es democratizar la eficiencia energética, permitiendo que el hogar se gestione bajo estándares de la OMS (confort térmico entre 18°C y 24°C) sin que el usuario tenga que analizar tablas complejas de precios o mapas meteorológicos.

## ⏱️ Programación Crítica (Estabilidad del Sistema)
El flujo está calibrado específicamente para garantizar la disponibilidad de los datos y la estabilidad de la IA:

Ejecución diaria a las 21:00: Se ha fijado esta hora para evitar los picos de demanda en los servidores de IA que suelen causar el error 503 (High Demand) detectado durante la franja de las 20:00.

Sincronización con REE: A las 21:00, los precios del PVPC para el día siguiente ya están publicados, permitiendo que la consulta {{ $now.plus({ days: 1 }) }} obtenga la información necesaria de Red Eléctrica.

## 📍 Personalización: Tu Municipio
Para que el agente analice el clima de tu zona, debes actualizar el código de municipio en el nodo Obtencion_URL_AEMET.

¿Cómo encontrar el código de tu municipio?
Ve a la web oficial de AEMET y busca tu municipio en el buscador de predicción.

Una vez en la página de predicción por horas de tu municipio, observa la URL del navegador.

El código necesario es el número que aparece al final de la URL, justo después de las letras "id".

Ejemplo: Para Argés (Toledo), la URL es .../municipios/horas/arges-id45016, por lo que el código es 45016.

Sustituye ese número en el campo URL del primer nodo del flujo: https://opendata.aemet.es/.../municipio/horaria/TU_CODIGO.

## 🛠️ Pila Tecnológica
Cerebro (LLM): Google Gemini (Modelo Flash para máxima eficiencia y ahorro de cuota).

Orquestación (Workflow): n8n (Low-Code/Agentic).

Fuentes de Datos: * AEMET: Predicción horaria técnica personalizada por código de municipio.

REE (ESIÓS): Precios de la luz en tiempo real.

Interfaz de Salida: Telegram Bot (Formato HTML estricto para evitar errores de parseo).

## 📋 Configuración y Requisitos
1. Obtención de Tokens
AEMET: Solicita tu clave API en su Centro de Descargas.

Google Gemini: Crea tu API Key en Google AI Studio.

Telegram: Crea tu bot con @BotFather.

2. Conexión con REE (ESIÓS)
El nodo de Red Eléctrica utiliza el token público de la web oficial. Para configuraciones avanzadas, consulta la documentación de ESIÓS, teniendo en cuenta que la configuración del nodo podría variar según las actualizaciones de su API pública.



## 📊 Ejemplo de Informe Generado
A continuación, se muestra un ejemplo real del protocolo que el agente envía cada noche a través de Telegram:

📍 Argés (Toledo) | 2026-04-21
☀️ CICLO SOLAR: 07:30 - 21:00

🌡️ ANÁLISIS TÉRMICO Y SALUD (OMS):

❄️ Zona de Infraconfort (inferior a 18°C): 02:00-09:00. T. mín 13°C. Riesgo respiratorio.

✨ Zona de Confort (18-24°C): 00:00-01:00, 10:00-11:00, 20:00-23:00. Rango ideal.

🔥 Zona de Estrés Térmico (superior a 24°C): 12:00-19:00. T. máx 30°C. Riesgo de fatiga.

💰 ANÁLISIS ELÉCTRICO (PVPC):
🟢 VALLE/VERDE: 09:00 (0,09880 €/kWh), 14:00-17:00 (precio medio 0,061 €/kWh).
🔴 PICO/ROJO: 19:00-23:00 (precio máximo 0,24412 €/kWh).
El 21 de abril es martes, no aplican ventajas de fin de semana.

🪟 ESTRATEGIA OPERATIVA DE VENTANAS:

ORDEN: VENTILACIÓN CRUZADA (20:00-23:00) / CIERRE HERMÉTICO (12:00-19:00).

MOTIVO TÉCNICO: Protección frente a Estrés Térmico (30°C) y vientos elevados.

❄️ PLAN DE CLIMATIZACIÓN ACTIVA:

EQUIPO: Combo AC + Ventilador.

AJUSTE: 14:00-17:00 (24°C, Modo Frío).

MOTIVO: Pre-enfriamiento estructural en tramo VERDE económico.

⚠️ ALERTAS Y SEGURIDAD CRÍTICA:

Viento superior a 25 km/h: 19:00 (39 km/h).

Lluvia: 19:00 ("Ip", precipitación ligera).
