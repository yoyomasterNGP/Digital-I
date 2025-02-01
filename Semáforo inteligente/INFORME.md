# Semáforo inteligente

## Introducción

## Diseño

Para este proyecto vamos diseñar un circuito que maneje los semáforos de una intersección de 2 calles en doble sentido en función del tráfico de cada una; teniendo un total de 4 semáforos, que llamaremos semáforo A, B, C, D.

![Tomado de: https://www.freepik.es/vector-premium/highways-vista-superior-dibujos-animados_1878740.htm](IMAGENES_PF/DIS.png "Diseño")

### Entradas y salidas

Las entradas constarán de un par de sensores que medirán tanto el tráfico que entra como el tráfico que sale, que llamaremos Xp y Xl respectivamente, para un total de 8 entradas. Las salidas serán la iluminación del semáforo (Rojo, amarillo o verde), que llamaremos RX, AX y VX, para un total de 12 salidas.

![Tomado de: https://www.freepik.es/vector-premium/highways-vista-superior-dibujos-animados_1878740.htm](IMAGENES_PF/E-S.png "Entradas-Salidas")

### Diagrama de bloques

El proyecto lo definimos en distintas etapas. Primeramente, las señales de entrada deberán pasar por un contador que sume los carros que entran a la calle y reste los carros que salgan de la misma. Después, necesitamos saber cúal es la calle con más tráfico, por lo que la señal de los contadores pasará por un comparador que determine cúal es la calle con más tráfico. Una vez definido el estado actual del tráfico, una máquina de estados decide cúal es el estado siguiente siguiente que los semáforos deben tomar. Finalmente, según las salidas de la máquina de estados, cada semáforo tiene su propia lógica que establece que luz se debe prender.

![Diagrama de bloques](IMAGENES_PF/DB.png "Diagrama de bloques")

### Contador

Vamos a trabajar con un contador de 6 bits, de esta manera se puede contar tráfico del 0 al 63.
![Contador](IMAGENES_PF/CONT.JPG "Contador")

La entrada y salida del tráfico la simulamos con 2 pulsadores, "+" y "-" respectivamente; así mismo las entradas "++" y "--" cumplen la misma función pero se conectan con una señal reloj adicional para subir o bajar más rápido el contador, aunque no tienen niguna aplicación real. Los valores de los contadores se restan para sacar el tráfico total y con ello obtenemos la salida "Num" que es el número de 6 bits. Adicional a esto tenemos 2 circuitos combinacionales que tienen como salida "L" y "M", la "L" impide que el número pase de 63 a 0 y la "M" impide que el número pase de 0 a 63.

### Comparador 

![Comparador](IMAGENES_PF/COM.JPG "Comparador")

El comparador tiene 4 entradas de 6 bits, que corresponde al tráfico de cada semáforo y son NA, NB, NC, ND; y 4 salidas de 1 bit TA, TB, TC y TD que representarán cuál es el semáforo con mayor tráfico. Para definir el número mayor se emparejan los números en NA - NB, y NC - ND y se comparan, los dos números mayores pasan a un nuevo comparador y con esto ya sabemos cúal es el número mayor. Además de esto, hay una serie de compuertas lógicas y multiplexores que defininen las salidas. Una aclaración con este circuito es ¿qué pasaría si dos o más semáforos tienen el mismo tráfico?, en este caso se escogió de manera arbitraria la siguiente jerarquía:

1. Tráfico A
2. Tráfico B
3. Tráfico C
4. Tráfico D

Lo que quiere decir que el semáforo A tiene mayor prioridad y el semáforo D el de menor prioridad.

### Máquina de estados 
La máquina de estados tendrá 4 de entradas de 1 bit que son TA, TB, TC y TD que representan el estado presente, a partir de esto definimos los distintos estados que puede tomar la máquina.

#### Estados

De manera intuitiva se podría pensar que los estados de la máquina son todas las posibles combinaciones que pueden haber entre las luces de los semáforos, sin embargo esto no es cierto, ya que hay una restricción de que solo puede haber un semáforo en verde a la vez; así que en base a esto definimos nuestros 4 primero estados:

1. Semáforo A en verde y B, C, D en rojo (E0)
2. Semáforo B en verde y A, C, D en rojo (E2)
3. Semáforo C en verde y A, B. D en rojo (E4)
4. Semáforo D en verde y A, B, C en rojo (E6)

 Con esto nos percatamos que los estados restantes corresponden a la transición entre cada uno de los 4 estados, siendo los siguientes:

5. Semáforo A y B en amarillo y C y D en rojo (E1)
6. Semáforo A y C en amarillo y B y D en rojo (E9)
7. Semáforo A y D en amarillo y B y C en rojo (E8)
8. Semáforo B y C en amarillo y A y D en rojo (E3)
9. Semáforo B y D en amarillo y A y C en rojo (E7)
10. Semáforo C y D en amarillo y A y B en rojo (E5)

Obteniendo un total de 10 estados

#### Transición de estados

Empezamos por el diagrama de transición de estados

![Diagrama de transición de estados](IMAGENES_PF/DTS.png "Diagrama de transición de estados")

Para codificar los estados vamos a usar binario obteniendo la siguiente tabla

![Código de estados](IMAGENES_PF/CES.JPG "Código de estados")

Con base a la codificación nos damos cuenta de que necesitamos 4 Flip-Flops para nuestra máquina de estados

Con esto ya podemos armar nuestra tabla de transición de estados

![Tabla de transición de estados](IMAGENES_PF/TTS.JPG "Tabla de transición de estados")

Las ecuacioes de $Q0'\; \; \; Q1'\; \; \; Q2'\; \; \; Q3'$ las obtenemos a partir de la suma de productos (SoP), también tenemos en cuenta la tabla de transición y la tabla de excitación de los diferentes Flip-Flop; y se determinó que los Flip-Flop que generan ecuaciones con menos términos, son Flip-Flop tipo D para $Q0' \; \; \; Q3'$ y Flip-Flop tipo JK para $Q1' \; \; \; Q2'$.

