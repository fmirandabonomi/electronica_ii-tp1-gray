# Trabajo práctico 1 - Electrónica II 2022 para ingeniería electrónica - Codificador para código gray de tres bits

Para completar el práctico debes:
- Instalar Visual Studio Code.
- Instalar la extension puorc.awesome-vhdl
- Instalar Git.
- Instalar GHDL.
- Instalar make.
- Clonar este repositorio en tu máquina.
- Ejecutar el testbench y ver que falla.
- Corregir la implementación hasta que pase las pruebas.

## Instalar Visual Studio Code y la extensión VHDL

Para instalar Visual Studio Code con la extensión necesaria

- Ve al sitio [code.visualstudio.com](https://code.visualstudio.com/) en tu navegador
- Descarga el instalador
- Ejecuta la instalación
- Abre Visual Studio Code
- Presiona Ctrl+Mayusc+X para abrir el panel de extensiones
- Escribe en el cuadro de búsqueda en la parte superior del panel escribe (o copia y pega, sin las comillas) "puorc.awesome-vhdl"
- Debe aparecer un único resultado, presiona "Install" en el resultado.

## Instalar Git

Para instalar Git

- Ve al sitio [git-scm.com/downloads](https://git-scm.com/downloads) en tu navegador
- Ve al link de tu plataforma
- Descarga el instalador (en windows "Standalone Installer" de 32 o 64 bits según corresponda)
- Ejecuta el instalador
- Cuando te pide elegir el editor elije "Visual Studio Code" en lugar de vim. Todas las otras opciones puedes dejarlas por defecto.
- Windows: Abre "git cmd", lo encontrarás en el menú inicio en git o con windows+q "git cmd" si tienes windows 10 o superior.
- Linux: Abre una terminal nueva.
- Configura tu nombre y email. Luego de cada comando debes presionar enter. Una vez configurado puedes salir de la consola.
```
  git config --global --add user.name "<escribe tu nombre aquí>"
  git config --global --add user.email <escribe tu email aquí>
  exit
```
## Instalar GHDL y make

En linux se instala con el manejador de paquetes de tu distribución.
En Windows
- Instala MSYS2 siguiendo las instrucciones en [msys2.org](https://www.msys2.org/) y supongo que lo instalas en `c:\msys64`
- Abre la consola de MSYS (desde el acceso directo en el menú inicio o buscando con windows+q)
- Actualiza el sistema ejecutando el siguiente comando (respeta mayúscula y minúscula, presiona enter para ejecutar) repetidas veces hasta que indique que todo está actualizado (up to date).
```
  pacman --noconfirm -Syu
```
  Nota: Con algunas actualizaciones deberás volver a abrir MSYS.
- Instala ghdl y sus dependencias
```
  pacman --noconfirm -S ucrt64/mingw-w64-ucrt-x86_64-ghdl-llvm
```
  debes aceptar para que proceda con la instalación.
- Instala make
```
  pacman --noconfirm -S make
```
- Puedes cerrar la consola luego de instalar
```
  exit
```  
- Agrega al path las carpetas `C:\msys64\ucrt64\bin` y `C:\msys64\usr\bin` para ello debes
  - Abrir _Propiedades del sistema_
  - Abrir _Configuración avanzada del sistema_
  - En opciones avanzadas elegir _Variables de entorno_
  - En el listado de variables de usuario hacer doble click en la variable `Path`
  - Agregar al final de la lista `C:\msys64\ucrt64\bin` y luego `C:\msys64\usr\bin`
    Nota: en versiones anteriores de windows aparece un solo texto largo en lugar de un listado, en ese caso agregar `;C:\msys64\ucrt64\bin;C:\msys64\usr\bin` (incluye el punto y coma) al final del texto

## Clonar el repositorio y probar el testbench

Para clonar este repositorio 
- Abre Visual Studio Code
- Presiona _Ctrl+Mayusc+P_ para abrir la paleta de comandos
- Escribe `Git:Clone` y presiona enter
- Pega en el cuadro de entrada lo siguiente y presinona enter:
```
  https://github.com/fmirandabonomi/electronica_ii-gray.git
```
- Selecciona una carpeta base. El repositorio se clonará en una nueva carpeta llamada `electronica_ii-gray` dentro de la carpeta que elijas. **Asegurate que en la ruta de acceso no haya carpetas con espacios en sus nombres**
- Una vez clonado aparecerá un cuadro en el sector inferior izquierdo y te dará la opción de abrirlo. Selecciona _Open_ u _Open in New Window_.
- Abre una terminal con el menú _Terminal->New terminal_
- Escribe el comando
```
  make
```
  Si todo está bién verás mensajes de error y luego la leyenda `bin_a_gray debe generar un codigo gray [FAIL]`
  
## Corregir la implementación

Para corregir la implementación debes editar el archivo `design.vhd`. 
- Abre el panel _explorer_ con _Ctrl+Mayus+E_
- Haz click en `design.vhd` para abrirlo. Aparecerá el editor en el lado derecho
- Lee el programa y haz los cambios que corresponda
- Para probar tu implementación debes guardar el archivo con _Ctrl+S_, ir a la terminal (puedes usar _Ctrl+ñ_), y ejecutar
```
  make
```
- Si las pruebas fallan (resultado `[FAIL]`) puedes encontrar pistas leyendo los errores.
- El práctico está completo cuando pasa las pruebas (resultado `[PASS]`)
- Para eliminar los archivos generados por ghdl usa el comando `make clean`
