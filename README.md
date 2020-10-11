# Aux73_Ejer5

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
