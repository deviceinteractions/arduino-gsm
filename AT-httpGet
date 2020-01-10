// Device Interactions

// A Sample code that sends a HTTP GET request to a server and prints the results
// Using AT-commands
// With SoftwareSerial

// Power the SIM900 with a 12V2A adapter

// Follow these connections:
// Connect the Module GND to Arduino GND
// Connect the Module TX to Arduino Pin 7
// Connect the Module RX to Arduino Pin 8

#include <SoftwareSerial.h>
// Set up serial & softwareserial instance called SIM900
SoftwareSerial SIM900(8, 7);
void setup() {
  SIM900.begin(19200);	
  Serial.begin(9600);	
  delay(20000);
  // Wait for the SIM Card to register
}

void loop() {
  Serial.println("HTTP get method :");
  Serial.print("AT\\r\\n");
  SIM900.println("AT");	// Check Communication
  delay(5000);
  ShowSerialData();	// Print response on the serial monitor
  delay(5000);
  /* Configure bearer profile 1 */
  Serial.print("AT+SAPBR=3,1,\"CONTYPE\",\"GPRS\"\\r\\n");		
  SIM900.println("AT+SAPBR=3,1,\"CONTYPE\",\"GPRS\"");	// Set Connection type as GPRS
  delay(5000);
  ShowSerialData();
  delay(5000);
  Serial.print("AT+SAPBR=3,1,\"APN\",\"TATA.DOCOMO.INTERNET\"\\r\\n");	
  SIM900.println("AT+SAPBR=3,1,\"APN\",\"TATA.DOCOMO.INTERNET\"");	
  // Access Point Name of the provider
  // Google this to find your Sim Card's APN
  delay(5000);
  ShowSerialData();
  delay(5000);
  Serial.print("AT+SAPBR=1,1\\r\\n");
  SIM900.println("AT+SAPBR=1,1");	// Open GPRS context
  delay(5000);
  ShowSerialData();
  delay(5000);
  Serial.print("AT+SAPBR=2,1\\r\\n");
  SIM900.println("AT+SAPBR=2,1");	// Query the GPRS context
  delay(5000);
  ShowSerialData();
  delay(5000);
  Serial.print("AT+HTTPINIT\\r\\n");
  SIM900.println("AT+HTTPINIT"); // Initialize HTTP service
  delay(5000); 
  ShowSerialData();
  delay(5000);
  Serial.print("AT+HTTPPARA=\"CID\",1\\r\\n");
  SIM900.println("AT+HTTPPARA=\"CID\",1");	// Set parameters for HTTP session
  delay(5000);
  ShowSerialData();
  delay(5000);
  Serial.print("AT+HTTPPARA=\"URL\",\"https://yesno.wtf/api\"\\r\\n");
  SIM900.println("AT+HTTPPARA=\"URL\",\"https://yesno.wtf/api\"");	// Set parameters for HTTP session
  // We are testing this with the Yes or No API, which randomly responds as either yes or no
  delay(5000);
  ShowSerialData();
  delay(5000);
  Serial.print("AT+HTTPACTION=0\\r\\n");
  SIM900.println("AT+HTTPACTION=0");	// Start GET session
  delay(10000);
  ShowSerialData();
  delay(10000);
  Serial.print("AT+HTTPREAD\\r\\n");
  SIM900.println("AT+HTTPREAD");	// Read data from HTTP server
  delay(8000);
  ShowSerialData();
  delay(8000);
  Serial.print("AT+HTTPTERM\\r\\n");  
  SIM900.println("AT+HTTPTERM");	// Terminate HTTP service
  delay(5000);
  ShowSerialData();
  delay(5000);
  Serial.print("AT+SAPBR=0,1\\r\\n");
  SIM900.println("AT+SAPBR=0,1"); // Close GPRS context
  delay(5000);
  ShowSerialData();
  delay(5000);
}

void ShowSerialData()
{
  while(SIM900.available()!=0)	// If data is available on serial port
  Serial.write(char (SIM900.read()));	// Print character received on to the serial monitor
}
