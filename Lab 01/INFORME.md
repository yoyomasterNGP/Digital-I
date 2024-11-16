# COMPARACIÓN DE TECNOLOGÍA CMOS y TTL
- Nicolás Garzón Peña
- 2
- 3
___
# Cálculos y simulaciones
## Negador TTL 74LS04

Para el TTL vamos a utilizar una alimentación de 5V.

### Características DC

Vamos a analizar los valores $V_{IH}, V_{IL}, V_{OH}, V_{OL}$; para ello variamos la señal de entrada de 0V a 5V $(V_{in})$ y la comparamos con una señal de salida $(V_{out})$ que será el voltaje sobre una carga de $10k\Omega$ en la salida del negador. Cuando el voltaje de salida pase de bajo a alto nos indicará el $V_{IL}$ y cuando pase de alto a bajo nos indicará el $V_{IH}$ y el voltaje de salida corresponde a $V_{OH}$ y $V_{OL}$.
![DC TTL](IMAGENES/DC_TTL.JPG "DC TTL")

$$
V_{IH}\\
V_{IL}\\
V_{OH}\\
V_{OL}
$$

### Características AC

Vamos a analizar los tiempos de retardo $(t_{PLH}, t_{PHL})$ y tiempos de almacenamiento $(t_{THL}, t_{TLH})$, para ello la entrada será una señal cuadrada de 1kHz con un tiempo de subida y de bajado de 20 ns, y la salida nuevamente será una carga de $10k\Omega$.
![AC TTL](IMAGENES/AC_R_HL_TTL.JPG "Tiempo de retardo TTL HL")
![AC TTL](IMAGENES/AC_R_LH_TTL.JPG "Tiempo de retardo TTL LH")
![AC TTL](IMAGENES/AC_A_HL_TTL.JPG "Tiempo de almacenamiento TTL HL")
![AC TTL](IMAGENES/AC_A_HL_TTL.JPG "Tiempo de almacenamiento TTL LH")

### Fan - Out

Para el Fan - Out vamos a tomar como referencia el $V_{OH}$ el cual es de 2.7V; la entrada será de 0V y la carga a la salida será una resistencia variable. Cuando la tensión a la salida sea de $V_{OH}$ el Fan - Out corresponde a la corriente de salida.
![AC TTL](IMAGENES/FO_TTL.JPG "Tiempo de almacenamiento TTL LH")

### Fan - In




## Negador CMOS CD4069

Para el CMOS vamos a utilizar una alimentación de 5V.

### Características DC

Vamos a analizar los valores $V_{IH}, V_{IL}, V_{OH}, V_{OL}$; para ello variamos la señal de entrada de 0V a 5V $(V_{in})$ y la comparamos con una señal de salida $(V_{out})$ que será el voltaje sobre una carga de $10k\Omega$ en la salida del negador. Cuando el voltaje de salida pase de bajo a alto nos indicará el $V_{IL}$ y cuando pase de alto a bajo nos indicará el $V_{IH}$ y el voltaje de salida corresponde a $V_{OH}$ y $V_{OL}$.
![DC TTL](IMAGENES/DC_CMOS.JPG "DC CMOS")

### Características AC

Vamos a analizar los tiempos de retardo $(t_{PLH}, t_{PHL})$ y tiempos de almacenamiento $(t_{THL}, t_{TLH})$, para ello la entrada será una señal cuadrada de 1kHz con un tiempo de subida y de bajado de 20 ns, y la salida nuevamente será una carga de $10k\Omega$.
![AC TTL](IMAGENES/AC_R_HL_CMOS.JPG "Tiempo de retardo TTL HL")
![AC TTL](IMAGENES/AC_R_LH_CMOS.JPG "Tiempo de retardo TTL LH")
![AC TTL](IMAGENES/AC_A_HL_CMOS.JPG "Tiempo de almacenamiento TTL HL")
![AC TTL](IMAGENES/AC_A_HL_CMOS.JPG "Tiempo de almacenamiento TTL LH")

### Fan - Out

Para el Fan - Out vamos a tomar como referencia el $V_{OH}$ el cual es de 2.7V; la entrada será de 0V y la carga a la salida será una resistencia variable. Cuando la tensión a la salida sea de $V_{OH}$ el Fan - Out corresponde a la corriente de salida.
![AC TTL](IMAGENES/FO_TTL.JPG "Tiempo de almacenamiento TTL LH")

### Fan - In
