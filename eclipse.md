# Updating eclipse.ini on MacOS

On MacOS X, eclipse.ini is found under $ECLIPSE_HOME/Eclipse.app/Contents/Eclipse where ECLIPSE_HOME is the installation folder of your eclipse distribution.



/Applications/Eclipse.app/Contents/Eclipse



https://wiki.eclipse.org/Eclipse.ini

```shell
/usr/libexec/java_home --verbose
```

/Applications/Eclipse JEE.app/Contents/Info.plist

**Install**

https://www.youdriveai.com/how-to-install-eclipse-on-macos-using-homebrew

### Failed to create java virtual machine .

Edit Info.plist file

cd /Applications/Eclipse JEE.app/Contents/, 

and add jdk path like this:

<string>-vm</string><string>/Library/Java/JavaVirtualMachines/jdk1.8.0_191.jdk/Contents/Home/bin/java</string>

Uninstall Eclipse Manually**

https://nektony.com/how-to/uninstall-eclipse-on-mac



Here is what happens:

1. `mvn clean` deletes the `target` directory
2. `mvn package` performs some work, but then encounters a compilation error due to a missing dependency. That's why the target folder is in error.
3. Running Maven > Update Project in Eclipse causes Eclipse to perform its own compilation, separate from Maven. Eclipse has a different classpath than Maven, so its compilation succeeds. Now the `target` directory has all the compiled classes.
4. Re-running `mvn package` now succeeds, because it finds all the classes already compiled and doesn't need to perform any compilation.

[Install Lombok for Eclipse on Mac](https://nawaman.net/blog/2017-11-05)