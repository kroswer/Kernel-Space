Kernel para Raspberry Pi 3 cross compile
-

Autor: Díaz Gayosso Hugo Enrique 

El toolchain utilizado fue gcc-linaro-arm-linux-gnueabihf-raspbian-x64
Lo descargamos directamente del repositorio de git, donde se encuentran otros tools que podemos utilizar, dependiendo el caso. 
>https://github.com/raspberrypi/tools

Al igual que las fuentes necesarias para compilar nuestro kernel. 
>https://github.com/raspberrypi/linux

Se agregó el PATH para el toolchain en el archivo .bashrc, esto para facilitar los comandos posteriores.
Esto se puede hacer añadiendo una linea parecida a la siguiente.
```
export PATH=$PATH:/home/user/tools/arm-bcm2708/gcc-linaro-arm-linux-gnueabihf-raspbian-x64/bin
```

En la carpeta /linux que descargamos, ejecutamos los siguientes comandos. 
```
KERNEL=kernel7
make ARCH=arm CROSS_COMPILE=arm-linux-gnueabihf- bcm2709_defconfig
```
Esto para utilizar la configuración predeterminada para la compilacion del kernel necesario para la Raspberry PI 3. El archivo de configuración utilizado se puede encontrar [aqui](https://github.com/kroswer/Kernel-Space/blob/master/bcm2709_defconfig).

Para compilarlo se utiliza el siguiente comando. 
```
make ARCH=arm CROSS_COMPILE=arm-linux-gnueabihf- zImage modules dtbs
```
Se puede aumentar la velocidad del proceso con la bander -j n, donde n es el numero de procesos * 1.5

Una vez hecho esto se copian los archivos generados a la tarjeta SD.
