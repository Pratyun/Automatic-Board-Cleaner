char data = 0;           //Variable for storing received data
int motor1pin1 = 10;
int motor1pin2 = 11;

int motor2pin1 = 12;
int motor2pin2 = 13;

void setup() 
{
    Serial.begin(9600);  //Sets the data rate in bits per second (baud) for serial data transmission
    pinMode(13, OUTPUT); //Sets digital pin 13 as output pin

    // put your setup code here, to run once:
  pinMode(motor1pin1, OUTPUT);
  pinMode(motor1pin2, OUTPUT);
  pinMode(motor2pin1, OUTPUT);
  pinMode(motor2pin2, OUTPUT);
}

void loop()
{
    if(Serial.available() > 0)       // Send data only when you receive data:
    {
        data = Serial.read();        //Read the incoming data and store it into variable data
        Serial.print(data);          //Print Value inside data in Serial monitor
        Serial.print("\n");          //New line 
        if(data == '1')              //Checks whether value of data is equal to 1 
            digitalWrite(13, HIGH);  //If value is 1 then LED turns ON
        else if(data == '0')         //Checks whether value of data is equal to 0
            digitalWrite(13, LOW);   //If value is 0 then LED turns OFF
            
       digitalWrite(motor1pin1, HIGH);
       digitalWrite(motor1pin2, LOW);

       digitalWrite(motor2pin1, HIGH);
       digitalWrite(motor2pin2, LOW);
       delay(1000);

       digitalWrite(motor1pin1, LOW);
       digitalWrite(motor1pin2, HIGH);

       digitalWrite(motor2pin1, LOW);
       digitalWrite(motor2pin2, HIGH);
       delay(1000);

    }                            
}
