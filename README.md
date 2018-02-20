# tcp-simulator-master

Objective
---------
Your source ports # and destination port # has become the corresponding agent IDs. (111, 001, 100). Watch out for the final length of the fields according to the packet specification given. 

•	Sequence number is a random number that you generate for your communication. Once decided you will use this field to keep track of the message lengths sent for the variable part data based on the TCP principles. 

•	A three-way handshake must be performed to establish the sequence number and acknowledgement number. 

•	You should use your knowledge on DRP, TER, URG, ACK, RST, SYN, FIN to use it properly during the communication. Refer to textbook for details. 
•	You can use the receiver window to rate limit the other user in communication 
•	checksum should be calculated as per the Internet checksum and should be calculated on first 16 Bytes. 
•	Urgent point could be used to point to anywhere when the URG is set can sent any detail as communication between agents. 
•	Keep of log of the communication. Each agent have to log the messages in the order in which they are transacted. Each agent has to keep a separate log file for each of the communication opened. Eg. if agent Chan is communicating with agent Jan and agent Ann he has to have two log files one for each communication. 
•	wait for an ack. Once you sent a message you will have to wait until you get the ack back. I have simplified by completely removing the window concept. So, there should be a one-to-one mapping between a message and an ack. You won’t send a message until you get back an ack back. 
•	Reliability: one in 5 packets gets lost between everyone, so you may have to recover it by correctly identifying it using the ack and retransmitting it. This is one of your key challenges to ensure the agents gets all the messages in order. They can’t afford to miss any of the messages. You will have to run a timer at each agent side to estimate the loss of packet. You can set the timer to a value not less than 20 seconds. For this getting done you have field in the packet header called DRP which the router will check to decide whether to forward the packet or not. 


What tasks to perform
---------------------
• checksum should be calculated as per the Internet checksum and should be calculated on first 16 Bytes.
• After the 5th message from agent Chan, agent Ann realizes something odd had happened and goes eerie about continuing communication with agent Chan.
• Agent Ann has to communicate this information with agent Jan. with an URG pointer on.
• Agent Ann has to download the complete set of communication transaction with agent Chan and terminate all the connections with agent Chan using the RST flag in TCP.
• There is pointer in the header field called the TER which enabled will terminate the process and you will exit out of the client program.
• Agent Jan establishes with the Air-force Headquarters and orders a air-strike. The mission goes well and now the target is destroyed. Now agent Jan has to terminate connection as per TCP norms and signal agent Ann about the success.


How to run the code
--------------------

1.	Open the folder containing the code in a Linux environment, if preferable.
2.	Open terminal pointing to the said folder. 
3.	Run the "missiontcp.server.py" file on the terminal.
4.	Repeat step 2 and run the "ann.py", "jan.py" & "chan.py" files from different terminals.
5.	Allow the three-way handshake to happen for all clients.
6.	By default, port numbers for Ann, Jan and Chan are 2001, 2002, 2003 respectively.
7.	Pick a client, say Ann, and provide the file you want to send by specifying the path to file and provide the destination client port number, say Jan, and press enter.
8.	The Dijkstra's algorithm determines the shortest path between the clients over the network and sends the file.
9.	File is received by the client, in this case Jan.
10.	Connection is terminated.



