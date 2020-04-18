https://www.oracle.com/java/technologies/javase-downloads.html



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

