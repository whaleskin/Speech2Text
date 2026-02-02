# 🔢 OBS MODULO 10 - *Speech and Text Analytics*
![Speech to Text](https://ibb.co/JjXyb9Yr)

Este repositorio contiene el código que hemos desarrollado durante el máster de IA en OBS para:

El proyecto se realiza en 4 etapas.
El código fuer realizado en python 3.12.10, utilizando visual studio code, el cual puede ser personalizado según se requiera.
La interfaz gráfica se ha realizado en GRADIO.

# 🌐 Aplicación Web de Transcripción de Voz a Texto basada en Whisper

## 1. Introducción
Este documento describe el diseño, implementación y funcionamiento de una aplicación web para la transcripción automática de voz a texto. La aplicación ha sido desarrollada como parte del Trabajo Fin de Máster (TFM) en el contexto de la asignatura *Speech and Text Analytics*.
El objetivo principal del sistema es permitir al usuario convertir audio en texto de manera sencilla, ya sea grabando directamente desde un micrófono o subiendo un archivo de audio previamente grabado. Para ello, se utiliza el modelo Whisper de OpenAI, reconocido por su alto rendimiento en tareas de reconocimiento automático del habla (ASR, *Automatic Speech Recognition*).

---

## 2. Objetivos del sistema
Los objetivos principales de la aplicación son:

- Implementar un sistema de transcripción de voz a texto basado en modelos de *Deep Learning*.
- Proporcionar una interfaz web intuitiva y accesible.
- Permitir la entrada de audio tanto en tiempo real (micrófono) como mediante archivos.
- Almacenar de forma automática las grabaciones procesadas.
- Garantizar un diseño visual claro y consistente.

---

## 3. 💻 Tecnologías empleadas

### 3.1 Python
Lenguaje principal de desarrollo, elegido por su ecosistema de librerías orientadas a *Machine Learning* y procesamiento de audio.

### 3.2 Gradio
Framework utilizado para la creación de la interfaz web. Permite conectar funciones de Python con componentes visuales de manera rápida y eficiente.

### 3.3 Whisper (OpenAI / Hugging Face)
Modelo de reconocimiento de voz a texto basado en *Transformers*. Se emplean dos posibles implementaciones:
- Whisper a través de la librería `transformers` de Hugging Face.
- Whisper oficial de OpenAI como mecanismo de respaldo.

### 3.4 PyTorch
Se utiliza para detectar la disponibilidad de GPU (CUDA) y acelerar el proceso de inferencia cuando es posible.

### 3.5 FFmpeg
Herramienta empleada para normalizar los archivos de audio, asegurando un formato estándar (mono, 16 kHz) adecuado para el reconocimiento del habla.

---

## 4. Arquitectura del sistema

La aplicación sigue una arquitectura sencilla de tipo cliente-servidor:

1. **Interfaz de usuario (UI)**: construida con Gradio y accesible desde un navegador web.
2. **Lógica de negocio**: función de transcripción que gestiona la entrada de audio, la inferencia del modelo y el almacenamiento.
3. **Modelo de ASR**: Whisper, encargado de transformar el audio en texto.
4. **Sistema de archivos**: utilizado para guardar las grabaciones procesadas.

---

## 5. Funcionamiento de la aplicación

### 5.1 Selección del dispositivo
Al iniciar la aplicación, se detecta automáticamente si existe una GPU compatible con CUDA. En caso afirmativo, el modelo se ejecuta sobre GPU; de lo contrario, se utiliza la CPU.

### 5.2 Carga del modelo
Se intenta cargar el modelo Whisper mediante la librería `transformers`. Si esta carga falla, se utiliza la implementación oficial de OpenAI Whisper como alternativa.

### 5.3 Entrada de audio
El usuario puede proporcionar audio de dos formas:

- Grabación directa desde el micrófono.
- Subida de un archivo de audio en formatos comunes (.wav, .mp3, .m4a, .flac, .ogg, .aac).

### 5.4 Proceso de transcripción
Una vez recibido el audio:

1. Se genera un nombre de archivo único mediante un *timestamp*.
2. El audio se transcribe utilizando Whisper.
3. El archivo se normaliza y se guarda en el directorio local de grabaciones.
4. El texto transcrito se muestra en la interfaz web.

### 5.5 Salida
La aplicación devuelve:

- El texto transcrito.
- La ruta completa donde se ha almacenado el archivo de audio procesado.

---

## 6. Diseño de la interfaz

La interfaz se ha diseñado con los siguientes criterios:

- Dos columnas de ancho fijo, centradas en la pantalla.
- Separación clara entre entradas y salidas.
- Botón principal de acción que ocupa el ancho completo de ambas columnas.
- Adaptación a pantallas pequeñas mediante reglas *responsive* en CSS.

Este diseño mejora la usabilidad y facilita la comprensión del flujo de interacción.

---

## 7. Gestión de errores

El sistema incluye mecanismos básicos de control de errores:

- Validación de la existencia de audio antes de la transcripción.
- Captura de excepciones durante la inferencia y el procesamiento de audio.
- Mensajes informativos mostrados al usuario en caso de fallo.

---

## 8. 📌 Conclusiones

La aplicación desarrollada cumple los objetivos planteados, ofreciendo una solución funcional y accesible para la transcripción automática de voz a texto. El uso de Whisper garantiza una alta calidad en el reconocimiento del habla, mientras que Gradio facilita la creación de una interfaz clara y eficiente.

Este sistema puede ampliarse en trabajos futuros incorporando características como detección automática de idioma, diarización de hablantes, transcripción por segmentos con marcas temporales o integración con bases de datos.

---

## 9. Trabajo futuro

Como posibles líneas de mejora se proponen:

- Añadir selección manual o detección automática del idioma.
- Incorporar marcas de tiempo por frase o palabra.
- Implementar procesamiento por lotes de múltiples archivos.
- Integrar métricas de evaluación del reconocimiento.
- Desplegar la aplicación en un entorno cloud.

---

## 10. Referencias

- OpenAI. *Whisper: Robust Speech Recognition via Large-Scale Weak Supervision*.
- Hugging Face Transformers Documentation.
- Gradio Documentation.
- FFmpeg Documentation.

---

## Los participantes de este proyecto hemos sido:
- Carlos
- Juan
- Nicolas
- Riccardo
