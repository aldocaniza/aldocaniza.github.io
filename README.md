- InfoLab01
	- Se procedio a la instalacion del Sistema Operativo Linux, Distribucion Ubuntu Server 24.04
	- Pasos
		- Descarga del archivo ISO de la pagina oficial de Ubuntu [Get Ubuntu Server | Download | Ubuntu](https://ubuntu.com/download/server)
		- Se utilizo el software Rufus para crear una unidad de instalación en un dispositivo flash USB (Pendrive)
		- Se inserto el unidad de instalacion en la computadora destinada a Servidor
		- Se establecio como unidad de booteo a dicha unidad
		- Se siguieron los pasos indicados en el proceso de instalación, como elección de distribución de teclado, credenciales, paquetes por defecto
			- Credenciales:
				- Nombre del equipo: admin0
				- Nombre del servidor: ubuntuserver
				- Usuario: admin1
				- Clave: 12345admin
				- Usuario: root
				- Clave: sistema123
		- En este caso se opto por formatear la unidad HDD para su instalacion en limpio del Sistema Operativo.
		- Una vez finalizada la instalacion, se reinicio el equipo Servidor.
		- Al iniciarse el equipo se ingreso con las credenciales "root"
		- Posterior a eso se instalo el paquete de net-tools con el comando "sudo apt install net-tools"
		- Luego se ejecuto el comando "ifconfig" para obtener la IP local del servidor
		- Seguidamente se instalo el paquete SSH para la conexion remota con el servidor con el comando "sudo apt install SSH"
	- Acceso al servidor por SSH
	- Pasos
		- Se descargo el software Putty para conexion remota al servidor
		- Se ingreso al servidor mediante una conexion SSH, con la IP obtenida en el proceso anterior y las credenciales establecidas en el proceso de instalacion.
	- Servidor de Correo
	- Pasos
		- Mediante una conexion SSH se procedio a la instalacion del paquete Postfix con el comando "sudo apt install postfix"
		- Se establecio como un servidor de correo local, con el dominio "ubuntuserverucsa1er"
		- Se iniciaron las configuraciones iniciales del servidor de correo.