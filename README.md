# Esp32-dev-on-Docker
build and flash to esp32 using ESP-IDF  and Docker

# commands:
  - Build docker image from Dockerfile
    - Go to Dockerfile directory(cloned directory) and run:
  ```
    docker build -t  esp-build .
  ```
  - Build project:
  ```
   - sudo docker run --rm -it -v <PROJECT_DIRECTORY>:/proj esp-build
  ```
  
 - Clean project:
 ```
 - sudo docker run --rm -it -v <PROJECT_DIRECTORY>:/proj esp-build clean
 ```
 
 - Flash project[WIP]
 ```
 sudo docker run --rm -it -v <PROJECT_DIRECTORY>:/proj --device=/dev/tty.usbserial-69526807B6 esp-build flash
 ```
