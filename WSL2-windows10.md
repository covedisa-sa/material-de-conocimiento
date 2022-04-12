# 1. Instalar WSL 2 (para Windows 10)

WSL se ha convertido es una de las herramientas de desarrollo muy popular dentro de Windows 10, con esta herramienta no necesitas crear un dual boot en tu equipo (tener instalados dos sistemas operativos) para contar con todas las bondades del desarrollo de Linux. Pero como todo, WSL tiene sus detalles como el bajo rendimiento en la lectura de archivos.

Por fortuna Microsoft lanzó a través de la actualización de **Windows 10 Release 2004 Build 19041** la nueva versión de WSL, WSL 2.

## Pero, ¿por qué WSL 2?
Las características principales de WSL 2 son un mayor rendimiento (hasta 20 veces mejor que WSL 1 🤯) y un kernel de Linux 100% nativo, y otras características como:

- Llamadas del sistema totalmente compatibles
- Poco uso de memoria RAM
- Acceder a los archivos de la distro a través de la Red desde el explorador de Windows

Además debemos considerar tener un ambiente de desarrollo lo más cercano a lo que tendremos a los servidores en producción. Si comparamos porque utilizar contra **GitBash** la razón es sencilla, tenemos una alta gama de herramientas de desarrollo disponibles en WSL, además de que **GitBash** está muy limitado a funcionar adecuadamente para que utilicemos **Git**.

## ¿Qué necesito para correr WSL 2?
- Tener instalado Windows 10 Home o mejor (Windows 10 S no soporta WSL)
- Tener instalado **Windows 10 Release 2004 Build 19041** o posterior

> Nota:
> Para verificar su versión de Windows y el número de compilación, seleccione la tecla del logotipo de **Windows + R**, escriba **winver**, seleccione **Aceptar**. Puede actualizar a la última versión de Windows seleccionando **Inicio > Configuración > Actualización de Windows > Buscar actualizaciones**.


## Instalación
Primero que nada necesitamos habilitar Subsistema de Windows para Linux (Windows Subsystem for Linux) y Hyper-V, una herramienta de virtualización de Microsoft necesitado para WSL 2, pues nuestra distro se vuelve una maquina virtual dentro de nuestra sistema operativo de una forma especial que da vida a WSL 2 (aquí es donde sucede la magia del rendimiento).

Presionamos la tecla **Windows** y escribimos características y damos clic en: **Activar o desactivar las características de Windows**



Fig. 1 - Activar o desactivar las características de Windows

Aparece una pequeña ventana con el listado de características disponibles para nuestro sistema, necesitamos buscar las opciones de Hyper-V y Subsistema de Windows para Linux, nos aseguramos de que estén palomeadas ambas herramientas, damos clic en Aceptar y Windows empezará a descargar los archivos necesarios y cuando termine nos pedirá reiniciar nuestra máquina por lo que aceptamos y reiniciamos Windows.


Fig. 2 - Hyper-V seleccionado

Fig. 3 - Subsistema de Windows para Linux seleccionado

Una vez que tu equipo se reinició ya podemos descargar Ubuntu a través de la Microsoft Store.



Cuando termine la descarga iniciamos la aplicación y esperamos a que termine el proceso y establecemos nuestro usuario y contraseña de nuestra distribución de Linux.

Como verás el proceso de instalación es el mismo que WSL 1, pero aquí es donde se encuentra la diferencia principal, para ello necesitamos abrir Powershell presionando la combinación de teclas Windows + r y escribimos powershell.

Fig. 4 - Ejecutar Powershell

Nos abrirá una terminal donde ejecutaremos el siguiente comando: wsl --list --verbose o en su versión corta wsl -l -v, al ejecutar esta línea se despliega una lista de distribuciones instalada en nuestra máquina:

NAME     STATE    VERSION
Ubuntu   Stopped  1


Como observamos aún tenemos la versión 1 seleccionada, para establecer la versión 2 corremos el siguiente comando: wsl --set-version <el-nombre-de-la-distro> 2 o en el caso del ejemplo wsl --set-version Ubuntu 2 y presionamos Enter. Aparece un mensaje indicando que el proceso de conversión está ejecutándose y que tomará unos minutos, por lo que si gustas puedes ir por un café o estirar las piernas y brazos ya que si toma unos cuantos minutos (aproximadamente de 10 a 15 minutos).

Una vez completado el proceso volvemos a correr wsl -l -v y deberá mostrar la lista así:

NAME     STATE    VERSION
Ubuntu   Stopped  2


Y listo, ya tenemos WSL 2 disponible para desarrollar! 🤘
Consideraciones especiales

Al utilizar la versión 2 debemos tener las siguientes consideraciones:

No utilices alguna aplicación en Windows que haga uso del puerto 53, ya que en caso de que sea así se bloqueará el puerto utilizado por Hyper-V y tu distro no podrá iniciar.
Procura utilizar el sistema de archivos de tu distro porque si accedes a través del formato de archivos de Windows el rendimiento puede ser peor que el de WSL 1.

