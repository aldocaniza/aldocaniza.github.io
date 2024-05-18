- InfoLab01
	- Se procedio a la instalacion del Sistema Operativo Linux, Distribucion Ubuntu Server 24.04
	- Pasos
		- ```Descarga del archivo ISO de la pagina oficial de Ubuntu [Get Ubuntu Server | Download | Ubuntu](https://ubuntu.com/download/server)```
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

- InfoLab02
	- Configuracion de Servicio de Correo
		- Se instala el paquete de postfix y mailutils con los siguientes comandos
			- sudo apt install postfix libsasl2-2 libsasl2-modules ca-certificates
			- sudo apt install mailutils
		- En la pantalla inicial de configuracion indicamos el tipo de mail como Local Only, el hostname localhost y el SMTP como `[smtp.gmail.com]:587`
		- Editamos el fichero de configuracion de postfix main.cf con el editor nativo de linux "nano" con el siguiente comando
			- sudo nano /etc/postfix/main.cf
			- editamos los siguientes campos con estos datos, reemplazando lo que ya esta cargado
				- relayhost = `[smtp.gmail.com]:587`
				  smtp_sasl_auth_enable = yes  
				  smtp_sasl_security_options = noanonymous  
				  smtp_tls_CApath = /etc/ssl/certs  
				  smtpd_tls_CApath = /etc/ssl/certs  
				  smtp_use_tls = yes  
				  smtp_tls_CAfile = /etc/ssl/certs/ca-certificates.crt  
				  smtp_sasl_password_maps = hash:/etc/postfix/sasl/sasl_passwd  
				  smtp_tls_security_level = encrypt  
			- guardamos los cambios con Ctrl + X ---> Y ---> Enter
		- Luego que de que esten listas las configuraciones iniciales, procedemos a obtener la contraseña de aplicacion de una cuenta de gmail ya creada en el siguiente enlace
			- [https://security.google.com/settings/security/apppasswords]
			- Creamos un ID para generar una clave nueva y copiamos dicha clave para ingresarlo en la configuracion del postfix
		- Procedemos a configurar el fichero sasl_passwd con el siguiente comando
			- sudo nano /etc/postfix/sasl/sasl_passwd
			- Ingresamos las Credenciales con la siguiente sintaxis
				- [[smtp.gmail.com]]:587 username@gmail.com:password
			- Guardamos los cambios con Ctrl + X
		- Luego procedemos a generar la base de datos con las Credenciales ingresadas y cambiar los permisos de los archivos para ejecutarlos como root
			- sudo postmap /etc/postfix/sasl/sasl_passwd
			- sudo chmod 0600 /etc/postfix/sasl/sasl_passwd
			- sudo chmod 0600 /etc/postfix/sasl/sasl_passwd.db
			- sudo chown root.root /etc/postfix/sasl/sasl_passwd*
			  sudo chmod 400 /etc/postfix/sasl/sasl_passwd  
		- Hasta aqui llega la configuracion del servidor, debemos reiniciar el servicio para aplicar los cambios, lo hacemos con el siguiente comando
			- sudo /etc/init.d/postfix reload
			- sudo systemctl restart postfix
	- Envio de Correo
		- Los correos se envian con la siguiente Sintaxis
			- ```echo "Hola Mundo" | mail -s "Mensaje de prueba" correodestino@example.com```

			
			