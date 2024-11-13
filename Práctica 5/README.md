# Práctica 5 - Visión por Computador

### Autores

- Pablo Segura López
- Kilian Armas Pérez

## Explicación del código en VC_P5_G1.ipynb

El archivo `VC_P5_G1.ipynb` contiene un código que utiliza un detector de caras para superponer una visualización de la armadura de Iron Man sobre la cara del usuario. A continuación se explica el funcionamiento del código:

1. **Importación de librerías y configuración inicial**: Se importan las librerías necesarias, se configura la conexión con la webcam y se cargan los videos de Iron Man.

2. **Detección de caras y ojos**: Se utiliza el detector de caras y ojos para localizar la posición de la cara y los ojos del usuario en cada frame de la webcam.

3. **Normalización de la imagen**: Se normaliza la imagen de la cara del usuario para ajustar su tamaño y orientación.

4. **Superposición de la armadura de Iron Man**: Se superpone la visualización de la armadura de Iron Man sobre la cara del usuario, ajustando su posición y tamaño.

5. **Detección de apertura de la boca**: Se detecta si el usuario abre la boca y, en función de ello, se alterna entre la visualización de la armadura de Iron Man abierta o cerrada.

6. **Visualización del resultado**: Se muestra el resultado final en una ventana, combinando la imagen de la webcam con la visualización de la armadura de Iron Man.

## GIF de funcionamiento del código

![Funcionamiento del código](images/ironman.gif)
