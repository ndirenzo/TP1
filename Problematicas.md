# Problematicas de Yakindu
  1. Fue necesario pedir la licencia educativa para poder validar la herramienta. Esto demoro la instalación unos días mientras se aguardo por la respuesta de la empresa.
  2. En el momento de instalar la herramienta en el IDE Eclipse, la version del plugin de Yakindu en Eclipse no era compatible con la licencia provista. Ante dicha situación debimos desinstalar el plugin e instalar una versión anterior (en nuestro caso, la 3.4.1 como esta indicado en el archivo [Yakindu.pdf](github.com/ndirenzo/TP1/blob/main/Instalación%20de%20herramientas/Yakindu.pdf))

# Problematicas de Compilacion
  1. Durante la subida del firmware-v3 al IDE Eclipse, siguiendo los pasos de instalación de la guía [Guia de instalación](https://github.com/ndirenzo/TP1/blob/main/Instalaci%C3%B3n%20de%20herramientas/README.md) nos encontramos con un error: En la sección [1.1.4](https://github.com/ndirenzo/TP1/tree/main/Instalaci%C3%B3n%20de%20herramientas#114-abrir-proyecto-de-firmware-para-programar-en-asembler-c-o-c) se indica que se debe elegir como Toolchain ARM Cross GCC pero al hacerlo no se podía completar la subida. Para poder continuar elegimos la opción "none".

 2. Se produjo un error durante la compilación de los ejemplos de la herramienta de Yakindu. Al generar los archivos de compilación para los ejemplos según los instructivos del TP1, se generaban los archivos dentro de la carpeta /gen del ejemplo al hacer click derecho sobre los archivos .sgen y utilizar la opción "Generate Code Artifacts", pero no era posible compilarlos. El error radicaba en que luego de la reinstalación de la herramienta Yakindu, enunciado en la sección anterior, no se había compilado el projecto antes de compilar los ejemplos. Esto produjo que el archivo "app.elf" no exista, con lo que el programa no podía compilar los ejemplos del Yakindu.
 3. 
# Problematicas de Debugging

