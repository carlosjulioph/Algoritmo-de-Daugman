# Algoritmo Daugman

El algoritmo de Daugman mide la diferencia en las intensidades de píxeles promedio en una imagen en escala de grises para un grupo de círculos con el mismo centro y radio diferente.

Aquí revisaremos la funcionalidad de este método para la segmentación de región de iris requerida en la implementación de sistemas de reconocimiento biométrico a través de la información de nuestros ojos.

La idea es encontrar la mayor caída (delta) en los valores de intensidad entre dos círculos vecinos. Debería implicar la transición entre el iris y su entorno.

![](https://github.com/carlosjulioph/Algoritmo-de-Daugman/blob/main/images_readme/1.png){:height="50%" width="50%"}
