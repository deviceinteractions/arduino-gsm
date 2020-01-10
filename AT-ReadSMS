// By Device Interactions

// A Sample code that receives an SMS sent to the used Sim Card
// Using AT-commands
// With SoftwareSerial


#include <SoftwareSerial.h>

// Setting up software serial
SoftwareSerial SIM900(7, 8);
// Define a variable to store the received SMS content in
char incoming_char=0;

void setup() {
  // Using a baud rate of 19200 for Serial communication
  SIM900.begin(19200);
  // Use a standard 9600 baud rate for the serial monitor
  Serial.begin(9600); 
  // Wait for the Sim Card to register
  delay(20000);

  // Put the SIM900 in SMS mode
  SIM900.print("AT+CMGF=1\r"); 
  delay(100);
  // Ask module to send any received SMS content via Serial to the SoftwareSerial bus 
  SIM900.print("AT+CNMI=2,2,0,0,0\r");
  delay(100);
}

void loop() {
  // Display the text received from the Module
  if(SIM900.available() >0) {
    //Get the characters from the Module
    incoming_char=SIM900.read(); 
    //Print the received characters on the Serial Monitor
    Serial.print(incoming_char); 
  }
}
