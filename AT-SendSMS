// By Device Interactions

// A Sample code that sends an SMS to a specified Mobile Number
// Using AT-commands
// With SoftwareSerial

// Power the SIM900 with a 12V2A adapter

// Follow these connections:
// Connect the Module GND to Arduino GND
// Connect the Module TX to Arduino Pin 7
// Connect the Module RX to Arduino Pin 8


#include <SoftwareSerial.h>

// Setting up software serial
SoftwareSerial SIM900(7, 8); 

void setup() {
  // Using a baud rate of 19200 for Serial communication
  SIM900.begin(19200);
  // Waiting for the Sim Card to register
  delay(20000);   
  
  // Call the SMS function
  sendSMS();
}

void loop() { 
  // No recurring logic
}

void sendSMS() {
  // Put the SIM900 in SMS mode
  SIM900.print("AT+CMGF=1\r"); 
  delay(100);

  SIM900.println("AT + CMGS = \"+919895460246\""); // Target Mobile number here
  delay(100);
  // Other international telephone codes can be added in place of '+91' at the start of the number
  
  SIM900.println("Message example from Arduino Uno."); // Your SMS content here 
  delay(100);

  // Send the end character for AT Commands
  SIM900.println((char)26); 
  delay(100);
  SIM900.println();
  // Wait for the module to process the command and send the SMS
  delay(6000); 
}
