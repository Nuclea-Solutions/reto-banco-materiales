# Reto Banco Materiales

<a href="https://universe.roboflow.com/materialsbank/dump-truck-detection">
    <img src="https://app.roboflow.com/images/download-dataset-badge.svg"></img>
</a>

Actualmente existe un banco de materiales (terreno con materiales para construcción) que se encuentra
en un lugar remoto por lo que la seguridad deja que desear y muchas veces esto lleva a que se roben
materiales del lugar.

## Problema a resolver

Lo que se busca es poder monitorear el lugar mediante cámaras, procesar la información de estas cámaras
y empezar con la toma de decisiones.

Diferentes consideraciones que se deben tomar en cuenta:

- Cantidad de cámaras
- Posicionamiento de las cámaras
- Calidad de imagen
- FPS de las cámaras
- Procesamiento en tiempo real

Para el procesamiento se tendrá que hacer fine tuning al modelo de YOLOv8 para mejorar la detección de
camiones y a la par poder hacer la distinción de si estos cuentan con materiales. 

Este modelo permitirá llevar a cabo la detección que servirá como parte de los criterios para los
agentes del sistema para la toma de decisiones.

El objetivo inicial es:
- Reconocer cuando un camión cambia su estado (de vacío a lleno)
- Llevar un registro de los camiones que se han visto (sin importar su estado) así como del tiempo que han durado
- A partir de los registros obtenidos, llevar a cabo la toma de decisiones como:
    - Mandar alerta cuando se detecta el cambio de estado de un camión

Video demostrando la detección de objetos:

[![Demo Object Detection](/assets/annotated.mp4)](/assets/annotated.mp4)

## Herramientas a utilizar

- [Ultralytics](https://docs.ultralytics.com/): Proporciona acceso al modelo YOLOv8 y facilita el hacer fine tuning
- [Roboflow](https://roboflow.com/): Para facilitar el etiquetado con el que vamos a hacer fine tuning
- [Supervision](https://github.com/roboflow/supervision): Librería para python que facilita el agregar anotaciones a los frames para mostrar cada objeto detectado por el modelo, tiene integración con Ultralytics
- [OpenCV](https://pypi.org/project/opencv-python/): Usada por supervision para etiquetado y ofrece facilidades para interactuar con cámaras
- Unreal Engine: Generación de simulaciones para usar como entrada de datos (los frames) al modelo
- AgentPy: Biblioteca de Python para trabajar con Modelación Basado en Agentes (ABM). Útil para implementar Sistemas Multi-Agentes (MAS).
- Sockets: para comunicar Cliente (Unreal Engine) y Servidor (AgentPy)

## Instalacion

Se recomienda tener lo siguiente instalado antes de correr los ejemplos si se piensa correr en local:

- git-lfs
- python: 3.11.0
- pip: 22.3

Por facilidad para cambiar entre version de python (en caso de que lo utilicen para
otras materias o proyectos personales), tambien se recomienda instalar pyenv para
manejar las diferentes versiones.

## Ejemplos

Antes de correr los ejemplos, necesitamos instalar las dependencias del proyecto:

```sh
pip install -r requirements.txt
```

El proyecto ya cuenta con algunos [ejemplos](/examples/) que son:

Titulo | Visual Studio Code | Google Colab | Descripcion
--------|-----------|------------|----------
Introduccion | [Introduccion](/examples/introduction.ipynb) | [Introduccion](https://colab.research.google.com/drive/1omeyCRGkCGpKhKsX5HgN_aRbvT06wpyB#scrollTo=2XJO1qTdn_g_) | Como usar un modelo (yolov8n) para detectar objetos a partir de una imagen
Deteccion con video | [Detection With Video](/examples/detection-with-video.ipynb) | [Detection With Video](/) | Como usar un modelo (modelo con fine tunning) para detectar camiones con y sin materiales a partir de un video
Fine Tuning | [Fine Tuning](/examples/fine-tuning.ipynb) | [Fine Tuning](/) | Como hacerle fine tuning al modelo de YOLO