# Aux73_Ejer5

//servidor TCP
import java.io.*;
import java.net.*;
class TCPServer { public static void main(String argv[]) throws Exception {
String clientSentence;
String capitalizedSentence;
// Crear el socket servidor 
ServerSocket welcomeSocket = new ServerSocket(6789);
// Bucle infinito esperando conexiones de clientes
while (true) {
// Espera conexión de un cliente, y cuando la hay esta genera un socket secundario asociado al cliente
Socket connectionSocket = welcomeSocket.accept();
// Crea un input stream 
BufferedReader inFromClient = new BufferedReader(new InputStreamReader(connectionSocket.getInputStream()));
// Crea un output stream asociado 
DataOutputStream outToClient = new DataOutputStream(connectionSocket.getOutputStream());
// Lee la línea que manda el cliente
clientSentence = inFromClient.readLine();
// Convirtiendo la a mayusculas
capitalizedSentence = clientSentence.toUpperCase() + '\n';
// Escribe la línea hacia el cliente
outToClient.writeBytes(capitalizedSentence);
}}}

//cliente TCP
import java.io.*;
import java.net.*;
class TCPClient {
public static void main(String argv[]) throws Exception{
String sentence;
String modifiedSentence;
//Crea input stream (de texto) 
//Crea el socket cliente y conecta al servidor
    Socket clientSocket = new Socket("server.com", 6789);
    //Crea output stream (de bytes) asociado al socket
    DataOutputStream outToServer = new DataOutputStream(clientSocket.getOutputStream());
    //Lee una línea de teclado
    sentence = inFromUser.readLine();
    //Envía la línea al servidor
    outToServer.writeBytes(sentence + '\n');
    //Lee la línea devuelta por el servidor
    modifiedSentence = inFromServer.readLine();
    System.out.println("FROM SERVER: " + modifiedSentence);
    //Cierre del socket
    clientSocket.close();
    }
}
