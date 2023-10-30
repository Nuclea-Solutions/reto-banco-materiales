# Reto Banco Materiales

Actualmente existe un banco de materiales (terreno con materiales para construcción) que se encuentra
en un lugar remoto por lo que la seguridad deja que desear y muchas veces esto lleva a que se roben
materiales del lugar.

## Problema a resolver

Lo que se busca es poder monitorear el lugar mediante cámaras, procesar la información de las cámaras
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

