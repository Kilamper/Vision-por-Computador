# Práctica 3

### Autores

- Pablo Segura López
- Kilian Armas Pérez

## Tarea 1 - Captura una o varias imágenes con monedas no solapadas. 
En esta tarea 1 se ha realizado la detección de monedas usando funciones de umbralizado (Threshold) y posteriormente detección de contornos. Para ello, en el cuaderno se exponen dos casos: con una imagen ideal y una imagen no ideal.
Además, para contar el dinero total que había en la imagen, se calculó previamente los datos de las longitudes reales de los diamétros de las monedas y, teniendo una moneda de referencia, se comparan los ratios en píxeles con los reales. Dicha moneda de referencia se pide al usuario, indicando que introduzca como "input" el valor de la moneda en céntimos (en caso de 1 o 2 euros sería 100 o 200) y, posteriormente, se pide al usuario que señale la moneda de dicho valor en la imagen.
En el caso de la imagen ideal, bastó con aplicar un threshold Otsu y buscar los contornos. El proceso de ejecución, desde el punto de vista del usuario, es el siguiente:
- Se pide el valor de la moneda de referencia
- Se pide que el usuario señale dicha moneda en la imagen:

![Captura de pantalla 2024-10-15 223629](https://github.com/user-attachments/assets/f2fbf7c0-3a66-4b5c-83a9-92c3b9f171a4)

- Por último, se muestra la imagen posteriormente con las monedas encontradas y mostrando por pantalla la cantidad de dinero que se encontró en la imagen:

![Captura de pantalla 2024-10-15 224627](https://github.com/user-attachments/assets/7856af46-63f1-48df-a491-1e12d9cb3193)

En el caso de la imagen no ideal, no solo fue necesario aplicar el threshold, sino que, a su vez, se llevó a cabo un desprecio del ruido/sombras de la imagen mediante dilatado y difuminado (blur), después, se llevó a cabo el mismo proceso explicado anteriormente.
Imagen no ideal:

![Coins1](https://github.com/user-attachments/assets/ca71069c-8675-4fed-bf2e-6fc728eb6dbe)

Resultado de la imagen no ideal: en el caso de esta imagen no ideal, el conteo del dinero puede depender del valor de la moneda de referencia, conllevando un error mayor o menor. En el caso de la próxima imagen, el error es de 1 céntimo (4,63€), usando la moneda de 1 euro como imagen de referencia:

![Captura de pantalla 2024-10-15 224644](https://github.com/user-attachments/assets/e79fd725-d2ed-48c6-b4d5-cd7f16efe55c)

Extra: para evitar tomar como "moneda" objetos muy grandes o muy pequeños, se añadieron dos entradas al diccionario de ratios de los tamaños de las monedas. Una de ellas para evitar los objetos muy pequeños y la otra para evitar los objetos muy grandes. A ambas se le concedió un valor de 0€

## Tarea 2 - Segmentación y reconocimiento de microplásticos y matriz de confusión
Primero que nada, en esta tarea se llevó a cabo un proceso de segmentación y de análisis de características geométricas y de color, mostrándolas por pantalla para tomar características que facilitaran diferenciar los diferentes tipos de microplásticos.
Segmentación de las 3 categorías:

![Captura de pantalla 2024-10-15 223509](https://github.com/user-attachments/assets/ddaef074-49b6-4031-b752-2ad79052c1c2)

![Captura de pantalla 2024-10-15 223458](https://github.com/user-attachments/assets/d85bcfb0-04a3-4ee8-808e-a5d77a3de177)

![Captura de pantalla 2024-10-15 223447](https://github.com/user-attachments/assets/6be6f28d-158c-4235-9b43-a336d4579dfd)

Ejemplo de output de características:

![Captura de pantalla 2024-10-15 231136](https://github.com/user-attachments/assets/532c75e7-38a1-4e4d-8d1a-adc0bddf0663)

Mediante este análisis, llegamos a las siguientes conclusiones para diferenciar los microplásticos: se podría considerar un fragmento en caso de que su compacidad fuera mayor que 30 y que el número de puntos que formaba su perímetro fuera mayor a 100, o bien si su color era mayor a 110; se podría considerar alquitrán todos aquellos cuyo color fuera muy oscuro, inferior a 70; y el resto serían pellets.
Teniendo en cuenta esto, se usaron las próximas 3 imágenes para testear la precisión de estas decisiones y crear la matriz de confusión en base a los resultados:

![pellet-03-olympus-10-01-2020](https://github.com/user-attachments/assets/22b89dc1-8ae1-41b5-8af8-cdde860459a5)

![fragment-03-olympus-10-01-2020](https://github.com/user-attachments/assets/46dad506-fc79-4e46-8361-9bc0fcaf560a)

![tar-03-olympus-10-01-2020](https://github.com/user-attachments/assets/43a9dc36-0bce-455b-b222-bae3780208ba)

La matriz de confusión fue la siguiente:

![Captura de pantalla 2024-10-15 223533](https://github.com/user-attachments/assets/5ae4b73a-3489-49be-8b16-66a833811d78)

En la matriz de confusión se puede observar que hay 9 errores, causados porque el algoritmo confundió 9 pellets como alquitrán. 
En general, el algoritmo tiene un buen rendimiento, brindando una exactitud del 95,21%, una precisión del 95,72%, una puntuación F1 de 95,14% y un "recall" (cómo de bien reconoce los True Positives) del 95,21%.
