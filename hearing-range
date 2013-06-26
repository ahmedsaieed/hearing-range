#include <Encoder.h>
#include <toneAC.h>
#include "math.h"
#include <LiquidCrystal.h>


///////
//long int number = 12345;
#include "Arduino.h"
void setup();
void loop();
int ScalePot(int x);
void intTo7Seg(int num);
int a,b,c,d,e,f,g;

const int num_digits = 5;

int enable_digit[num_digits];
int digits[num_digits+1];
//////



int freq = 0;
int state = 0;
const int ResetBtnPin = 22;

// initialize the library with the numbers of the interface pins
//LiquidCrystal lcd(7, 6, 2, 3, 4, 5);

Encoder myEnc1(20, 21);
Encoder myEnc1000(18, 19);

void setup() {
  // set up the LCD's number of columns and rows:
//  lcd.begin(8 , 1);
//  Serial.begin(9600);
  // set up Serial library at 9600 bps
  
  pinMode(ResetBtnPin, INPUT);


//////
  a = 25;
  b = 23;
  c = 2;
  d = 1;
  e = 0;
  f = 29;
  g = 27;
  
  enable_digit[0] = 3;
  enable_digit[1] = 4;
  enable_digit[2] = 5;
  enable_digit[3] = 6;
  enable_digit[4] = 7;

  pinMode(a, OUTPUT);
  pinMode(b, OUTPUT);
  pinMode(c, OUTPUT);
  pinMode(d, OUTPUT);
  pinMode(e, OUTPUT);
  pinMode(f, OUTPUT);
  pinMode(g, OUTPUT);
  
  pinMode(enable_digit[0], OUTPUT);
  pinMode(enable_digit[1], OUTPUT);
  pinMode(enable_digit[2], OUTPUT);
  pinMode(enable_digit[3], OUTPUT);
  pinMode(enable_digit[4], OUTPUT);
  
  digitalWrite(a, LOW);
  digitalWrite(b, LOW);
  digitalWrite(c, LOW);
  digitalWrite(d, LOW);
  digitalWrite(e, LOW);
  digitalWrite(f, LOW);
  digitalWrite(g, LOW);
  
  digitalWrite(enable_digit[0], HIGH);
  digitalWrite(enable_digit[1], HIGH);
  digitalWrite(enable_digit[2], HIGH);
  digitalWrite(enable_digit[3], HIGH);
  digitalWrite(enable_digit[4], HIGH);
  
 

////


}

void loop() {
  // freq = ScalePot(analogRead(A0));
  //
  //freq = ScalePot(myEnc1.read());
  //freq = analogRead(A0);
  // freq = myEnc.read();
  state = digitalRead(ResetBtnPin);

//  if (digitalRead(ResetBtnPin) == 0)
//    {
//      freq = 0;
//      //myEnc1.write(0);      
//      //myEnc1000.write(0);
//    }
//    else
//    {
    freq = myEnc1.read() + 1000*myEnc1000.read();
//  Serial.println(myEnc1000.read()); 
    if (freq < 0)
      freq = 0;
    else if (freq > 25000)
      freq = 25000;
//    }
  toneAC(freq); // Play the frequency (150 Hz to 15 kHz in 10 Hz steps).
//  Serial.print("Freq = ");
//  Serial.println(freq);

//  lcd.clear();
//  lcd.print(freq);
//  delay(50);
  //delay(1000);

//  for (int i = 0; i <= 10; i++)
//  {
//  lcd.print(i);
//  lcd.clear();
//  }
  //lcd.print("");
  
  
//////////

//  digits[4] = (number - ( (10*digits[3]) + (100*digits[2]) + (1000*digits[1]) + (10000*digits[0]) );
  digits[4] = freq % 10;
  Serial.println(digits[4]);
  freq = freq / 10;
  digits[3] = freq % 10;
  Serial.println(digits[3]);
  freq = freq / 10;
  digits[2] = freq % 10;
  Serial.println(digits[2]);
  freq = freq / 10;  
  digits[1] = freq % 10;
  Serial.println(digits[1]);
  freq = freq / 10;
  digits[0] = freq % 10;
  Serial.println(digits[0]);

  digitalWrite(enable_digit[0],HIGH);
  digitalWrite(enable_digit[1],HIGH);
  digitalWrite(enable_digit[2],HIGH);
  digitalWrite(enable_digit[3],HIGH);
  digitalWrite(enable_digit[4],HIGH);
 

  int current_digit = 0;
  
  for(current_digit = 0; current_digit < 5; current_digit++) {
    
    digitalWrite(enable_digit[current_digit],LOW);
    
//    delay(1);
    
    intTo7Seg (digits[current_digit]);
    
    delay(1);
    digitalWrite(enable_digit[current_digit],HIGH);
    
    digitalWrite(a, LOW);
    digitalWrite(b, LOW);
    digitalWrite(c, LOW);
    digitalWrite(d, LOW);
    digitalWrite(e, LOW);
    digitalWrite(f, LOW);
    digitalWrite(g, LOW);
    
    delay(1);
  
 
  }
  
//////////////


   }


int ScalePot(int x) {
  if (x < 0)
    return 0;
  else if ( x >= 0 && x < 25 )
    return x;
  else if ( x >= 25 && x < 1000 )
    return 2*x;
  else if ( x >= 1000 && x < 2000 )
    return 3*x;
  else if (x >= 2000 && x < 18000)
    return 5*x;
  else if (x >= 18000 && x < 19500)
    return 2*x;
  else if (x >= 19500 && x< 22000)
    return x;
  else if (x > 22000)
    return 22000;
}

void intTo7Seg(int num) {
  
  
  switch (num) {
    case 0:
    digitalWrite(a, HIGH);
    digitalWrite(b, HIGH);
    digitalWrite(c, HIGH);
    digitalWrite(d, HIGH);
    digitalWrite(e, HIGH);
    digitalWrite(f, HIGH);
    digitalWrite(g, LOW);
    
    break;
    
    case 1:
    digitalWrite(a, LOW);
    digitalWrite(b, HIGH);
    digitalWrite(c, HIGH);
    digitalWrite(d, LOW);
    digitalWrite(e, LOW);
    digitalWrite(f, LOW);
    digitalWrite(g, LOW);
    
    break;

    case 2:
    digitalWrite(a, HIGH);
    digitalWrite(b, HIGH);
    digitalWrite(c, LOW);
    digitalWrite(d, HIGH);
    digitalWrite(e, HIGH);
    digitalWrite(f, LOW);
    digitalWrite(g, HIGH);
    
    break;

    case 3:
    digitalWrite(a, HIGH);
    digitalWrite(b, HIGH);
    digitalWrite(c, HIGH);
    digitalWrite(d, HIGH);
    digitalWrite(e, LOW);
    digitalWrite(f, LOW);
    digitalWrite(g, HIGH);
    
    break;


    case 4:
    digitalWrite(a, LOW);
    digitalWrite(b, HIGH);
    digitalWrite(c, HIGH);
    digitalWrite(d, LOW);
    digitalWrite(e, LOW);
    digitalWrite(f, HIGH);
    digitalWrite(g, HIGH);
    
    break;

    case 5:
    digitalWrite(a, HIGH);
    digitalWrite(b, LOW);
    digitalWrite(c, HIGH);
    digitalWrite(d, HIGH);
    digitalWrite(e, LOW);
    digitalWrite(f, HIGH);
    digitalWrite(g, HIGH);
    
    break;

    case 6:
    digitalWrite(a, HIGH);
    digitalWrite(b, LOW);
    digitalWrite(c, HIGH);
    digitalWrite(d, HIGH);
    digitalWrite(e, HIGH);
    digitalWrite(f, HIGH);
    digitalWrite(g, HIGH);
    
    break;

    case 7:
    digitalWrite(a, HIGH);
    digitalWrite(b, HIGH);
    digitalWrite(c, HIGH);
    digitalWrite(d, LOW);
    digitalWrite(e, LOW);
    digitalWrite(f, LOW);
    digitalWrite(g, LOW);
    
    break;
    
    case 8:
    digitalWrite(a, HIGH);
    digitalWrite(b, HIGH);
    digitalWrite(c, HIGH);
    digitalWrite(d, HIGH);
    digitalWrite(e, HIGH);
    digitalWrite(f, HIGH);
    digitalWrite(g, HIGH);
    
    break;
    
    case 9:
    digitalWrite(a, HIGH);
    digitalWrite(b, HIGH);
    digitalWrite(c, HIGH);
    digitalWrite(d, HIGH);
    digitalWrite(e, LOW);
    digitalWrite(f, HIGH);
    digitalWrite(g, HIGH);
    
    break;
    
    
    
  }
  
}
