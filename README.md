
Proyecto: Interview IA
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
Un Simulador de Entrevistas Técnicas Impulsado por IA
1. Contexto del Problema
En el sector tecnológico, las entrevistas de programación son un pilar fundamental. Sin embargo, practicar en un entorno realista es difícil. Las plataformas actuales validan la corrección del código, pero ignoran una habilidad igualmente crucial: la capacidad de comunicar y razonar sobre la propia solución. Un gran ingeniero no solo escribe código que funciona, sino que puede explicar por qué tomó ciertas decisiones, analizar su eficiencia y discutir alternativas.

El objetivo de este proyecto es crear "Interview IA", un simulador que evalúa de forma integral tanto la habilidad técnica para resolver problemas como la capacidad de comunicación del desarrollador.

2. Stack Tecnológico
La solución debe ser construida utilizando exclusivamente el siguiente stack:

Backend: Django

Base de Datos: MongoDB

Inteligencia Artificial:

Google Gemini (a través de Vertex AI)

Google Cloud Speech-to-Text

Gestión de Contexto IA: Model Context Protocol (MCP)

3. Librerías Principales
Para la interacción con el stack, necesitarás las siguientes librerías de Python. La gestión de otras dependencias de Django corre por tu cuenta.

Python

# requirements.txt
django
pymongo
google-cloud-aiplatform
google-cloud-speech
4. Flujo del Sistema
Tu tarea es diseñar e implementar la arquitectura que haga posible el siguiente flujo de usuario:

Inicio y Selección:

El usuario accede a la aplicación y ve una lista de problemas de programación.

Elige un problema y un modo de entrevista: Modo Texto o Modo Voz.

Creación de la Sesión:

El backend crea un nuevo documento en MongoDB para la sesión, almacenando el estado inicial de la entrevista.

Interacción (Modo Texto):

El usuario escribe su solución en un editor de código.

Al enviar, el backend construye un contexto (MCP) con la descripción del problema y el código del usuario.

Se invoca a Gemini con este contexto para analizar la correctitud, eficiencia y calidad del código. La evaluación se muestra al usuario.

Interacción (Modo Voz):

El usuario primero escribe y finaliza su código.

Luego, activa el micrófono y explica verbalmente su razonamiento.

El audio es procesado por la API Speech-to-Text para obtener una transcripción.

El backend construye un contexto (MCP) enriquecido: problema + código + transcripción.

Se invoca a Gemini con este contexto multimodal, pidiéndole que evalúe la claridad del razonamiento y formule preguntas de seguimiento.

Feedback:

Al concluir, una llamada final a Gemini revisa el contexto completo de la sesión.

La IA genera un informe final consolidado (puntos fuertes y áreas de mejora).

Este informe se almacena en MongoDB y se presenta al usuario.

FLUJO DEL SISTEMA (DIAGRAMA DE ACTIVIDAD)
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
<img width="4185" height="5162" alt="MCP_6" src="https://github.com/user-attachments/assets/88977688-3c2b-4f14-9eb3-f910ca6921d8" />
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

MÁS INFORMACIÓN:

https://docs.google.com/document/d/1nyIVEeCo2HoJd9jIZh6vyXJzRObPbMsqKJFZZqEYH1U/edit?usp=sharing


