--Project Summary

The project involves the implementation of a networked system consisting of two sensors (a temperature
sensor and a humidity sensor), a gateway, and a server. The sensors generate values periodically and send
them to the gateway, which then forwards the data to the server. The server stores the received data and
provides a web interface for accessing it.

--Solution Approach

The system was implemented using Java and socket programming. Each component of the system (the
sensors, the gateway, and the server) was implemented as a separate Java class. The temperature sensor
and the gateway communicate via TCP, while the humidity sensor and the gateway communicate via
UDP. The gateway and the server communicate via TCP.
A handshake protocol was implemented between the gateway and the server. When a connection is
established, the gateway sends a “HANDSHAKE_REQ” message to the server, which responds with a
“HANDSHAKE_ACK” message.
The temperature sensor generates a random temperature value every second and sends it to the gateway.
The humidity sensor generates a random humidity value every second, but only sends it to the gateway if
the value exceeds 80. Otherwise, it sends an “ALIVE” message.
The gateway forwards the received data to the server and monitors the activity of the sensors. If it doesn’t
receive any data from a sensor for a certain amount of time, it sends a ‘SENSOR OFF’ message to the
server.
The server stores the received data in a ConcurrentHashMap and provides a web interface for accessing it.
The server uses Java’s built-in HttpServer class to create an HTTP interface. This interface includes two
contexts, “/temperature” and “/humidity”, each handled by a separate handler class (TemperatureHandler
and HumidityHandler). These handlers respond to HTTP requests with the current temperature and
humidity data, respectively. This allows users to access the sensor data through a web browser or other
HTTP client. The server starts listening on port 8080 for incoming HTTP requests as soon as it is started.
This HTTP interface provides a user-friendly way to monitor the sensor data in real-time.

