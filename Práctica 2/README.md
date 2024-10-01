# Práctica 2

### Autores

- Pablo Segura López
- Kilian Armas Pérez

## Tarea 1 - Realizar la cuenta de píxeles blancos por filas (en lugar de por columnas).

En esta tarea realizamos la cuenta de píxeles blancos por filas basandonos en el ejemplo de conteo por columnas, para ello indicaremos en la llamada a la función "cv2.reduce()" que queremos sumar los valores de los píxeles por filas en vez de por columnas, lo que se indica mediante el segundo parámetro, que puede ser 0 (suma por columnas) o 1 (suma por filas).

Cuando ya se hayan sumado los valores de los píxeles, realizaremos el cálculo del porcentaje de píxeles blancos por fila. Esto se llevará a cabo diviendo la suma de los valores de los píxeles de cada fila entre 255 por el número de filas.

![Respuesta de Canny por filas](image.png)

Una vez calculados los porcentajes, en primer lugar, procedemos a calcular el número de píxeles blancos por columnas y filas. Con estos datos, ya podemos hallar el número máximo y mínimo de píxeles tanto por columnas como por filas, el índice de estos y el número de columnas/filas con una cantidad mayor o igual al 95% del máximo.

![Máximos y Mínimos Píxeles Blancos Canny](image-1.png)

## Tarea 2 - Aplicar umbralizado a la imagen resultante de Sobel

En primer lugar, realizamos el umbralizado de la imagen de Sobel para obtener una imagen lo más similar posible a la obtenida anteriormente con Canny.

![Umbralizado Imagen Sobel](image-2.png)

Cuando ya tengamos la imagen umbralizada de Sobel, al igual que con la imagen resultante de Canny, hallaremos los máximos y mínimos, así como los índices de estos.

![Máximos y Mínimos Píxeles Blancos Canny](image-3.png)

A continuación, dibujaremos líneas blancas sobre las columnas y/o filas con una cantidad de píxeles blancos superior al 95% del máximo. Esto se logra recorriendo con un for los vectores "max_col_95_sobel" y "max_row_95_sobel", que contienen valores booleanos (True/False), donde el valor True indica que esa línea supera el umbral señalado.

![Mayor/Igual 95% Máximo](image-4.png)

## Tarea 3 - Proponer un demostrador que capture las imágenes de la cámara.



## Tarea 4 - Plantear una reinterpretación de la parte de procesamiento de la imagen tomando como punto de partida alguna de dichas instalaciones.
