## Wireless Networking

#### Neighbour Discovery using Quorum Discovery Protocol
The project implemented a quorum based neighbour discovery protocol. One node would be sensing light readings, and when one or more sensor tags discover that this light sensing node is nearby, will receieve the accumalated light sensor readings via broadcast messages. Our SensorTags runs as two state machines, namely main_state, which manages the overall state of the SensorTag, and nbr_state, representing the state of the neighbor discovery process. Both transmitter and receiver are similar in their states, with the exception of the transmitter having an implicit BROADCAST state while the receiver has an implicit RECEIVE state.
  
##### Proximity Detection
Proximity detection is done using the RSSI value that is detected during the neighbor discovery process. During the discovery process, the transmitter will always prioritize the first device it finds for the logging of DETECT and ABSENT events. Transmitters will not be able to detect other transmitters, while receivers will not be able to detect other receivers. This is done to prevent confusion in our discovery process.

##### Reliability
We implemented an acknowledgement protocol in our system. With every broadcast of a light packet, the transmitter will wait for the receiver’s acknowledgement for 1 second. If no acknowledgement is received by the transmitter, the light packet will be transmitted again, provided that the transmitter is not in NBR_STATE_DISCOVERY, until an acknowledgement is received or three broadcast attempts have been made, whichever is earlier. Another enhancement includes filtering out invalid packets that may be coming in from other nodes and have a different packet structure.

##### Power Consumption
With the implementation of the acknowledgement protocol, for the transmitter, we are able to turn off the radio immediately when an acknowledgement is received, reducing any unnecessary broadcasts. As for the receiver, we are able to turn off the radio immediately upon receiving the light packet as well.
<!--

**Here are some ideas to get you started:**

🙋‍♀️ A short introduction - what is your organization all about?
🌈 Contribution guidelines - how can the community get involved?
👩‍💻 Useful resources - where can the community find your docs? Is there anything else the community should know?
🍿 Fun facts - what does your team eat for breakfast?
🧙 Remember, you can do mighty things with the power of [Markdown](https://docs.github.com/github/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax)
-->
