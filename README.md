A library and gateway to use an Arduino with the ThingBroker developed at the MAGIC lab. UBC.


### Some assumptions

We assume you are running Linux.

### Usage

+ Install Python in your machine and run the command "python brokerlistener" for more instructions. You can also change the "brokerlistener" file to executable and run it as ./brokerlistener. We're providing "runfordemo.sh" as an example.

+ Upload the "broker_pins" Arduino sketch to an arduino board.

+ We are providing an example-red-app for you to see how to interact with the arduino.

The brokerlistener process listens for events on a given thingId and relays such events to the board. There are three supported events:

+ digital
+ read
+ analog

Digital event types turn digital pins on (1) or off (0). Analog events take a value 0-255 and set that value into a given ANALOG pin. Read events read the input from a given pin. We also provide a "timeout" configuration that ensures that the pin is pulled down after an X number of seconds.

### Example events:

Set analog pin "5" to value "100" and pull resistor down after 10 seconds:
> {'type':'analog','5':'100', 'timeout':'10'}

Set pin "13" to "true", or resistor up, and don't ever timeout:
> {'type':'digital','13':'1'}

Read the value of pin "5" and send an event like so: {"type": "read_result", "1":"20"}:
> {'type':'read','pin':'5', 'timeout':'10'}

