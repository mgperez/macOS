Tomcat
https://tomcat.apache.org/download-90.cgi
https://www.dryant.com/programacion/como-instalar-un-servidor-java-tomcat-en-mac-os-todas-las-versiones/
https://sintaxispragmatica.wordpress.com/2014/07/16/instalar_apache_tomcat_en_mac_os-x/

En el archivo .bash_profile colocar las 2 siguiente lineas:

```shell
export CATALINA_HOME=$HOME/development/apache-tomcat-...
export PATH=$PATH:$CATALINA_HOME/bin
```

Mover la carpeta Tomcat a $HOME/development

```shell
$ sudo mv $HOME/Downloads/apache... $HOME/development
```

Dar permisos de ejecución a los scripts de Tomcat

```shell
sudo chmod +x $HOME/development/apache.../bin/*.sh
```

\# Ejecutar y parar Tomcat desde terminal

```shell
$ startup.sh
```

Ahora una vez iniciado nos vamos al navegador y probamos en la barra de direcciones: **localhost:8080** y se nos abrirá la pagina principal local de nuestro server local en Tomcat

apagar el server solo utilizar 

```shell
$ shutdown.sh 
```

Para crear un link simbolico lo podemos hacer con el terminal de la siguiente forma:

> sudo ln -s /usr/local/Tomcat/webapps/ ~/Documents/

A partir de ahora todo lo que coloquemos en ~/Documents/webapps/ estará ubicado realmente en /usr/local/Tomcat/webapps y accesible desde cualquier app.