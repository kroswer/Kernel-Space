Kernel para Raspberry Pi 3 cross compile
-

El toolchain utilizado fue gcc-linaro-arm-linux-gnueabihf-raspbian-x64
Lo descargamos directamente del repositorio de git 
>https://github.com/raspberrypi/tools

Al igual que las fuentes necesarias. 
>https://github.com/raspberrypi/linux

Se agregó el PATH para el toolchain en el archivo .bashrc

En la carpeta /linux ejecutamos los siguientes comandos. 
```
KERNEL=kernel7
make ARCH=arm CROSS_COMPILE=arm-linux-gnueabihf- bcm2709_defconfig
```
Esto para utilizar la configuración predeterminada necesaria para la Raspberry PI 3. El archivo de configuración utilizado se puede encontrar [aqui](https://github.com/kroswer/Kernel-Space/blob/master/bcm2709_defconfig).

Para compilarlo se utiliza el siguiente comando. 
```
make ARCH=arm CROSS_COMPILE=arm-linux-gnueabihf- zImage modules dtbs
```

Una vezs hecho esto se copian los archivos generados a la tarjeta SD.