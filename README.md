# Bluetooth
![](https://www.tijuana.tecnm.mx/wp-content/uploads/2014/11/Heading-Ing-sistemas-768x252.png)
# Depto de Sistemas y Computación
# Ing. En Sistemas Computacionales
# SISTEMAS PROGRAMABLES 
# Autor (es): Muro Andrade Brandon Arturo
# Repositorio:  Bluetooth
# Fecha de revisión:  
# Objetivo: Prender y apagar el led de la pico usando bluetooth

# CÓDIGO
```python
# Prender y apagar el led de la pico usando bluetooth
# Muro Andrade Brandon Arturo 20211818
# Tecnológico Nacional de México ITT
# Sistemas programables


# Import necessary modules
from machine import Pin 
import bluetooth
from ble_simple_peripheral import BLESimplePeripheral

# Create a Bluetooth Low Energy (BLE) object
ble = bluetooth.BLE()

# Create an instance of the BLESimplePeripheral class with the BLE object
sp = BLESimplePeripheral(ble)

# Create a Pin object for the onboard LED, configure it as an output
led = Pin("LED", Pin.OUT)

# Initialize the LED state to 0 (off)
led_state = 0

# Define a callback function to handle received data
def on_rx(data):
    print("Data received: ", data)  # Print the received data
    global led_state  # Access the global variable led_state
    if data == b'toggle\r\n':  # Check if the received data is "toggle"
        led.value(not led_state)  # Toggle the LED state (on/off)
        led_state = 1 - led_state  # Update the LED state

# Start an infinite loop
while True:
    if sp.is_connected():  # Check if a BLE connection is established
        sp.on_write(on_rx)  # Set the callback function for data reception






```

![image](https://github.com/BrandonMuro2/Bluetooth/assets/80359445/903e3fba-d359-4381-a621-5f9001aed9f1)
