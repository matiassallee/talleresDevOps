# Taller de infraestructura como código

## Prerequisitos

1. En caso de tener HyperV habilitado, ir a Turn Windows Features On or Off y deshabilitar HyperV porque va a generar conflictos. Nos va a pedir reiniciar la máquina y luego del reinicio hay que ejecutar el siguiente comando en una consola de CMD o Powershell como administrador ```bcdedit /set hypervisorlaunchtype off```.

    Luego reiniciar la máquina y estamos prontos para seguir.

1. VirtualBox <= 6.0 
    
    Al día 15 de enero de 2020 la última versión de Vagrant no tiene soporte para la 6.1 que es la que nos va a ofrecer como descarga por defecto VirtualBox. 
    
    Para conseguir este build previo es simplemente entrar [acá](https://www.virtualbox.org/wiki/Download_Old_Builds_6_0) y descargar la versión 6.0.16 para nuestro SO.

    En caso de querer saber que versión tenemos instalada, simplemente abrimos VirtualBox -> Help -> About VirtualBox y nos debería mostrar nuestra versión.

    El error que nos mostraría si intentamos de hacer ```vagrant up``` es este:

    ![](/recursosMD/capturaErrorVagrantUp.PNG)

2. Vagrant > 2.0

    Para descargar vagrant es simplemente desde [acá](https://www.vagrantup.com/downloads.html).

3. Preinstalación de una box

    Vagrant trabaja con "boxes", las cuales son simplemente una imagen básica y liviana de un SO la cual clona a la hora de crear una VM. Si nosotros llevamos instalada previamente la box al taller, no tenemos que descargarla cuando la referenciemos desde un Vagrantfile, lo cual nos va a agilizar bastante los procesos para que la demo no sean 20 minutos de descargas.

    Una vez instalado Vagrant, vamos a ejecutar el siguiente comando:

    ```vagrant box add hashicorp/bionic64```

    Nos va a promptear para que seleccionemos el provider, seleccionamos la opción para VirtualBox y dejamos que descargue. Deberíamos ver una salida similar a la siguiente:

    ![](/recursosMD/capturaVagrantAdd.PNG)

    Esto va a dejar disponible de manera local la imagen base que vamos a usar en nuestro Vagrantfile. Para corroborar que instalamos de manera correcta, podemos ejecutar los siguientes comandos y no debería de descargarse la imágen base nuevamente si no que debería utilizar la local.

    ``` pwsh
    $ mkdir vagrantTest
    $ cd vagrantTest
    $ vagrant init hashicorp/bionic64
    $ vagrant up
    ```
    La salida que deberían ver es similar a la siguiente, y no decir nada sobre descargas:

    ![](/recursosMD/capturaVagrantUp.PNG)

    Pueden probar ejecutar el comando ```vagrant ssh``` que nos debería abrir una sesión de consola vía ssh en nuestra VM. Para salir simplemente ejecutamos el comando ```exit```. También van a poder ver en VirtualBox que efectivamente hay una nueva VM creada.