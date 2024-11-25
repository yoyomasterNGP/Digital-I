# COMPARACIÓN DE TECNOLOGÍA CMOS y TTL
| Electrónica Digital I | Grupo 4 | Equipo 3 |
|------------------------|---------|----------|

- Nicolás Garzón Peña
- José Alejandro López Vargas
- Johan Stiven Tovar López
___

En la electrónica digital, las tecnologías TTL y CMOS destacan por sus características y aplicaciones. Este informe se enfoca en comparar estos negadores mediante el análisis de parámetros clave, como tiempos de respuesta, niveles de tensión y disipación de potencia, utilizando, en primer lugar, los valores nominales proporcionados en los datasheets, luego simulaciones en Qucs y finalmente comparando estos datos con las mediciones experimentales.

# Especificaciones técnicas

En esencia, los dos **negadores** a utilizar son puertas lógicas que invierten el valor de su entrada: si recibe un `1`, entrega un `0`, y viceversa. Es un pilar para formar otras compuertas lógicas.  

 | Entrada (A) | Salida (¬A) |
|-------------|-------------|
| 0           | 1           |
| 1           | 0           |

Sin embargo, estas salidas y entradas están situadas dentro de intervalos de voltaje especificos en cada tecnología, cómo se vera posteriormente.

## Negador TTL 74LS04
Los **TTL (Transistor-Transistor Logic):** se usan en sistemas de alta velocidad, como computadoras y controladores industriales. Su hoja de especificaciones es:

![Especificaciones TTL](IMAGENES/74LS04.jpg "Hoja de especificaciones")

Además, el circuito equivalente dado en los datasheets del dispositivo es:

![TTL Circuit](IMAGENES/circuit_diagram_ttl.jpg "Circuito equivalente 74LS04")

## Negador CMOS CD4069
Los **CMOS (Complementary Metal-Oxide-Semiconductor):** Ideal para dispositivos de bajo consumo, como celulares y sensores portátiles. Su hoja de especificaciones es:

![Especificaciones CMOS](IMAGENES/AC_cmos_spec.jpg "Hoja de especificaciones AC")

![Especificaciones CMOS](IMAGENES/DC_cmos_spec.jpg "Hoja de especificaciones DC")

Además, el circuito equivalente dado en los datasheets del dispositivo es:

![CMOS circuit](IMAGENES/circuit_diagram_cmos.jpg "Circuito equivalente CD4069")

Como podemos observar, existen diferencias notables entre estos dos dispositivos. La más evidente es la complejidad de sus circuitos equivalentes. La tecnología TTL utiliza una variedad de transistores BJT (transistor bipolar de unión), y en la variante TTL Schottky, se incorporan diodos Schottky para mejorar la velocidad de conmutación. Por otro lado, la tecnología CMOS es mucho más sencilla, utilizando únicamente dos transistores, uno NMOS y otro PMOS.

Estas diferencias en la topología de los circuitos tienen repercusiones que se evidencian en las tablas mostradas. Por ejemplo, los tiempos de conmutación (tPLH y tPHL) son generalmente más rápidos en la tecnología TTL debido a los transistores Schottky. Además, los niveles de voltaje manejados en la tecnología TTL son más altos, ya que es necesario alimentar una mayor variedad de componentes. En cambio, la tecnología CMOS, al ser más sencilla, consume mucho menos energía.

# Cálculos y simulaciones
## Negador TTL 74LS04

Para el TTL vamos a utilizar una alimentación de 5V.

### Características DC

Vamos a analizar los valores $V_{IH}, V_{IL}, V_{OH}, V_{OL}$; para ello variamos la señal de entrada de 0V a 5V $(V_{in})$ y la comparamos con una señal de salida $(V_{out})$ que será el voltaje sobre una carga de $10k\Omega$ en la salida del negador. Cuando el voltaje de salida pase de bajo a alto nos indicará el $V_{IL}$ y cuando pase de alto a bajo nos indicará el $V_{IH}$ y el voltaje de salida corresponde a $V_{OH}$ y $V_{OL}$.
![DC TTL](IMAGENES/DC_TTL.JPG "DC TTL")

$$
\begin{align}
V_{IH}=2.5V\\
V_{IL}=2.5V\\
V_{OH}=3.34V\\
V_{OL}=0V
\end{align}
$$

### Características AC

Vamos a analizar los tiempos de retardo $(t_{PLH}, t_{PHL})$ y tiempos de almacenamiento $(t_{THL}, t_{TLH})$, para ello la entrada será una señal cuadrada de 1kHz con un tiempo de subida y de bajado de 20 ns, y la salida nuevamente será una carga de $10k\Omega$.
![AC TTL](IMAGENES/AC_R_HL_TTL.JPG "Tiempo de retardo TTL HL")
![AC TTL](IMAGENES/AC_R_LH_TTL.JPG "Tiempo de retardo TTL LH")
![AC TTL](IMAGENES/AC_A_HL_TTL.JPG "Tiempo de almacenamiento TTL HL")
![AC TTL](IMAGENES/AC_A_LH_TTL.JPG "Tiempo de almacenamiento TTL LH")

$$
\begin{align}
t_{PHL}=8ns\\
t_{PLH}=8ns\\
t_{THL}=2ns\\
t_{TLH}=2ns
\end{align}
$$

### Fan - Out

Para el Fan - Out vamos a tomar como referencia el $V_{OH}$ del datsheet el cual es de 2.7V; la entrada será de 0V y la carga a la salida será una resistencia variable. Cuando la tensión a la salida sea de $V_{OH}$ el Fan - Out corresponde a la corriente de salida.
![AC TTL](IMAGENES/FO_TTL.JPG "Tiempo de almacenamiento TTL LH")

Obtenemos un Fan - Out de $459\mu A$


## Negador CMOS CD4069

Para el CMOS vamos a utilizar una alimentación de 5V.

### Características DC

Vamos a analizar los valores $V_{IH}, V_{IL}, V_{OH}, V_{OL}$; para ello variamos la señal de entrada de 0V a 5V $(V_{in})$ y la comparamos con una señal de salida $(V_{out})$ que será el voltaje sobre una carga de $10k\Omega$ en la salida del negador. Cuando el voltaje de salida pase de bajo a alto nos indicará el $V_{IL}$ y cuando pase de alto a bajo nos indicará el $V_{IH}$ y el voltaje de salida corresponde a $V_{OH}$ y $V_{OL}$.
![DC TTL](IMAGENES/DC_CMOS.JPG "DC CMOS")

$$
\begin{align}
V_{IH}=2.5V\\
V_{IL}=2.5V\\
V_{OH}=4.72V\\
V_{OL}=0V
\end{align}
$$

### Características AC

Vamos a analizar los tiempos de retardo $(t_{PLH}, t_{PHL})$ y tiempos de almacenamiento $(t_{THL}, t_{TLH})$, para ello la entrada será una señal cuadrada de 1kHz con un tiempo de subida y de bajado de 20 ns, y la salida nuevamente será una carga de $10k\Omega$.
![AC TTL](IMAGENES/AC_R_HL_CMOS.JPG "Tiempo de retardo TTL HL")
![AC TTL](IMAGENES/AC_R_LH_CMOS.JPG "Tiempo de retardo TTL LH")
![AC TTL](IMAGENES/AC_A_HL_CMOS.JPG "Tiempo de almacenamiento TTL HL")
![AC TTL](IMAGENES/AC_A_LH_CMOS.JPG "Tiempo de almacenamiento TTL LH")

$$
\begin{align}
t_{PHL}=138ns\\
t_{PLH}=138ns\\
t_{THL}=2ns\\
t_{TLH}=2ns
\end{align}
$$

### Fan - Out

Para el Fan - Out vamos a tomar como referencia el $V_{OH}$ del datsheet el cual es de 4.95V; la entrada será de 0V y la carga a la salida será una resistencia variable. Cuando la tensión a la salida sea de $V_{OH}$ el Fan - Out corresponde a la corriente de salida.
![AC TTL](IMAGENES/FO_CMOS.JPG "Tiempo de almacenamiento TTL LH")

Obtenemos un Fan - Out de $98.8\mu A$

## Oscilador en anillo

![AC TTL](IMAGENES/AO_3.JPG "Tiempo de almacenamiento TTL LH")

![AC TTL](IMAGENES/AO_5.JPG "Tiempo de almacenamiento TTL LH")

# Resultados Experimentales 
## Negador CMOS CD4069

### Tiempo de Almacenamiento
![ALmacenamiento CMOS](IMAGENES/Almacenamiento_CMOS.jpeg "Tiempo de almacenamiento CMOS")

$TPLH = 64.00ns$


### Tiempo de Delay
![Delay CMOS](IMAGENES/Delay_CMOS.jpeg "Tiempo de Delay CMOS")

$TPHL = 32.00ns$

### Características de voltaje

 | Parámetro | Valor nominal (Datasheet) | Valor experimental | Error porcentual
|-------------|-------------|-----------|------------|--------
| $V_{ol} $           | 1           |
| 1           | 0           |

Las fotos de las mediciones se encuentran en: %%%liiink docs





## Negador TTL 74LS04

### Tiempo de Almacenamiento
![ALmacenamiento TTL](IMAGENES/Almacenamiento_TTL.jpeg "Tiempo de almacenamiento TTL")

$TPLH = 26.00ns$


### Tiempo de Delay
![Delay TTL](IMAGENES/Delay_TTL.jpeg "Tiempo de Delay TTL")
$TPHL = 22.00ns$

## Oscilador en Anillo CMOS

### Oscilador de 2 compuertas lógicas


