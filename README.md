# Chat-Application
A Client/Server chat application using Java sockets

Basic Concepts
Server :
To communicate with the client, the server uses two type of sockets
ServerSocket : this class is used by the server to declare a ServerSocket object which the server needs to listen to connection requests from the clients
Socket : this class is used by the server to declare a Socket object, which the server uses to send and recieve data from the client
Client :
To communicate with the server, the client uses one single socket which’s an object from Socket class, to send and recieve data from server
=> the instantiating of Socket class in server and client is different even though it is the same class but it differs from client to the server.

1- Server.java
To begin with, we declare 5 objects:
final ServerSocket serversocket : this line means we declared an object called “ serversocket” which is an object of the class ServerSocket. It is declared “ final” which means it is a constant
final Socket clientSocket : this line means we declared an object called “ clientsocket” which is an object of the class Socket. It is declared “ final” which means it is a constant
final BufferedReader in : this line means we declared an object called “ in” which is an object of the class BufferedReader. It is used to read data from the clientSocket object
final PrintWriter out : this line means we declared an object called “ out ” which is an object of the class PrintWriter. It is used to write data into the clientsocket object
=> In all above code, we just declared the objects , we still didn’t instanciate them.
final Scanner sc = new Scanner(System.in) : this line of code means we created an object from the class Scanner called “ sc” to be able to read data from the user’s keybord

new InputStreamReader( clientSocket.getInputStream()) : creates a stream reader for the socket. However this stream reader only reads data as Bytes , therefore it must be passed to BufferedReader to be converted into characters.
Now that all objects we will use are created, we will start implementing two threads :
Sender thread : it contains the code the server will use to send messages to client
Recieve thread : it contains the code the server will use to recieve messages from client
Sender thread
Now in this part, we will read data from user and we send this data to the client.

The class Thread in Java has its own default run() method which should contains the code that the thread will execute. However it can’t be executed, unless you call the method start() on that thread . Also , Since in every different thread we have a different code to implement , we use @Override annotation .
Recieve thread
In this part we implement the recieve thread.
We read data that is sent from the client using the “ in” object associated to the clientSocket using the method readLine().
This method reads line by line the message sent by the client, if this method returns null that means that the client is not connected anymore. It doesn’t mean that the client didn’t send anything because the client can be connected to the server and still doesn’t send anything.

When the client is not connected to the server anymore we should close all sockets and streams we used using the method close(). Also, we put all the code inside a try/catch so we can print any error related to reading data or closing sockets and streams.
