# wireless-bot
#define m11 11    // rear motor
#define m12 12
#define m21 10    // front motor
#define m22 9
#define m3 8 //up movement
#define m4 7 // open

char str[2],i;

void forward()                                                 
{
   digitalWrite(m11, LOW);
   digitalWrite(m12, LOW);
   digitalWrite(m21, HIGH);
   digitalWrite(m22, LOW);
}

void backward()
{
   digitalWrite(m11, LOW);
   digitalWrite(m12, LOW);
   digitalWrite(m21, LOW);
   digitalWrite(m22, HIGH); 
}

void left()
{
   digitalWrite(m11, HIGH);
   digitalWrite(m12, LOW);
   delay(100);
   digitalWrite(m21, HIGH);
   digitalWrite(m22, LOW);
}

void right()
{
   digitalWrite(m11, LOW);
   digitalWrite(m12, HIGH);
   delay(100);
   digitalWrite(m21, HIGH);
   digitalWrite(m22, LOW);
}

void Stop()
{
   digitalWrite(m11, LOW);
   digitalWrite(m12, LOW);
   digitalWrite(m21, LOW);
   digitalWrite(m22, LOW);
}

void up()
{
   digitalWrite(m4, LOW);
   digitalWrite(m3, HIGH);
   
}

void open()
{
   digitalWrite(m3, LOW);
   digitalWrite(m4, HIGH);
}

void setup() 
{
  Serial.begin(9600);
  pinMode(m11, OUTPUT);
  pinMode(m12, OUTPUT);
  pinMode(m21, OUTPUT);
  pinMode(m22, OUTPUT);
  pinMODE(m3,OUTPUT);
   pinMODE(m4,OUTPUT);
}

void loop() 
{
  while(Serial.available())
  {
    char ch=Serial.read();
    str[i++]=ch;
    
    if(str[i-1]=='1')
    {
     Serial.println("Forward");
     forward();
     i=0;
    }

    else if(str[i-1]=='2')
    {
     Serial.println("Left");
     right();
     i=0;
    }

    else if(str[i-1]=='3')
    {
      Serial.println("Right");
      left();
      i=0;
    }
    
    else if(str[i-1]=='4')
    {
      Serial.println("Backward");
      backward();
      i=0;
    }

    else if(str[i-1]=='5')
    {
      Serial.println("Stop");
      Stop();
      i=0;
    }
     else if(str[i-1]=='6')
    {
      Serial.println("OPEN");
      open();
      i=0;
    }
     else if(str[i-1]=='7')
    {
      Serial.println("UP");
      UP();
      i=0;
    }
    
    delay(100);
  }
}
