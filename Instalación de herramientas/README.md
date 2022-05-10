# Paquete de herramientas listas para usar para la programación de las plataformas del Proyecto CIAA

## Herramientas contenidas

- Lanzador de aplicaciones.
- Entornos de programación en lenguaje C/C++:
     - [Embedded IDE.](embedded-ide/README.md)
     - [GNU MCU Eclipse.](eclipse/README.md)
 - [IDE4PLC](ide4plc/README.md). Entorno de programación en lenguaje Ladder Diagram (IEC 61131-3).
 - [CIAABOT IDE](ciaabot-ide/README.md). Entorno de programcación en lenguaje CIAABOT (basado en Blockly).
 - GNU ARM Embedded. Toolchain.
 - OpenOCD. Programación y depuración.
 - Zenity. Generación de interfaces gráficas.

### Herramientas adicionales en la versión de Windows

 - Terminal bpp, versióon 1.93b 20141030. Terminal serie.
 - Busybox.

### Herramientas adicionales en la versión de Linux

 - GTKterm.
 - Cutecom.
 - Git.

## Utilización

Debe descargar de [releases](https://github.com/epernia/software/releases/tag/r1.1.0) la versión para Windows o Linux.

**NOTA: No tiene sentido clonar este repositorio porque solamente incluye documentación, el software está incluído en las releases.**

Descomprimir la carpeta en una ruta conocida, sin espacios y con los permisos adecuados. Se recomiendan:

- **Windows**. C:\CIAA\
- **Linux**. $HOME/CIAA/

Luego ingresar a la carpeta y ejecutar el lanzador de apliaciones. 

**Nota:** Este lanzador *es necesario* debido a que se ejecutan los programas directamente sin utilizarlo les faltará a los mismos rutas necesarias en variable de entorno PATH.

**Lanzador de aplicaciones en Windows**

![launcher1-win](applauncher/docs/CIAA-folder-win.png)

Desde el lanzador puede ejecutar cualquiera de los programas desde los accesos:

![launcher-win](applauncher/docs/launcher-win.png)

**Primera vez en Windows**

La primera vez debe instalar los **drivers FTDI VCP** (desde el icono del lanzador de aplicacciones) para la EDU-CIAA-NXP o CIAA-NXP:

![FTDI-Win](applauncher/docs/FTDI-Win.png)

Presione "Extract" y luego instale el driver con todas las opciones por defecto.

Luego reemplazar el driver del dispositivo *Dual RS232HS (Interface 0)* con **Zadig**. Para lograrlo debe abrir zadig desde el lanzador de aplicaciones y luego en el menú "Optinos" presionar sobre "List all devices". En el combo seleccione el dispositivo "Dual RS232HS (Interface 0)" y presionar el botón "Replace Driver":

![Zadig-Win](applauncher/docs/Zadig-Win.png)

**Lanzador de aplicaciones en Linux**

![launcher1-linux](applauncher/docs/CIAA-folder-linux.png)

Desde el lanzador puede ejecutar cualquiera de los programas desde los accesos:

![launcher-linux](applauncher/docs/launcher-linux.png)

**Primera vez en Linux**

La primera vez debe instalar varias herramientas y programas necesarios mediante el icono **Install tools** del lanzador de aplicacciones (se requiere contraseña de administrador para este paso).

**NOTA para Ubuntu 20.04**: El entorno funciona correctamente en Ubuntu 18.04. Para que funcione en Ubuntu 20.04 deberá:

1. Descargar el paquete libgconf-2-4 (en lugar de libgconf2-4, es muy sutil la diferencia de nombres)
2. Cambiar el link simbólico de librt.so.1 de librt-2.19.so a librt-2.31.so

Esto se logra ejecutando los siguientes comandos en una terminal:

```
sudo apt install libgconf-2-4
cd $HOME/CIAA/CIAA_Software_1.1-linux-x64/tools/openocd/bin
cp /usr/lib/x86_64-linux-gnu/librt-2.31.so .
ln -sfn librt-2.31.so librt.so.1
```

Puede que tenga que reemplazar $HOME por la ruta a su usuario.

## Repositorios de frameworks para la programación de las plataformas CIAA en C/C++

Se recomienda la utilización del último repositorio. Actualmente Firmware v3. Los disponibles son:

- [firmware_v3.](https://github.com/epernia/firmware_v3)
- [firmware_v2.](https://github.com/ciaa/firmware_v2)
- [firmware_v1.](https://github.com/ciaa/firmware_v1)


# Utilización de firmware_v3 con Eclipse

## 1. Abrir proyecto firmware_v3 en Eclipse

### 1.1. Abrir proyecto firmware_v3 en Eclipse por primera vez

#### 1.1.1. Iniciar Eclipse

Recordar iniciar Eclipse desde el Launcher. Esto traerá las variables de entorno necesarias para ubicar las herramientas externas para compilación y depuración.

#### 1.1.2. Workspace

Al abrir el Eclipse solicita seleccionar la carpeta a utilizar como espacio de trabajo (*Workspace*), elegir dentro de la ruta donde descomprimieron el Launcher la carpeta:

```
<rutaDondeDescomprimiElLauncher>/workspaces/eclipse-ws
```

![Eclipse-01](Eclipse-Win01.png)

#### 1.1.3. Ventana inicial

Al iniciar el Eclipse muestra una pestaña de bienvenida (*Wellcome*) como la siguiente:

![Eclipse-02](Eclipse-Win02.png)

Debe cerrar esta pestaña para que se muestre el árbol de proyectos y el espacio del editor de archivos:

![Eclipse-03](Eclipse-Win03.png)

#### 1.1.4. Abrir Proyecto de Firmware para programar en asembler, C o C++

Primero debemos clonar o descargar el Proyecto a abrir, en este caso firmware_v3:

https://github.com/epernia/firmware_v3

Ubicar la carpeta Firmware v3 dentro de la carpeta del Launcher. 

Luego en Eclipse ir al menú:

```
New --> Makefile Project with Existing Code
```

![Eclipse-04](Eclipse-Win04.png)

En la ventana que se abre deberá:

- Elegir mediante "Browse" la carpeta ```firmware_v3```
- Tildar en Languages ```C``` y ```C++```
- Elegir como Toolchain ```ARM Cross GCC```

![Eclipse-05](Eclipse-Win05.png)

Una vez realizado presione "Finish" y verá el Proyecto "firmware_v3" en el árbol de proyectos:

![Eclipse-06](Eclipse-Win06.png)

Con esto queda el proyecto firmware_v3 listo para su utilización. 

**Nota**: Eclipse puede tener múltiples proyectos en simultáneo dentro de un mismo *Workspace*. En particular, el proyecto *firmware_v3 es un único proyecto que se compone de múltiples programas* (los ejemplos que trae más los programas que realizaremos nosotros). Es decir con un único proyecto de Eclipse abierto tendremos la posibilidad de seleccionar que programa del mismo se desea compilar y descargar a la plataforma de hardware.

### 1.2. Abrir proyecto firmware_v3 en Eclipse en sucesivas ocasiones

Eclipse guarda todas las configuraciones realizadas sobre la carpeta elegida como *Workspace* con y de esta manera al abrir nuevamente Eclipse y seleccionar el *Workspace* que hemos creado se cargará el proyecto firmware_v3 automáticamente.

## 2. Compilar proyecto firmware_v3 en Eclipse

### 2.1. Configurar opciones de compilación

Se debe hacer click derecho sobre el proyecto "firmware_v3" y luego en la opción "*Properties*":

![Eclipse-07](Eclipse-Win07.png)

En la ventana que se abre debe hacer click sobre "*C/C++ Build*" y en la parte derecha debe:

- Destildar la opción "*Use default build command*".
- En "*Build command*" escribir ```make``` en el campo de texto.

Presionar *"Apply and Close*" para aplicar la configuración.

![Eclipse-08](Eclipse-Win08.png)

### 2.2. Configurar rutas y símbolos

El programa compilará correctamente si no se realiza este paso pero puede confundir al usuario pensando que existen muchos errores donde en realidad no los hay. Esto se debe a que Eclipse busca automáticamente los símbolos y si no los encuentra los subraya en rojo como errores aunque no lo sean.
Eclipse marcará subrayados en rojo tipos de datos estandar (por ejemplo, ```uint8_t```), constantes definidas en las bibliotecas (ejemplo, ```LED``` de sAPI), entre otros.
Para solucionar esto deberá hacer click derecho sobre el proyecto "firmware_v3" y luego en la opción "*Properties*". 
En la ventana que se abre debe:

1. Hacer click sobre la flecha de la opción *"C/C++ General"* para desplegrar el menú.
2. Hacer click en la opción *"Preprocessor Include Paths, Macross, etc."*.
3. En el área a la derecha que se abre clickear sobre la tab *"Providers"*.
4. Tildar el checkbox *"CDT ARM Cross GCC Built-in Compiler Settings"*.
5. Bajo la lista de checkboxes en el campo de texto *"Command to get compiler specs"* deberá ingresar un comando muy largo que incluye todos los CFLAGS. Este comando se pueden obtener ejecutando en una Terminal (en Linux) o (Busybox en Windows) el comando ```make .print_eclipse_cfg``` desde la raiz de la carpeta firmware_v3. Este comando cambia en base a cambios en las bibliotecas (carpeta libs), cambios de plataforma (BOARD) defines de compilación condicional. En estos casos deberá actualizar este campo.
6. Presionar *"Apply"* para aplicar la configuración.
7. Presionar *"Apply and Close"* para aplicar la configuración y cerrar la ventana de propiedades.

![Eclipse-23](Eclipse-Win23.png)

Captura del comando ```make .print_eclipse_cfg``` en Windows:

![Eclipse-24](Eclipse-Win24.png)

En este caso se debe copiar:

```
arm-none-eabi-gcc -mcpu=cortex-m4 -mthumb -mfloat-abi=hard -mfpu=fpv4-sp-d16 -D__USE_LPCOPEN -DCHIP_LPC43XX -DARM_MATH_CM4 -D__USE_NEWLIB -DCORE_M4 -D__FPU_PRESENT=1U -DUSE_SAPI -Ilibs/arduino//inc -Ilibs/cmsis_core//inc -Ilibs/cmsis_dsp//inc -Ilibs/editline//inc -Ilibs/fatfs//inc -Ilibs/freertos//inc -Ilibs/lpc_fatfs_disks//inc -Ilibs/lpc_open//inc -Ilibs/lpcusblib//inc -Ilibs/minut//inc -Ilibs/plc//inc -Ilibs/rkh//inc -Ilibs/sapi//inc -Ilibs/seos_pont_2014//inc -Ilibs/sys_newlib//inc -Ilibs/tinyprintf//inc -Iexamples/c/sapi/lcd/lcd_gpio/inc -Ilibs/lpc_open/boards/edu_ciaa_nxp/inc -Ilibs/lpc_open/boards/inc -Ilibs/lpc_open/lpc_chip_43xx/inc -Ilibs/lpc_open/lpc_chip_43xx/usbd_rom -Ilibs/lpc_open/lpc_startup/inc -Ilibs/sapi/sapi_v0.6.2/base/inc -Ilibs/sapi/sapi_v0.6.2/soc/core/inc -Ilibs/sapi/sapi_v0.6.2/soc/peripherals/inc -Ilibs/sapi/sapi_v0.6.2/soc/peripherals/usb/device/inc -Ilibs/sapi/sapi_v0.6.2/soc/peripherals/usb/host/inc -Ilibs/sapi/sapi_v0.6.2/board/inc -Ilibs/sapi/sapi_v0.6.2/abstract_modules/inc -Ilibs/sapi/sapi_v0.6.2/external_peripherals/display/fonts/inc -Ilibs/sapi/sapi_v0.6.2/external_peripherals/display/fonts/greek_chars_5x7/inc -Ilibs/sapi/sapi_v0.6.2/external_peripherals/display/fonts/icon_chars_5x7/inc -Ilibs/sapi/sapi_v0.6.2/external_peripherals/display/lcd/inc -Ilibs/sapi/sapi_v0.6.2/external_peripherals/display/led_segments/7segment/inc -Ilibs/sapi/sapi_v0.6.2/external_peripherals/imu/mpu60X0/inc -Ilibs/sapi/sapi_v0.6.2/external_peripherals/imu/mpu9250/inc -Ilibs/sapi/sapi_v0.6.2/external_peripherals/keypad/inc -Ilibs/sapi/sapi_v0.6.2/external_peripherals/led_rgb/inc -Ilibs/sapi/sapi_v0.6.2/external_peripherals/magnetometer/hmc5883l/inc -Ilibs/sapi/sapi_v0.6.2/external_peripherals/magnetometer/qmc5883l/inc -Ilibs/sapi/sapi_v0.6.2/external_peripherals/memory/eeprom/inc -Ilibs/sapi/sapi_v0.6.2/external_peripherals/motor/servo/inc -Ilibs/sapi/sapi_v0.6.2/external_peripherals/temperature_humudity/dht11/inc -Ilibs/sapi/sapi_v0.6.2/external_peripherals/ultrasonic/hcsr04/inc -Ilibs/sapi/sapi_v0.6.2/external_peripherals/wifi/esp8266_at/inc -ggdb3 -Og -ffunction-sections -fdata-sections -DBOARD=edu_ciaa_nxp -std=c99 -E -P -v -dD "${INPUTS}"
```

### 2.3. Compilar proyecto

Para compilar el proyecto puede realizarlo mediante el icono del martillo (*Build*), o mediante la opción "*Build*" presionando el botón derecho sobre el proyecto firmware_v3.

![Eclipse-09](Eclipse-Win09.png)

**Nota**: firmware_v3 compilará el programa que tenga seleccionado para compilar, si es la primera vez compilará el ejemplo seleccionado por defecto.

Al presionar "*build*" se compila el proyecto dando como resultado lo siguiente:

![Eclipse-10](Eclipse-Win10.png)

**Nota:** observe que se ve: 

- Los bytes ocupados en cada área de memoria (ver apunte de printf() y scanf() para comprenderlo).
- El programa que fue compilado dentro del proyecto, en este caso llamado "app" en la carpeta "examples/c" dentro de "firmware_v3".
- La plataforma de hardware para la cual se compiló el programa, en este caso "EDU-CIAA-NXP".

## 3. Configurar y ejecutar *targets* de de *makefile* en Eclipse

### 3.1. Targets por defecto en Eclipse

Eclipse muestra algunos de sus *targets* de diferentes maneras:

- El *target* **all** como el "botón del martillo" (***Build project***) accesible desde el menú superior.

  ![targets buttons](targets-01.png)

El botón ***build*** ejecuta el comando:

`make all` 

- Si se presiona botón derecho del *mouse* sobre el proyecto firmware_v3 se muestran como opciones del menú contextual:

  - ***Build Project.*** Ejecuta el comando `make all` 
  - ***Clean Project.*** Ejecuta el comando `make clean` 

  ![targets context](targets-02.png)

- Además se pueden configurar y agregar *targets* adicionales como se explica en la siguiente sección.

### 3.2. Configurar *targets* de de *makefile* en Eclipse

Para agregar botones para ejecutar *targets* de de *makefile* en Eclipse se debe ir a la pestaña ***Build Targets*** (1), luego presionar en la carpeta ***firmware_v3*** (2) y luego presionar el botón ***New Build Target*** (3):

![targets config 01](targets-03.png)

De esta forma se abre un formulario donde se agrega el nuevo target. Por ejemplo, para agregar el *target download*:

![targets excec 01](targets-04.png)

De esta forma el target queda accesible como un botón en eclipse como se muestra a continuación:

![targets excec 01](targets-05.png)

Se recomienda agregar los *targets*:

- `all` Compilar programa seleccionado.
- `clean` Eliminar archivos de compilaciones previas (remueve la carpeta *out* dentro del programa seleccionado). Es necesario ejecutarlo sobre le programa seleccionado al cambiar opciones de compilación del programa (archivo *config.mk*) o al cambiar la plataforma de hardware (*board*) para la cual se compilará el programa.
- `clean_all` Eliminar archivos de compilaciones previas de todos los programas dentro de la carpeta firmware_v3.
- `download` Descarga el programa seleccionado a la *board* seleccionada.
- `erase` Borra la flash de la *board* seleccionada. Es necesario resetear la plataforma luego de aplicarlo.
- `new_program` Permite gráficamente crear un nuevo programa dentro de la carpeta seleccionada por el usuario (la primera vez se pide el nombre de la carpeta donde se guardaran los programas y se crea dentro de la carpeta firmware_v3).
- `select_board` Permite elegir gráficamente la plataforma de hardware (*board*) para la cual se compilará el programa.
- `select_program` Permite elegir gráficamente el programa a utilizar (compilar, descargar, limpiar, etc.).

Se ejecutan realizando doble doble click sobre el icono de los mismos.

## 4. Depuración de un programa sobre la plataforma de hardware con Eclipse y firmware_v3

### 4.1. Configuración de la descarga y depuración del programa sobre el hardware

Ubique el ícono del bicho verde (*debug*) , presione sobre la flecha hacia abajo a la derecha de este icono y en la ventana que se despliega la opción "*Debug Configurations...*"

![Eclipse-11](Eclipse-Win11.png)

Esto abre la ventana de configuraciones:

![Eclipse-12](Eclipse-Win12.png)

A la izquierda realizar doble click sobre "*GDB OpenOCD Debugging*" que crea una nueva configuración:

![Eclipse-13](Eclipse-Win13.png)

En esta ventana se puede ver que proyecto está seleccionado (en este caso ```firmware_v3```) y el programa a descargar/depurar (campo de texto C/C++ Application:). 

Mediante el botón "*Search Project..*" puede elegir que programa va a descargar/depurar. 

**Nota**: recuerde que debe haber compilado previamente un programa. En este caso se muestra como ejemplo el programa ```app.elf```:

![Eclipse-14](Eclipse-Win14.png)

Seleccionarlo y presionar "*Ok*".

![Eclipse-15](Eclipse-Win15.png)

Ir a la pestaña "Debugger" donde deberá completar lo siguiente:

- Executable path: ```${OPENOCD_PATH}/openocd```
- Config options: ```-f scripts/openocd/lpc4337.cfg```

![Eclipse-16](Eclipse-Win16.png)

Deslice la pantalla más abajo y configure en la sección "*GDB Client Setup*":

- Executable name: ```arm-none-eabi-gdb```

![Eclipse-17](Eclipse-Win17.png)

Con esto ya se encuentra configurado el Eclipse para depurar. 

### 4.2. Probar el funcionamiento de la depuración sobre el hardware

Para probarlo presione sobre el botón "*Debug*". Aparecerá un mensaje como el siguiente la primera vez que avisa que el Eclipse pasará de la perspectiva de programación, a la de depuración (esto hace que se reacomoden vairos menues para facilitar la depuración). Presione "*Remember my decision*" y "*Switch*" para que no la muestre cada vez:

![Eclipse-19](Eclipse-Win19.png)

Cuando el programa se descargó a la plataforma y empezó a ejecutarlo dentendrá su ejecución al inicio de la función main().

![Eclipse-20](Eclipse-Win20.png)

### 4.3. Botones de control de ejecución y breakpoints

Mediante los botones de control de ejecución y breakpoints podremos controlar el programa que se ejecuta en la placa desde nuestra PC:

![Eclipse-21](Eclipse-Win21.png)

De izquierda a derecha:

- **Skip All Breakpoints (Ctrl+Alt+B)**. Habilitar/Deshabilitar breakpoints.
- **Resume (F8)**. Correr el código hasta el próximo breakpoint o de forma continua.
- **Suspend**. Detener la ejecución del programa.
- **Terminate (Ctrl+F2)**. Terminar sesión de debug con botón stop.
- **Connect/Disconnect**. Botón conectar o desconectar (siempre deshabilitado, no se utiliza en firmware_v3).
- **Step Into (F5)**. Ejecuta un paso dentro de la próxima función llamada.
- **Step Over (F6)**. Ejecuta un paso en una instrucción del código.
- **Step Return (F7)**. Ejecuta un paso fuera de la función actual. 

Además se puede *agregar o eliminar un breakpoint* mediante doble click en el área gris a la izquierda de las líneas de código).

En este ejemplo se puso un *beakpoint* en la función ```boardConfig()```:

![Eclipse-22](Eclipse-Win22.png)

### 4.4. Depurar otro programa dentro del mismo proyecto

Simplemente deberá compilar el otro programa y luego abrir la ventana "*Debug Configurations*" y mediante el botón "*Search Project..*" puede elegir que programa va a descargar/depurar:

![Eclipse-14](Eclipse-Win14.png)

**NOTA:**  Recuerde que previamente debe haber compilado el programa a depurar para que aparezca en la búsqueda.

Luego simplemente presionar sobre debug, el resto de las configuraciones que realizamos se hace una única vez.



## Más información

[Volver al README](../readme/readme-es.md).
