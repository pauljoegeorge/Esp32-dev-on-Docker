# On Ubuntu 18.04:
> Update your system
```
$sudo apt update
$sudo apt upgrade
```

> Install Prerequisite Packages for Docker
```
$sudo apt-get install curl apt-transport-https ca-certificates software-properties-common

```
> Add Docker repositories
```
$curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
$sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
$sudo apt update
```

> Install Docker
```
sudo apt install docker-ce
```
> Check Docker status
```
sudo systemctl status docker
```
> Sample Output:
![](https://i.imgur.com/g1nF8FY.png)

> Install Git
```
  $ sudo apt-get install git -y
```

> Clone environment setup repository
```
$ git clone https://github.com/pauljoegeorge/Esp32-dev-on-Docker.git
```
> Clone esp-idf repository
```
$ git clone --recursive https://github.com/espressif/esp-idf.git --branch release/v3.2
```
> Go to Esp32-dev-on-Docker directory
```
$ ls => command will list files in current directory
$ cd Esp32-dev-on-Docker
```
> Build docker image from Dockerfile
```
$ sudo docker build -t esp-image .
```

> Confirm that esp-image is listed on docker images
```
$ sudo docker images
```
> Let's build a sample HelloWorld project available inside esp-idf directory first
  - Copy HelloWorld project from esp-idf directory to a new location
```
  $ cd
  $ cp -r esp-idf/examples/get-started/hello_world .
  $ cd Esp32-dev-on-Docker
  $ sudo docker run --rm -it -v <WORKING_DIR>:/proj esp-build
  
  Hint: 
    - To get working directory: run $ pwd  command
    - Screen to small message? 
      - Make it big :D

```

> Connecting M5StickC to your computer
```
1. Run: $ ls /dev/tty*
  - Will list available serial ports
2. Now connect M5StickC to your computer and run the same command and see any new device is detected
  - $ ls /dev/tty*
  
3. No ? 
  - Shutdown
  -  Go to VirtualBox Manager>> Settings >> Ports >> USB >> Click (+) button, and it will show M5Stick C. 
    - its showing M5Stack***** in my case
  - Add and click OK
4. Start Ubuntu again
5. RUn the command to list serial ports again
  - $ ls /dev/tty*
 
 TADA!! I can see /dev/ttyUSB0 now

```

> Let's flash the project to M5StickC now
```
$ sudo docker run --rm -it -v hello_world:/proj --device=/dev/ttyUSB0 esp-build flash
```
> Sample Output:
![](https://i.imgur.com/pSpoXeN.png)

