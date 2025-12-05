## Proceso de flasheo de ADuCM3029
La adicup3029 tiene un problema. La memoria flash le queda con basura y el modo de limpiarlo es usando un programa que se llama Cosscore Serial Flash Programmer.
El proceso de flasheo se llevó a cabo con la computadora de Natalia debido a inconvenientes de instalación en pc de Elías (Linux).

## Primer intento
El proceso de flasheo fracasó en placa 2020 y 2024, se probó con cambiar el puerto y los baudios (rango entre 2400 a 115200) pero el programa arrojó siempre los mismos resultados.

| **Target**           | ADuCM302x                                                                                                     |
| :------------------- | ------------------------------------------------------------------------------------------------------------- |
| **Serial Port**      | COM6 (Dispositivo serie USB)                                                                                  |
| **Baudrate**         | 115200                                                                                                        |
| **Action**           | Erase                                                                                                         |
| **Key**              | ---------------------------------------------------                                                           |
| **File to download** | ---------------------------------------------------                                                           |
| **Status**           | Sending second stage kernel.<br>  Read Intel HEX application image with 668 bytes.<br>  No autobaud response. |

## Chequeo de luces
Se fueron conectando la placa 2020 y la placa 2024 a la pc de Natalia para comprobar si en ambas placas se encendían las mismas luces.
### Placa 2020:
DS1 (color verde)
DS2 (color rojo)
DS3 (color verde)
DS4 (color azul)

![[Placa 2020.png]]

### Placa 2024:
DS1 (color verde)
DS2 (color rojo)
DS3 (color verde) parpadeaba
![[Placa 2024.png]]

## Segundo intento
Se utilizó la placa 2020 de nuevo, se leyó la [Adicup3029 Hardware User Guide](https://wiki.analog.com/resources/eval/user-guides/eval-adicup3029/hardware/adicup3029), y se siguieron los pasos recomendados en la sección `Function` → `Push Buttons` → `3039_BOOT`.

| **Button** | **Function**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| :--------- | :----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 3029_BOOT  | When BOOT is held down during the RESET button press and moments afterwards, the ADuCM3029 microcontroller enters UART download mode via P0_10 and P0_11. In this case, the user can download a program via the USB using the CrossCore Serial Flash Programmer tool, just make sure the UART switch (S2) is in the correct “USB” position.(See [UART Switch](https://wiki.analog.com/resources/eval/user-guides/eval-adicup3029/hardware/adicup3029#uart_switch "resources:eval:user-guides:eval-adicup3029:hardware:adicup3029") section for more details) |

Con el programa CrossCore Serial Flash Programmer se logró flashear la placa.
A continuación se detallan resultados:

### Placa 2020

| **Target**           | ADuCM302x                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| :------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **Serial Port**      | COM6 (Dispositivo serie USB)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| **Baudrate**         | 115200                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| **Action**           | Erase                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| **Key**              | -----------------------------------------------------------                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| **File to download** | -----------------------------------------------------------                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| **Status**           | Sending second stage kernel.<br>  Read Intel HEX application image with 668 bytes.<br>  Received autobaud response<br>    Product ID ADuCM302x      <br>    Revision 431<br>    Serial number 1176E58BF9F5D98301AFA00043430333<br>    User code present.<br>    User code checksum failed.<br>    Write protection disabled.<br>    Read protection disabled.<br>  Sent 668/668 bytes.<br>  Download completed.<br>  Run command sent.<br>Erasing flash.<br>  Autobaud succeeded.<br>  Erase succeeded.<br>  Done. |


## Placa 2024
Mismo procedimiento que se le aplicó a la placa 2020.
Durante el flasheo la luz DS4 (color azul) se encendió y la luz DS3 (verde) dejó de parpadear.

| **Target**           | ADuCM302x                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| :------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **Serial Port**      | COM6 (Dispositivo serie USB)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| **Baudrate**         | 115200                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| **Action**           | Erase                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| **Key**              | -----------------------------------------------------------                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| **File to download** | -----------------------------------------------------------                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| **Status**           | Sending second stage kernel.<br>  Read Intel HEX application image with 668 bytes.<br>  Received autobaud response<br>    Product ID ADuCM302x      <br>    Revision 431<br>    Serial number 11F6E588FCE0C793757FB00043430333<br>    User code present.<br>    User code checksum failed.<br>    Write protection disabled.<br>    Read protection disabled.<br>  Sent 668/668 bytes.<br>  Download completed.<br>  Run command sent.<br>Erasing flash.<br>  Autobaud succeeded.<br>  Erase succeeded.<br>  Done. |
