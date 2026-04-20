# agente-eficiencia-energetica

🤖 Agente de IA: Consultor de Eficiencia Energética (n8n + Gemini)
Este repositorio contiene un flujo de n8n diseñado para actuar como un consultor inteligente en eficiencia energética y salud ambiental. El sistema monitoriza automáticamente el clima y los precios de la electricidad para generar recomendaciones personalizadas enviadas vía Telegram.

🕒 Automatización y Programación Crítica
El flujo está configurado con un nodo Schedule Trigger para automatizar su ejecución diaria.

Hora de ejecución recomendada: Se debe programar a partir de las 20:15 o 21:00 horas.

Motivo técnico: El nodo Consula_Precios_REE busca los datos del día siguiente utilizando la expresión {{ $now.plus({ days: 1 }) }}.

Disponibilidad de datos: Red Eléctrica de España (REE) suele publicar los precios del PVPC para la jornada siguiente a las 20:15; una ejecución anterior resultará en un error por falta de datos.

🏗️ Funcionamiento del Sistema
El flujo se organiza en tres etapas principales que convergen en el Agente de IA:

Ingesta de Datos Meteorológicos (AEMET): Obtiene la previsión horaria y la formatea para extraer variables críticas como temperatura, rachas de viento y humedad.

Análisis de Mercado Eléctrico (REE): Consulta los precios del PVPC para el día siguiente, clasificándolos por tramos horarios y niveles de coste (Verde, Amarillo, Rojo).

Análisis de IA (Google Gemini): El agente procesa ambas fuentes de datos basándose en los estándares de la OMS (confort entre 18°C-24°C) para recomendar el uso de ventanas, aire acondicionado o ventiladores.

📋 Requisitos de Configuración
1. API AEMET
Obtención: Solicita tu API Key gratuita en el Centro de Descargas de AEMET.

Nodo: Obtencion_URL_AEMET.

2. Google Gemini (IA)
Token: Genera tu clave en Google AI Studio.

Modelo: Se utiliza el modelo más eficiente (Gemini Flash), optimizado para tareas de análisis de datos estructurados sin consumo excesivo de recursos.

3. Red Eléctrica (REE)
Token: Este flujo utiliza el token público de la API de ESIOS.

Referencia: Puedes consultar la documentación oficial o solicitar un token propio en la web de ESIOS.

4. Telegram
Configura un bot mediante @BotFather y obtén tu Chat ID personal para recibir el informe.
