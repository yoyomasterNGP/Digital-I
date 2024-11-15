# COMPARACIÓN DE TECNOLOGÍA CMOS y TTL
- Nicolás Garzón Peña
- 2
- 3
___
# Cálculos y simulaciones
## Negador TTL 74LS04

Para el TTL vamos a utilizar una alimentación de 5V.

### Características DC

Vamos a analizar los valores $V_{IH}, V_{IL}$; para ello variamos la señal de entrada de 0V a 5V $(V_{in})$ y la comparamos con una señal de salida $(V_{out})$ que será el voltaje sobre una carga de $10k\Omega$ en la salida del negador. Cuando el voltaje de salida pase de bajo a alto nos indicará el $V_{IL}$ y cuando pase de alto a bajo nos indicará el $V_{IH}$.
![DC TTL](IMAGENES/DC_TTL.jpg "DC TTL")

### Características AC

Vamos a analizar los tiempos de retardo $(t_{PLH}, t_{PHL})$ y tiempos de almacenamiento $(t_{THL}, t_{TLH})$, para ello la entrada será una señal cuadrada de 1kHz con un tiempo de subida y de bajado de 20 ns, y la salida nuevamente será una carga de $10k\Omega$.
![AC TTL](IMAGENES/AC_A_TTL.jpg "AC TTL")
