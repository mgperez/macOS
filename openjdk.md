Ver todas las versiones de jdk instaladas 

```shell
$ /usr/libexec/java_home -V
```

Exportar la variable $JAVA_HOME en el archivo “.bash_profile”

Abrir una ventana de la terminal y acceder como super usuario,

```shell
$ sudo su
$ nano .bash_profile
$ exit
$ cd $HOME
$ source .bash_profile
$ echo $JAVA_HOME
```



https://www.oracle.com/java/technologies/javase-downloads.html



[Uninstalling the JRE on macOS](https://docs.oracle.com/javase/10/install/installation-jdk-and-jre-macos.htm#JSJIG-GUID-577CEA7C-E51C-416D-B9C6-B1469F45AC78)



\# Install Homebrew

```shell
# Install Cask
$ brew tap homebrew/cask-versions
```



Install the latest version of Java

```shell
$ brew cask install java

# To UnInstall JDK
$ brew cask uninstall java
```



Verify installation

```shell
$ java -version
$ echo $JAVA_HOME

#export JAVA_HOME=${/usr/libexec/java_home}
#export JAVA_HOME=$(/usr/libexec/java_home -v 11)
export JAVA_HOME=$(/usr/libexec/java_home -v 1.8)
```



https://github.com/AdoptOpenJDK/homebrew-openjdk

```shell
# to uninstall open jdk 8
$ brew cask uninstall caskroom/versions/adoptopenjdk8
```

Install the latest version of Java

```shell
$ brew cask install adoptopenjdk

# To UnInstall JDK
$ brew cask uninstall adoptopenjdk
```

