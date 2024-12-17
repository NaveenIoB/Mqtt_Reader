# Mqtt_Reader
A python program that connects to a Mosquitto MQTT broker, listens for messages on the topic /events

Now create a mosquitto broker container from eclipse-mosquitto docker image. Run below commnad :

docker run -it --name dockerbroker -v ./config:/mosquitto/config/ eclipse-mosquitto:latest

After creating Dockerfile, need to run below commnad :

docker build -t mqttsubc .

This command will make image with name of "mqttsubc". After that make a container from this image feom below command :

docker run -it mqttsubc

Now open your command prompt and run below commnad to publish data to broker and you will se publish data where your subscriber container is running.

mosquitto_pub -h localhost -t “/events” -m '{“sensor_value”:20.2}'

![image](https://github.com/user-attachments/assets/2ff41e2b-1756-4d9e-a5d9-049482c4d678)

