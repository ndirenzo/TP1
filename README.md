# TP1 - Sistemas Embebidos - Facultad de Ingeniería Universidad de Buenos Aires 10 de Mayo 2022

## Integrantes Grupo 1 : N.Direnzo, G.Pintos, J.González, M.Pintos

### Ejemplo 1
En este diagrama lo que se realiza es un encendido permanente del led número 3 (verde) de la placa EDU-CIAA.

![alt text](https://github.com/ndirenzo/TP1/blob/main/Diagramas/Diagrama%20Ejemplo%201.PNG?raw=true)

### Ejemplo 2
En este diagrama se le agrega parpadeo al LED 3. El mismo comienza la secuencia en estado apagado, trasncurrido 250ms se enciende, permanece encenido 500ms y se apaga nuevamente. Esta secuencia se repite indefiniamente. Tenemos entonces un periodo de 750ms y un Duty Cicle de 500ms/750ms=2/3


![alt text](https://github.com/ndirenzo/TP1/blob/main/Diagramas/Diagrama%20Ejemplo%202.PNG?raw=true)

### Ejemplo 3
En este diagrama se le agrega un estado de reposo. El programa comienza en reposo y permanece allí durante 3 segundos, momento en el cuál ingresa en un ciclo de parpadeo que dura 5 segundos con el mismo periodo y Duty cicle que el anterior.

![alt text](https://github.com/ndirenzo/TP1/blob/main/Diagramas/Diagrama%20Ejemplo%203.PNG?raw=true)

### Ejemplo 4
En este diagrama se comienza con el estado que indica el botón no oprimido. Cuando se omprime el botón por primera vez, el programa lo detecta y lo denomina en principio como "debounce", allí espera 100ms y realiza la validación. Si el botón continua siendo oprimido luego de este tiempo, se enciende el led 3, pero si no se encontraba opimido no se enciende y vuelve al estado no oprimido. Una vez encendido el led solo se apaga omprimiendo nuevamente el botón. Esto en la practica significa que si apretamos rapidamente el botón, el led no se encenderá. Para que se encienda la opresión debe ser prolongada durante el menos 100ms.

![alt text](https://github.com/ndirenzo/TP1/blob/main/Diagramas/Diagrama%20Ejemplo%204.PNG?raw=true)

### Ejemplo 5
En este ultimo ejemplo se tiene por un lado el diagrama de la validación del botón del ejemplo 4_Buttons y por otro el ciclo realizado en el ejemplo 3_idleBlink. Esta manejado por un diagrama principial que verifica que los botones hayan sido oprimidos correctamente: Si se oprimio el botón 2 enciende el led 1, si se oprimio el botón 3 enciende el led 2, si se oprimio el botón 4 hace parpadear el led 3. Ahora, si se oprimio el botón 1, lo que hace es apagar los 3 leds.

![alt text](https://github.com/ndirenzo/TP1/blob/main/Diagramas/Diagrama%20Ejemplo%205a.PNG?raw=true)

![alt text](https://github.com/ndirenzo/TP1/blob/main/Diagramas/Diagrama%20Ejemplo%205b.PNG?raw=true)
