## Download and Install java using tar
--------------------------------------

* Download "OpenJDK JDK 18.0.2.1" a tar file from any of the following links 

[OpenJDK 11.0.2 (build 11.0.2+9)](https://download.java.net/java/GA/jdk11/9/GPL/openjdk-11.0.2_linux-x64_bin.tar.gz)

[OpenJDK JDK 18.0.2.1 General-Availability Release](https://jdk.java.net/18/)

[Archived OpenJDK General-Availability Releases](https://jdk.java.net/archive/)

[JDK](https://openjdk.org/projects/jdk/11/)

```
wget https://download.java.net/java/GA/jdk18.0.2.1/db379da656dc47308e138f21b33976fa/1/GPL/openjdk-18.0.2.1_linux-x64_bin.tar.gz
```
```
ls
```

```
sudo mkdir /usr/lib/jvm/
```

```
sudo tar zxvf openjdk-18.0.2.1_linux-x64_bin.tar.gz --directory /usr/lib/jvm/
```

```
sudo echo 'JAVA_HOME=/usr/lib/jvm/jdk-18.0.2.1' >> /etc/environment
sudo echo 'MY_HOME=/home/ubuntu' >> /etc/environment
```

```
. /etc/environment
```
```
sudo echo 'export JAVA_HOME=/usr/lib/jvm/jdk-18.0.2.1' > /etc/profile.d/myenv.sh
sudo echo 'export PATH=$PATH:$JAVA_HOME/bin' >> /etc/profile.d/myenv.sh
```
```
source /etc/profile
```
```
echo $JAVA_HOME
```
```
sudo echo 'export MY_HOME=/home/ubuntu' > /etc/profile.d/new-env.sh
```
```
source /etc/profile
```

* If we need to set the _$JAVA_HOME_ variable.

* In our case, while setting up _Maven_, we need to set it where the **JDK** is installed.

1. Checking where's JAVA installed
```
whereis java
```
> java: /usr/bin/java /usr/share/java /usr/share/man/man1/java.1.gz

2. Dig deeper
```
ls -l /usr/bin/java
```
> lrwxrwxrwx 1 root root 22 Oct 30 15:07 /usr/bin/java -> /etc/alternatives/java

3. Let's Dig deeper
```
ls -l /usr/lib/jvm/java-11-openjdk-amd64/bin/java
```
> ~~-rwxr-xr-x 1 root root 6464 Mar 14 18:28 /usr/lib/jvm/java-11-openjdk-amd64/jre/bin/java~~
> > -rwxr-xr-x 1 root root 14560 Jul 22 09:14 /usr/lib/jvm/java-11-openjdk-amd64/bin/java

4. As it is not being referenced to any other directory, we'll use this.
Open /etc/environment using nano
```
sudo nano /etc/environment
```

5. Append the following lines
```
export JAVA_HOME=/usr/lib/jvm/java-1.11.0-openjdk-amd64
export PATH=$PATH:JAVA_HOME/bin
```

6. Reload PATH using
```
. /etc/environment
```

7. Next
```
echo $JAVA_HOME
```
> /usr/lib/jvm/java-1.11.0-openjdk-amd64

8. check Java
```
java --version
```

9. If we have multiple Java installations to change the default version, use the update-alternatives tool as shown below 
```
sudo update-alternatives --config java
```


* There are 3 choices for the alternative java (providing /usr/bin/java).

|  Selection  |  Path                                           | Priority  |  Status      |
|:-----------:|:-----------------------------------------------:|:---------:|:------------:|
|* 0          |  /usr/lib/jvm/java-11-openjdk-amd64/bin/java    |  1111     |  auto mode   |
|  1          |  /usr/lib/jvm/java-11-openjdk-amd64/bin/java    |  1111     |  manual mode |
|  2          |  /usr/lib/jvm/java-8-openjdk-amd64/jre/bin/java |  1081     |  manual mode |

Press <enter> to keep the current choice[*], or type selection number:


References ~
----------
[.1](https://mkyong.com/linux/how-to-set-environment-variable-in-ubuntu/){:target="_blank"}

[.2](https://askubuntu.com/a/175519){:target="_blank"}

[.3](https://stackoverflow.com/a/23427862/6297483){:target="_blank"}

[.4](https://askubuntu.com/questions/175514/how-to-set-java-home-for-java){:target="_blank"}

[.5](https://linuxize.com/post/install-java-on-ubuntu-18-04/){:target="_blank"}

For Better understanding on where to download & extract the JDK files
_[Refer Here](https://stackoverflow.com/questions/56066875/where-to-install-jdk-tar-gz-file-on-ubuntu-18.04)_{:target="_blank"}

<p style="text-align: right"><img src="./java.png"></p>
