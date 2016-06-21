S M A L L
=========
  
This is my custom Dockerfile for work on systems 32 bit  

Why this?
Because docker documentation says it requires 64 bits and my computer doesn't support it. /cry ;(  
  
  
Then how WTF use this ....?  
```bash
$ sudo apt-get install docker.io  
$ sudo docker -v  # You'll see something like this: 'Docker version 1.6.2' If it's all good
```
  
Next step ...  
  
create a random folder and follow the steps:  
```bash
$ mkdir some_folder  
$ cd some_folder  
$ git clone https://github.com/dhelbegor/small.git  
$ cd small  
```
 
build image:  
```bash
$ sudo docker build -f $(pwd)/docker/Dockerfile -t container_name . # (container_name) some name for your container   
```
  
run this image and enter into bash:  
```bash
$ sudo docker run -ti -v $(pwd)/:/root -p 8000:8000 container_name bash # (container_name) your container name defined on build  
```
  
now go to the root/ folder:  
```bash
$ cd root/  
$ django-admin.py startproject some_name .  
```
  
outside of bash, edit the project:  

```bash
$ sudo subl .  # Why I need use sudo?, because this is defined on build and run remember? $(pwd)/:/root  
```
'subl' requires Sublime Text
  
This is a small example how to use docker on systems 32 bits.  
  
I hope this is can be helpful :D  
