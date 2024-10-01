# Práctica 2

### Autores

- Pablo Segura López
- Kilian Armas Pérez

## Tarea 1 - Realizar la cuenta de píxeles blancos por filas (en lugar de por columnas).

En esta tarea realizamos la cuenta de píxeles blancos por filas basandonos en el ejemplo de conteo por columnas, para ello indicaremos en la llamada a la función "cv2.reduce()" que queremos sumar los valores de los píxeles por filas en vez de por columnas, lo que se indica mediante el segundo parámetro, que puede ser 0 (suma por columnas) o 1 (suma por filas).

Cuando ya se hayan sumado los valores de los píxeles, realizaremos el cálculo del porcentaje de píxeles blancos por fila. Esto se llevará a cabo diviendo la suma de los valores de los píxeles de cada fila entre 255 por el número de filas.

![Respuesta de Canny por Filas](https://github.com/user-attachments/assets/498b64e2-2c01-4801-90d3-85f29ed9bdbf)

Una vez calculados los porcentajes, en primer lugar, procedemos a calcular el número de píxeles blancos por columnas y filas. Con estos datos, ya podemos hallar el número máximo y mínimo de píxeles tanto por columnas como por filas, el índice de estos y el número de columnas/filas con una cantidad mayor o igual al 95% del máximo.

![Máximos y Mínimos de Píxeles Blancos Canny](https://github.com/user-attachments/assets/75b56376-977c-4aac-b39e-0d71717270e1)

## Tarea 2 - Aplicar umbralizado a la imagen resultante de Sobel

En primer lugar, realizamos el umbralizado de la imagen de Sobel para obtener una imagen lo más similar posible a la obtenida anteriormente con Canny.

![Umbralizado Imagen Sobel](https://github.com/user-attachments/assets/18c541ec-66a3-40f8-9e8f-d3bcb427b45a)

Cuando ya tengamos la imagen umbralizada de Sobel, al igual que con la imagen resultante de Canny, hallaremos los máximos y mínimos, así como los índices de estos.

![Máximos y Mínimos de Píxeles Blancos Sobel](https://github.com/user-attachments/assets/540658f2-4092-47ba-8d82-dd568a7ae403)

A continuación, dibujaremos líneas blancas sobre las columnas y/o filas con una cantidad de píxeles blancos superior al 95% del máximo. Esto se logra recorriendo con un for los vectores "max_col_95_sobel" y "max_row_95_sobel", que contienen valores booleanos (True/False), donde el valor True indica que esa línea supera el umbral señalado.

![Mayor/Igual 95% Máximo Sobel](https://github.com/user-attachments/assets/4ae30050-dbf4-49e9-8939-c72fe8bff753)

## Tarea 3 - Proponer un demostrador que capture las imágenes de la cámara.

Como demostrador hemos decidido mostrar cuatro versiones alternas del vídeo capturado por la cámara. Estas cuatro versiones son: una inversión de los colores de la imagen (1); la detección de la sección 8x8 más clara y más oscura de la imagen capturada (2), destacando con un círculo blanco la más oscura y con un círculo negro la más clara; un efecto de aberración cromática sobre la captura (3), este efecto se ha conseguido desplazando los canales cromáticos horizontalmente o verticalmente; y una detección de rostros que muestra toda la pantalla en negro, excepto un círculo alrededor de las caras detectadas (4). Cada una de estas opciones se activa presionando la tecla correspondiente, que se indican entre paréntesis anteriormente.

<div style="display: flex; gap: 10px;">
    <div>
        <h4>Imagen invertida</h4>
        <img src="https://github.com/user-attachments/assets/fb265c72-5436-44cb-a365-d5e890847b74" alt="Imagen invertida">
    </div>
    <div>
        <h4>Más claro y más oscuro</h4>
        <img src="https://github.com/user-attachments/assets/547ec002-adc0-4661-bdc3-c453c7373267" alt="Más claro y más oscuro">
    </div>
    <div>
        <h4>Aberración cromática</h4>
        <img src="https://github.com/user-attachments/assets/bf2382be-409b-4566-9eb1-97330fcffc76" alt="Aberración cromática">
    </div>
    <div>
        <h4>Detección de rostros</h4>
        <img src="https://github.com/user-attachments/assets/f11f053e-b30d-4e0b-84e7-cffddab1ee77" alt="Detección de rostros">
    </div>
</div>

## Tarea 4 - Plantear una reinterpretación de la parte de procesamiento de la imagen tomando como punto de partida alguna de dichas instalaciones.
Para esta tarea hemos decidido llevar a cabo una idea que parodia en cierto modo a "My little piece of privacy" [Fuente 1]. De esta forma, planteamos una "cortina" negra que va siguiendo el movimiento. Esta "cortina" está formada por líneas verticales negras que se colocan en las columnas de la imagen que detecten movimiento. Para ello, se ha tomado en cuenta la diferencia entre el frame actual con uno anterior y se busca las columnas de la imagen en la que dicha diferencia sea muy alta.

<img src="https://github.com/user-attachments/assets/6660e992-0678-452f-a3ed-4010d6ca8156" alt="Cortina negra que sigue el movimiento">

## Fuentes
Fuente 1: https://www.niklasroy.com/project/88/my-little-piece-of-privacy 
