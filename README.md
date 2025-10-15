README: Proyecto "Interview IA"
1. Contexto del Problema
En el sector tecnológico, las entrevistas de programación son un pilar fundamental. Sin embargo, practicar en un entorno realista es difícil. Los desarrolladores a menudo recurren a plataformas que solo validan la corrección del código, pero ignoran una habilidad igualmente crucial: la capacidad de comunicar y razonar sobre la propia solución. Un buen ingeniero no solo escribe código que funciona, sino que puede explicar por qué tomó ciertas decisiones, analizar su eficiencia y discutir alternativas.

El objetivo de este proyecto es resolver ese problema creando "Interview IA", un simulador de entrevistas inteligente que evalúa tanto la habilidad técnica para resolver problemas como la capacidad de comunicación del desarrollador.

2. Stack Tecnológico Obligatorio
La solución debe ser construida utilizando exclusivamente el siguiente stack tecnológico:

Backend: Django

Base de Datos: MongoDB

Inteligencia Artificial:

Google Gemini (a través de Vertex AI)

Google Cloud Speech-to-Text

Gestión de Contexto IA: Model Context Protocol (MCP)

3. Librerías Principales
Para interactuar con el stack, necesitarás principalmente las siguientes librerías de Python. La gestión de otras dependencias de Django corre por tu cuenta.

# requirements.txt
django
pymongo
google-cloud-aiplatform
google-cloud-speech
4. Flujo del Sistema
Así es como la aplicación debe funcionar a alto nivel. Tu tarea es diseñar e implementar la arquitectura que haga posible este flujo.

Inicio y Selección: El usuario llega a la aplicación, ve una lista de problemas de programación y elige uno, junto con un modo de entrevista: "Modo Texto" o "Modo Voz".

Sesión de Entrevista (Backend): Al iniciar, el backend crea un nuevo documento de sesión en MongoDB, asociando al usuario con el problema seleccionado. Aquí se almacenará todo el estado de la entrevista.

Interacción - Modo Texto:

El usuario escribe su solución en un editor de código en el frontend.

Al enviar, el código viaja al backend.

El backend construye un contexto (MCP) que incluye la descripción del problema y el código del usuario.

Se invoca a Gemini con este contexto para que analice la correctitud, eficiencia y calidad del código.

La evaluación de Gemini se muestra al usuario.

Interacción - Modo Voz:

El usuario primero escribe y finaliza su código.

A continuación, activa el micrófono para explicar su razonamiento.

El audio es enviado al backend.

El backend reenvía el audio a la API Speech-to-Text, que devuelve una transcripción.

El backend ahora construye un contexto (MCP) mucho más rico: la descripción del problema, el código del usuario y la transcripción de su explicación verbal.

Se invoca a Gemini con este contexto multimodal, pidiéndole que evalúe la claridad del razonamiento y formule preguntas de seguimiento.

Feedback Final: Al concluir cualquier modo, se realiza una llamada final a Gemini. Se le entrega el contexto completo de la sesión y se le pide que genere un informe final, consolidando los puntos fuertes y las áreas de mejora tanto en el código como en la comunicación. Este informe se almacena en MongoDB y se presenta al usuario.
