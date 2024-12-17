# Mqtt_Reader
A python program that connects to a Mosquitto MQTT broker, listens for messages on the topic /events

Prerequisite :
1.	If you run running this on windows, Docker Desktop is installed and running .
2.	Make sure you have mosquitto-clients available on your system so you can use commands like mosquitto_pub.

once prequest completed gopy the files present in github and download them, follow the instruction

•	Now create a mosquitto broker container from eclipse-mosquitto docker image. Run below commnad :

Step1:    docker run -it --name dockerbroker -v ./config:/mosquitto/config/ eclipse-mosquitto:latest

•	After creating Dockerfile, need to run below commnad :

Step2:    docker build -t mqttsubc .

•	This command will make image with name of "mqttsubc". After that make a container from this image feom below command :

Step3:    docker run -it mqttsubc

•	Now open your command prompt and run below commnad to publish data to broker and you will se publish data where your subscriber container is running.

Step4:    mosquitto_pub -h localhost -t “/events” -m '{“sensor_value”:20.2}'

![image](https://github.com/user-attachments/assets/2ff41e2b-1756-4d9e-a5d9-049482c4d678)

