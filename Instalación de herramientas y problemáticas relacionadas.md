# Pasos para la instalación
1. Descargar e instalar el Launcher de CIAA siguiendo el instructivo brindado:[CIAA](https://github.com/ndirenzo/TP1/tree/main/Instalaci%C3%B3n%20de%20herramientas#utilizaci%C3%B3n). En nuestro caso, todos los integrantes del grupo poseen Windows y debimos instalar los driver correspondientes (FTDI VCP).
2. Descargar el repositorio del [firmware_v3](https://github.com/epernia/firmware_v3) y pegarlo en el path C:\\CIAA\Eclipse
3. Seguimos los pasos del instructivo para abrir el proyecto firmware_v3 por primera vez.
4. Compilamos el proyecto.
 
  Problematicas de Compilacion

  4.1. Durante la subida del firmware-v3 al IDE Eclipse, siguiendo los pasos de instalación de la guía [Guia de instalación](https://github.com/ndirenzo/TP1/blob/main/Instalaci%C3%B3n%20de%20herramientas/README.md) nos encontramos con un error: En la sección [1.1.4](https://github.com/ndirenzo/TP1/tree/main/Instalaci%C3%B3n%20de%20herramientas#114-abrir-proyecto-de-firmware-para-programar-en-asembler-c-o-c) se indica que se debe elegir como Toolchain ARM Cross GCC pero al hacerlo no se podía completar la subida. Para poder continuar elegimos la opción "none".
 
 4.2. Se produjo un error durante la compilación de los ejemplos de la herramienta de Yakindu. Al generar los archivos de compilación para los ejemplos según los [instructivos del TP1](https://github.com/ndirenzo/TP1/blob/main/Enunciado%20TP1.pdf), se generaban los archivos dentro de la carpeta /gen del ejemplo al hacer click derecho sobre los archivos .sgen y utilizar la opción "Generate Code Artifacts", pero no era posible compilarlos. El error radicaba en que luego de la reinstalación de la herramienta Yakindu, enunciado en la sección anterior, no se había compilado el projecto antes de compilar los ejemplos. Esto produjo que el archivo "app.elf" no exista, con lo que el programa no podía compilar los ejemplos del Yakindu.
 
5. Luego de compilar, configuramos el [Debbuger OPEN-OCD](https://github.com/ndirenzo/TP1/tree/main/Instalaci%C3%B3n%20de%20herramientas#4-depuraci%C3%B3n-de-un-programa-sobre-la-plataforma-de-hardware-con-eclipse-y-firmware_v3).

  Problematicas de Debugging

  5.1. Una vez realizada la compilacion del archivo firmware_v3, al realizar el dubugging del archivo se debia seguir una serie de pasos para completarla. El primer problema fue que no se encontraba el archivo app.elf generado de la compilacion mencionada desde la funcion Search Proyect, como indicaban las instrucciones. La solucion a esto fue utilizar la funcion Browse y buscar en el archivo deseado.
  
  5.2. En la pestaña Debugger de Debug Configuracions, en la sección Executable Path, ya venía escrito por Default ${openocd_path}$/openocd y las instrucciones  en [Guia de instalación](https://github.com/ndirenzo/TP1/blob/main/Instalaci%C3%B3n%20de%20herramientas/README.md) , en la sección [4.1](https://github.com/ndirenzo/TP1/tree/main/Instalaci%C3%B3n%20de%20herramientas#114-abrir-proyecto-de-firmware-para-programar-en-asembler-c-o-c) decían de dejar ${OPENOCD_PATH}/openocd. Esto generó confunsión porque parecía que no había que hacer esa modificación.

6. Insatalación del Yakindu a traves del marketplace del Eclipse


  Problematicas de Yakindu
  
  6.1. Fue necesario pedir la licencia educativa para poder validar la herramienta. Esto demoro la instalación unos días mientras se aguardo por la respuesta de la empresa.
  
  6.2. En el momento de instalar la herramienta en el IDE Eclipse, la version del plugin de Yakindu en Eclipse no era compatible con la licencia provista. Ante dicha situación debimos desinstalar el plugin e instalar una versión anterior (en nuestro caso, la 3.4.1 como esta indicado en el archivo [Yakindu.pdf](github.com/ndirenzo/TP1/blob/main/Instalación%20de%20herramientas/Yakindu.pdf))
