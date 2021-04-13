# Algoritmo Daugman

El algoritmo de Daugman mide la diferencia en las intensidades de píxeles promedio en una imagen en escala de grises para un grupo de círculos con el mismo centro y radio diferente.

Aquí revisaremos la funcionalidad de este método para la segmentación de región de iris requerida en la implementación de sistemas de reconocimiento biométrico a través de la información de nuestros ojos.

La idea es encontrar la mayor caída (delta) en los valores de intensidad entre dos círculos vecinos. Debería implicar la transición entre el iris y su entorno.

<img src="https://github.com/carlosjulioph/Algoritmo-de-Daugman/blob/main/images_readme/1.png" width="700">

Para revisar cada uno de los pasos del algoritmo puedes ejecutar el notebook <u>`daugman_visual_explicacion.ipynb`</u> 

<img src="https://github.com/carlosjulioph/Algoritmo-de-Daugman/blob/main/images_readme/2.png" width="700">

A través de <u>`Prueba_daugman.py`</u>  realizamos pruebas para analizar precisión,  utilizando una muestra de imágenes del conjunto de datos  **UBIRIS.v1** Este conjunto de datos se compone de 1877 imágenes recopiladas de 241 personas durante septiembre de 2004 en dos sesiones distintas. Su principal característica es el hecho de que, en oposición a las bases de datos públicas y gratuitas existentes (CASIA y UPOL), incorpora imágenes con varios factores de ruido, permitiendo así la evaluación de métodos de reconocimiento de iris de robustez.

Solo se están considerando en la carpeta  <u>`final_image`</u> unas cuantas imágenes de dimensiones 200x150 correspondientes a la región del ojo definida a partir de un proceso de detección en el subconjunto de La sesión_1 , que contiene 1214 imágenes (800x600 pixeles) de 214 personas  diferentes. 

Para obtener un mejor resultado en la detección de la región del iris la imagen de entrada al algoritmo daugman debe ser de dimensiones cuadradas. Asi que de las imágenes originales se define una región de interes ROI cuadrada de dimensiones 150x150.

Para la detección de la región de Iris utilizamos la función `find_iris`:

`answer = find_iris(gray_img, daugman_start=10, daugman_end=70, daugman_step=2, points_step=3)`

donde,

- `gray_img`: imagen a escala de grises de dimensiones cuadradas.
- `daugman_start`: valor inferior en píxeles para el radio del iris.
- `daugman_end`: valor superior en píxeles para el radio del iris.
- `daugman_step`: valor en píxeles de paso para el rango de radios del iris.
- `points_step`: define cada cuantos puntos potenciales se ejecuta daugman.

La función retorna en `answer`  el circulo con el mayor delta de intensidad en la imagen como una tupla `((xc, yc), radius)`.

Para más información:
- [Iris localization using Daugman’s algorithm](https://www.diva-portal.org/smash/get/diva2:831173/FULLTEXT01.pdf)
