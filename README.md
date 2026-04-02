# Segmentación y Contaje Automático de Callos Vegetales

Este proyecto presenta el desarrollo de un software de visión artificial basado en la librería **OpenCV** para la segmentación y cuantificación automática de callos vegetales en cultivos *in vitro*. El objetivo es sustituir el contaje manual tradicional por un método objetivo, no invasivo y escalable.

## Características Principales
* **Segmentación Dual:** Implementa rutas de procesamiento en espacios de color **HSV** (para mayor velocidad) y **RGB Adaptativa** (para condiciones de iluminación irregular).
* **Extracción de Parámetros:** El sistema calcula automáticamente:
    * Contaje total de individuos.
    * Área proyectada (en píxeles y $mm^2$).
    * Centroide y circularidad de cada callo.
* **Precisión Elevada:** Validación con un **97,4% de precisión** global frente al contaje manual (*Ground Truth*).

## Metodología
El flujo de procesamiento digital de imágenes incluye:
1.  **Preprocesamiento:** Filtros de mediana para reducción de ruido.
2.  **Segmentación:** Umbralización en HSV y filtrado por área mínima (>300 px) para eliminar artefactos.
3.  **Refinamiento:** Aplicación de algoritmo **Watershed** para separar objetos próximos y limpieza morfológica (apertura).
4.  **Calibración:** Automatizada mediante la **Transformada de Hough** para detectar el borde de la placa y establecer la escala real.

## Resultados
* **Rendimiento:** El procesamiento en HSV es un 50% más rápido (~0,04 s/imagen) que el modo RGB adaptativo (~0,11 s/imagen).
* **Dataset:** Validado con 16 imágenes digitales (muestras p100 a p133), detectando un total de 112 callos.

## Contenido del Repositorio
* `Conteo_callos.ipynb`: Notebook con el código principal y el flujo de trabajo.
* `Memoria_TematicaC.pdf`: Documentación técnica detallada del proyecto.
* `labelme_annotation/`: Carpeta con las anotaciones de referencia.

## Autores
* Antonio Enrique Coll Meseguer
* Belén Salar Benito
