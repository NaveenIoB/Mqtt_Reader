Mqtt_Reader
This is a Python application that connects to a Mosquitto MQTT broker, listens for messages on the /events topic, and prints out the messages. This project uses Docker to run both the Mosquitto broker and the Python application, and it utilizes the gmqtt library for asynchronous MQTT communication.

Prerequisites:
1.	Docker Desktop:
    o	If you are running this on Windows, ensure that Docker Desktop is installed and running.
2.	mosquitto-clients:
    o	Ensure you have mosquitto-clients installed on your system. This will allow you to use commands like mosquitto_pub and mosquitto_sub to publish and subscribe to MQTT messages.
  	
Step 1: Clone the Repository
First, clone the repository from GitHub " https://github.com/NaveenIoB/Mqtt_Reader.git "

Step 2: Setting Up Mosquitto Broker
Create a Mosquitto broker container from the eclipse-mosquitto Docker image by running the following command:

docker run -it --name dockerbroker -v ./config:/mosquitto/config/ eclipse-mosquitto:latest

Step 3: Build the MQTT Subscriber Container
Now, build the Docker image for the MQTT listener Python application. From the project directory, run:

docker build -t mqttsubc .

Step 4: Run the MQTT Subscriber
After building the image, run the container from the mqttsubc image:

docker run -it mqttsubc

Step 5: Publish a Test Message

To send a message to the broker, open a new terminal (or command prompt) and run the following command:

mosquitto_pub -h localhost -t "/events" -m '{"sensor_value":20.2}'

Step 6: Verify the Output
Once the message is published, you should see the following output in the MQTT listener container:

Received message on /events: {"sensor_value":20.2}


Project Structure
Here’s an overview of the project files:
Mqtt_Reader/
│
├── config/                # Configuration files for Mosquitto broker
│
├── Dockerfile             # Dockerfile for the MQTT Python subscriber application
├── docker-compose.yml     # Docker Compose configuration (optional)
├── mqtt_listener.py       # Python script for MQTT subscriber using gmqtt
├── requirements.txt       # Python dependencies
├── README.md              # Project documentation



![image](https://github.com/user-attachments/assets/2ff41e2b-1756-4d9e-a5d9-049482c4d678)

