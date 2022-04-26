# sgdk-instructions

## Introducción

En este documento puedes encontrar un Resumen de las instrucciones para instalar, compilar y ejecutar todo lo necesario para el taller de Desarrollo para Sega Mega Drive celebrado en la feria "STEM Open" celebrado el 28 de Abril en Granada.

Para más información acerca del taller o ver las diapositivas, consulta el siguiente [enlace](https://docs.google.com/presentation/d/1EiIG_s2G1itPPTynk2w162dxMUYrKRXF8kGXLYqNhtc/edit?usp=sharing).

## Instalación y Configuración


Durante el taller, vamos a utilizar el editor Visual Studio Code; este paso es opcional, pero dejamos las instrucciones para su instalación, junto a la extensión Genesis Code.

<details><summary>Visual Studio Code(Opcional)</summary>

 Si utiliza Visual Studio Code, puede descargarlo desde la siguiente dirección:
  
  [https://code.visualstudio.com/](https://code.visualstudio.com/)
  
  Una vez descargado e instalado, puede instalar la extensión _Genesis Code_ que utilizaremos en este taller. Para instalar una extensión, puede utilizar el gestor de extensiones del propio editor e instalar la extensión _Genesis Code_.
  
  ![imagen](https://user-images.githubusercontent.com/6067824/165355160-98bf5abe-8e7f-48b8-87d6-f2e5ef588de5.png)

  Para instalarlo, simplemente pulse el botón install (o instalar).
</details>

En primer lugar, para seguir el taller, necesitarás instalar y configurar el kit de desarrollo [SGDK](https://github.com/Stephane-D/SGDK); seguidamente dejamos las instrucciones para instalarlo en Windows, Linux o usando contenedores Docker.



<details><summary>Windows</summary>
  
  Para instalar en windows, primero necesitaremos instalar Java a través de su JRE, como prerequisito.
  
  Una vez instalados los prerequisitos, descargaremos la ultima version del SGDK:
  
  [https://github.com/Stephane-D/SGDK/releases/tag/v1.70](https://github.com/Stephane-D/SGDK/releases/tag/v1.70)
  
  Una vez hecho esto, descomprimiremos la descarga donde más nos guste, y estableceremos la variable de entorno _GDK_.
  
  **NOTA**: Si se utiliza la extensión _Genesis Code_, podeis configurar la variable GDK dentro de la configuración de Visual Studio Code.
  
</details>

<details><summary>Linux</summary>

  Para poder utilizar SGDK con Linux, puede usarse el proyecto _GENDEV_; El cual puede descargar la siguiente versión:
  
  [https://github.com/kubilus1/gendev/releases/tag/0.5.1](https://github.com/kubilus1/gendev/releases/tag/0.5.1)
  
  Puede descargar el fichero .deb (para sistemas basados en debian) o el fichero comprimido.
  
  Antes de instalar el .deb o descomprimir, necesita instalar las siguientes dependencias:
  
  ```bash
  apt update
  apt install texinfo default-jre
  ```
  
  Una vez instaladas, puede instalar el fichero .deb o descomprimir el fichero descargado.
  
  ```bash
  dpkg -i <fichero.deb>
  ```
  
  Por último, establecer la variable de entorno _GENDEV_ a donde tenga instalado gendev.
  
  ```bash
  export GENDEV=/opt/gendev
  ```
  
  **NOTA**: También puede establacer el valor de esta variable, usando la configuración de Genesis Code.
  </details>
  
 <details><summary>Docker</summary>

 Podemos generar y utilizar una imagen docker con SGDK y tener toda la librería a través de un contenedor Docker. En primer lugar, necesitará instalar Docker en su Sistema. Puede encontrar las instrucciones [aquí](https://docs.docker.com/engine/install/).
    
 Una vez instalado, descargaremos la última versión de SGDK, y la descomprimiremos donde queramos; este paso es el mismo que para Windows:
    
 [https://github.com/Stephane-D/SGDK/releases/tag/v1.70](https://github.com/Stephane-D/SGDK/releases/tag/v1.70)

 Una vez descomprimido, abriremos una consola en la carpeta donde se encuentra SGDK, y ejecutaremos el siguiente comando:
    
  ```bash
  docker build -t sgdk .
  ```
    
  Esto tardara un rato; ya que tendrá que instalar y configurar todas las dependencias. Una vez hecho esto, ya podemos utilizar SGDK a través de Docker.
    
  </details>
  
## Ejemplos

En esta sección, podremos ver como descargar y compilar los ejemplos:
  
### Descargar ejemplos de Github
  
 Los ejemplos del taller (además de algunos más), los puedes encontrar en la siguiente dirección:
  
  [https://github.com/LaJaqueria/tallermdrive](https://github.com/LaJaqueria/tallermdrive)
  
  Para descargar este repositorio puede usar git:
  
  ```bash
  git clone https://github.com/LaJaqueria/tallermdrive.git
  ```
  
  O descargar el zip desde la web de Github

### Emulador
  
  Para este taller, recomendamos el emulador _Blastem_; puede descargarse de la siguiente dirección:
  
  [https://www.retrodev.com/blastem/(https://www.retrodev.com/blastem/)

  Si utiliza _Genesis Code_, puede configurar donde se encuentra el emulador en la configuración de la extensión.
  
  ![imagen](https://user-images.githubusercontent.com/6067824/165358702-2b6c3b57-c7e6-4089-a5cc-2fd0981803c1.png)

### Compilar y ejecutar

  En esta sección, vamos a mostrar como compilar y ejecutar en un emulador los ejemplos descargados.
  
**Windows**
  
  Para compilar en windows, puede usarse el siguiente comando:
  
  ```bash
  %GDK%\bin\make -f %GDK%\makefile.gen
  ```
  
  <details><summary>Genesis Code </summary>
  Puede usar el comando _Genesis Code: Compile & Run_ (Para abrir la consola de comandos usad la combinación <kbd>ctrl</kbd>+<kbd>Mayus</kbd>+<kbd>P</kbd>.
  
  Además, comprueba en la configuración de Genesis Code que tiene seleccionado el Toolchain SGDK/GENDEV.
    
   ![imagen](https://user-images.githubusercontent.com/6067824/165360000-9e7a75b7-1a73-459c-85d6-5d4d61eaca8a.png)

 </details>

  
 **Linux**
  
  Para compilar en Linux, puede usarse el siguiente comando:
  
  ```bash
  make -f $GENDEV/sgdk/mkfiles/makefile.gen clean all
  ```` 
  
  <details><summary>Genesis Code </summary>
   Puede usar el comando _Genesis Code: Compile & Run_ (Para abrir la consola de comandos usad la combinación <kbd>ctrl</kbd>+<kbd>Mayus</kbd>+<kbd>P</kbd>.
  
   Además, comprueba en la configuración de Genesis Code que tiene seleccionado el Toolchain SGDK/GENDEV.
    
   ![imagen](https://user-images.githubusercontent.com/6067824/165360000-9e7a75b7-1a73-459c-85d6-5d4d61eaca8a.png)

 </details>
  
  **Docker**
  
  Por último, si necesita usar docker, para compilar, puede hacerlo con el siguiente comando:
  
  ```bash
  docker run --rm -v $PWD:/src sgdk # En Windows, usar %CD% en vez de $PWD.
  ```
  
  <details><summary>Genesis Code </summary>
  Puede usar el comando _Genesis Code: Compile & Run_ (Para abrir la consola de comandos usad la combinación <kbd>ctrl</kbd>+<kbd>Mayus</kbd>+<kbd>P</kbd>.
  
  Además, comprueba en la configuración de Genesis Code que tiene seleccionado el Toolchain Docker. Además, de comprobar que el nombre de la imagen es correcta.
    
  ![imagen](https://user-images.githubusercontent.com/6067824/165360605-098fdac3-403f-4b88-8303-f8ad5ff99165.png)

 </details>
