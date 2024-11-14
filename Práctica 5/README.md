# Práctica 5 - Visión por Computador

### Autores

- Pablo Segura López
- Kilian Armas Pérez

## Explicación del código en VC_P5_G1.ipynb

El archivo `VC_P5_G1.ipynb` contiene un código que utiliza un detector de caras para superponer una visualización de la armadura de Iron Man sobre la cara del usuario. A continuación se explica el funcionamiento del código:

1. **Importación de librerías y configuración inicial**: Se importan las librerías necesarias, se configura la conexión con la webcam y se cargan los videos de Iron Man.

2. **Detección de caras y ojos**: Se utiliza el detector de caras y ojos para localizar la posición de la cara y los ojos del usuario en cada frame de la webcam. Verdaderamente, de las detecciones resultantes a esta sección del código, solo se utiliza el bounding box de la cara para normalizarla y cuadrarla en la armadura de Iron Man y 3 puntos de los labios para decidir si la boca detectada está abierta o no. Se hablará más adelante de esto.

3. **Normalización de la imagen**: Se normaliza la imagen de la cara del usuario para ajustar su tamaño y orientación. 

4. **Superposición de la armadura de Iron Man**: Se superpone la visualización de la armadura de Iron Man sobre la cara del usuario, ajustando su posición y tamaño. Para conseguir esto se crea una máscara de la "Green Screen" existente en los gifs de Iron Man para poder mezclar ambas imágenes. Para la realización de la práctica se han usado dos gifs de Iron Man obtenidos a partir de un vídeo en Youtube[1]: uno de los gifs corresponde al casco abriéndose y el otro al casco cerrándose:

<div>
  <img src="https://github.com/user-attachments/assets/87e95ff3-d5f6-4f23-8857-901f2ac24f7e" width=40% height=40% alt="Opening mask" title="Opening mask">
  <img src="https://github.com/user-attachments/assets/c744c68f-7e29-4dcc-ad56-1238aa4dd275" width=40% height=40% alt="Closing mask" title="Closing mask">
</div>

5. **Detección de apertura de la boca**: Se detecta si el usuario abre la boca y, en función de ello, se alterna entre la visualización de la armadura de Iron Man abierta o cerrada. Para conseguir detectar que la boca está abierta, se han tomado 3 de los puntos encontrados en los labios por el detector de características faciales usado previamente. Esos 3 puntos corresponden a los 2 puntos centrales internos de los labios y uno de los puntos próximos al superior. Cuando la boca se abre, se detecta que la distancia entre los puntos centrales (labio inferior y superior) es sustancialmente mayor a la distancia entre los dos puntos próximos del labio superior.

6. **Visualización del resultado**: Se muestra el resultado final en una ventana, combinando la imagen de la webcam con la visualización de la armadura de Iron Man.

## Ejemplo de funcionamiento

A continuación, se muestra un ejemplo del funcionamiento en formato GIF:

<img src="https://github.com/user-attachments/assets/5e8ef5f5-3c82-410e-adad-fe3636e7d1bd" width=60% height=60% alt="Iron Man filter">

## Enlace al vídeo original

El siguiente enlace redirige a la fuente original de la animación de Iron Man utilizada:

[1] https://www.youtube.com/watch?v=G9i9di9a5QA&ab_channel=GreenScreenMagic
