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
