#include<LiquidCrystal.h>
LiquidCrystal lcd(6,7,8,9,10,11);

#define Fan 3
#define Light 4
#define TV 5
// Defining Arduino Pins to control devices

int temp=0,i=0;
int led=13;
char str[15];
// Initialising relevant variables

void setup()
{
  lcd.begin(16,2);
  // Initializing LCD Display
  Serial.begin(9600);
  //Initializing Serial
  
  pinMode(led, OUTPUT);
  pinMode(Fan, OUTPUT);
  pinMode(Light, OUTPUT);
  pinMode(TV, OUTPUT);
  // Initializing Control Pins
  
  lcd.setCursor(0,0);
  lcd.print("GSM Control Home");
  lcd.setCursor(0,1);
  lcd.print("   Automaton    ");
  // Write initialization message to LCD Display
  
  delay(2000);
  lcd.clear();
  lcd.print("Circuit Digest");
  delay(1000);
  lcd.setCursor(0,1);
  lcd.print("System Ready");
   // Write System Ready message on LCD Display
  
  Serial.println("AT+CNMI=2,2,0,0,0");
  delay(500);
  Serial.println("AT+CMGF=1");
  // Send AT Command to GSM Module to start reading SMS Messages
  
  delay(1000);
  lcd.clear();
  lcd.setCursor(0,0);
  lcd.print("Fan   Light  TV ");
  lcd.setCursor(0,1);
  lcd.print("OFF    OFF   OFF "); 
  // Display current status of all devices
}

// Loop function
void loop()
{
  lcd.setCursor(0,0);
  lcd.print("Fan   Light  TV");
  // Display device names 
  
  if(temp==1) // check value of temp flag
  {
    check(); // run check function
    temp=0;  // reset value of temo flag
    i=0;     // reset value of i
    delay(1000);
  }
}

 void serialEvent() 
 {
  while(Serial.available())
  {
    if(Serial.find("#A."))        // look for the characters that start the command
    {
      digitalWrite(led, HIGH);    // flash the indication LED
      delay(1000);
      digitalWrite(led, LOW);
      while (Serial.available())  // when serial data is available, receive and store in inChar
      {
      char inChar=Serial.read();
      str[i++]=inChar;
      if(inChar=='*')
      {
        temp=1;   // set value of temp flag as 1
        return;
      } 
      } 
    }
   }
 }

void check()
{
   // when the incoming command is TV - ON
   if(!(strncmp(str,"tv on",5)))
    {
      digitalWrite(TV, HIGH);
      lcd.setCursor(13,1); 
      lcd.print("ON    ");
      delay(200);
    }  
   
   // when the incoming command is TV - OFF   
   else if(!(strncmp(str,"tv off",6)))
    {
      digitalWrite(TV, LOW);
      lcd.setCursor(13,1); 
      lcd.print("OFF    ");
      delay(200);
    }

   // when the incoming command is Fan - ON
    else if(!(strncmp(str,"fan on",5)))
    {
      digitalWrite(Fan, HIGH);
      lcd.setCursor(0,1); 
      lcd.print("ON   ");
      delay(200);
    }

   // when the incoming command is Fan - OFF
    else if(!(strncmp(str,"fan off",7)))
    {
      digitalWrite(Fan, LOW);
      lcd.setCursor(0,1); 
      lcd.print("OFF    ");
      delay(200);
    }

   // when the incoming command is Light - ON
    else if(!(strncmp(str,"light on",8)))
    {
      digitalWrite(Light, HIGH);
      lcd.setCursor(7,1); 
      lcd.print("ON    ");
      delay(200);
    }
   // when the incoming command is Light - OFF 
    else if(!(strncmp(str,"light off",9)))
    {
      digitalWrite(Light, LOW);
      lcd.setCursor(7,1); 
      lcd.print("OFF    ");
      delay(200);
    } 

   // when the incoming command is All - ON
    else if(!(strncmp(str,"all on",6)))
    {
      digitalWrite(Light, HIGH);
      digitalWrite(Fan, HIGH);
      digitalWrite(TV, HIGH);
      lcd.setCursor(0,1); 
      lcd.print("ON     ON    ON  ");
      delay(200);
    }
    
   // when the incoming command is All - OFF 
    else if(!(strncmp(str,"all off",7)))
    {
      digitalWrite(Light, LOW);
      digitalWrite(Fan, LOW);
      digitalWrite(TV, LOW);
      lcd.setCursor(0,1); 
      lcd.print("OFF   OFF    OFF  ");
      delay(200);
    }     
}
