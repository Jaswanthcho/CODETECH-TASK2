from flask import Flask, render_template, request
import RPi.GPIO as GPIO

app = Flask(__name__)

# Setup GPIO pins
GPIO.setmode(GPIO.BCM)
GPIO.setup(18, GPIO.OUT)  # Example pin for light

@app.route('/')
def index():
    return render_template('index.html')

@app.route('/toggle/<device>')
def toggle(device):
    if device == 'light':
        GPIO.output(18, not GPIO.input(18))  # Toggle light state
    return index()

if __name__ == '__main__':
    app.run(host='0.0.0.0', port=5000)


    OVER VIEW OF PROJECT 
    Hardware Requirements
Raspberry Pi: A Raspberry Pi 3 or 4 is recommended for better performance.
Wi-Fi Module: For internet connectivity.
Relay Module: To control high-voltage appliances like lights and fans.
LCD Display: To show the status of the appliances.
Sensors: Optional sensors like PIR for motion detection or temperature sensors.
Power Supply: To power the Raspberry Pi and connected devices.
Wires and Connectors: For connections between components.
Software Requirements
Operating System: Raspbian or any Linux-based OS compatible with Raspberry Pi.
Programming Language: Python is commonly used for scripting the automation logic.
Web Framework: Flask is recommended for creating a web interface.
Database: SQLite or any lightweight database to store appliance states and user commands.
Step-by-Step Implementation
Step 1: Setting Up the Raspberry Pi
Install the latest version of Raspbian on your Raspberry Pi.
Connect the Raspberry Pi to your Wi-Fi network.
Step 2: Installing Required Software
Install Python and Flask:
bash
sudo apt-get update
sudo apt-get install python3 python3-pip
pip3 install flask
Optionally, install other libraries for GPIO control:
bash
pip3 install RPi.GPIO
Step 3: Wiring the Components
Connect the relay module to the GPIO pins of the Raspberry Pi.
Wire your appliances (lights, fans) to the relay outputs.
Connect any sensors if needed (e.g., PIR sensors).
Step 4: Creating the Web Interface
Create a simple Flask application:
python
from flask import Flask, render_template, request
import RPi.GPIO as GPIO

app = Flask(__name__)

# Setup GPIO pins
GPIO.setmode(GPIO.BCM)
GPIO.setup(18, GPIO.OUT)  # Example pin for light

@app.route('/')
def index():
    return render_template('index.html')

@app.route('/toggle/<device>')
def toggle(device):
    if device == 'light':
        GPIO.output(18, not GPIO.input(18))  # Toggle light state
    return index()

if __name__ == '__main__':
    app.run(host='0.0.0.0', port=5000)
Create an index.html file with buttons to control your devices.
Step 5: Accessing the System Remotely
Use your web browser or mobile device to access the Raspberry Pi's IP address followed by :5000 (e.g., http://192.168.x.x:5000).
Control your appliances through the web interface.
Step 6: Mobile App Integration (Optional)
You can create a mobile app using frameworks like React Native or Flutter that sends requests to your Flask server to control devices.
Conclusion
By following these steps, you can set up a basic home automation system using a Raspberry Pi that allows remote control of various appliances through a web interface or mobile app. This setup can be expanded with additional features such as voice commands or integration with other smart home devices using platforms like Home Assistant127.
Related
How can I integrate voice commands into my Raspberry Pi home automation system
What are the best sensors to use with a Raspberry Pi for home automation
How can I secure my Raspberry Pi home automation system from hacking
Can I use a Raspberry Pi to automate outdoor lighting and security cameras
What are the advantages of using Flask over other web frameworks for home automation
Ask follow-up

