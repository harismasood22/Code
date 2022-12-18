int Motor_A_Enable = 10;  
int Motor_A_Reverse = 6; 
int Motor_A_Forward = 7;
int Motor_B_Enable = 11; 
int Motor_B_Reverse = 9; 
int Motor_B_Forward = 8;

void setup() {
  Serial.begin(9600);
  pinMode(Motor_A_Enable, OUTPUT);  pinMode(Motor_A_Forward, OUTPUT);   pinMode(Motor_A_Reverse, OUTPUT); //Left Motor
  pinMode(Motor_B_Enable, OUTPUT);  pinMode(Motor_B_Forward, OUTPUT);   pinMode(Motor_B_Reverse, OUTPUT); //Right Motor
}

void loop() {

  if(Serial.available() > 0)
  {
   char data = Serial.read();
    Serial.println(data);

    switch (data)
    {
      case 'F': //FORWARD
        analogWrite(Motor_A_Enable, 255); digitalWrite(Motor_A_Forward, LOW);  digitalWrite(Motor_A_Reverse, HIGH);
        analogWrite(Motor_B_Enable,255); digitalWrite(Motor_B_Forward, LOW);  digitalWrite(Motor_B_Reverse, HIGH);
        Serial.println(Motor_A_Enable);
        Serial.println(Motor_B_Enable);
        Serial.println(Motor_A_Forward);
        Serial.println(Motor_A_Reverse);
        Serial.println(Motor_A_Forward);
        Serial.println(Motor_B_Reverse);
        
        
        break;

         case 'B': //Backwards
        analogWrite(Motor_A_Enable, 255); digitalWrite(Motor_A_Forward, HIGH);  digitalWrite(Motor_A_Reverse, LOW);
        analogWrite(Motor_B_Enable, 255); digitalWrite(Motor_B_Forward, HIGH);  digitalWrite(Motor_B_Reverse, LOW);
        Serial.println(Motor_A_Enable);
        Serial.println(Motor_B_Enable);
        Serial.println(Motor_A_Forward);
        Serial.println(Motor_A_Reverse);
        Serial.println(Motor_A_Forward);
        Serial.println(Motor_B_Reverse);
        break;

         case 'L': //Right R tha yahan
        analogWrite(Motor_A_Enable, 255); digitalWrite(Motor_A_Forward, HIGH);  digitalWrite(Motor_A_Reverse, LOW);
        analogWrite(Motor_B_Enable, 255); digitalWrite(Motor_B_Forward, LOW);  digitalWrite(Motor_B_Reverse, HIGH);
        break;

         case 'R': //Left L tha yahan
        analogWrite(Motor_A_Enable, 255); digitalWrite(Motor_A_Forward, LOW);  digitalWrite(Motor_A_Reverse, HIGH);
        analogWrite(Motor_B_Enable, 255); digitalWrite(Motor_B_Forward, HIGH);  digitalWrite(Motor_B_Reverse, LOW);
        break;

         case 'S': //NOS
        analogWrite(Motor_A_Enable, 255); digitalWrite(Motor_A_Forward, LOW);  digitalWrite(Motor_A_Reverse, LOW);
        analogWrite(Motor_B_Enable, 255); digitalWrite(Motor_B_Forward, LOW);  digitalWrite(Motor_B_Reverse, LOW);
        break; 
 /*      case 'I':
        analogWrite(Motor_A_Enable, 255); digitalWrite(Motor_A_Forward, HIGH);  digitalWrite(Motor_A_Reverse, HIGH);
        analogWrite(Motor_B_Enable, 255); digitalWrite(Motor_B_Forward, LOW);  digitalWrite(Motor_B_Reverse, LOW);
   */  
      default: //If bluetooth module receives any value not listed above, both motors turn off
        analogWrite(Motor_A_Enable, 0);
        analogWrite(Motor_B_Enable, 0);
    }
  }
}