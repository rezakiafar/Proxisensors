# MQ9gassensor-buzzer-lcd-arduinouno
#include <LiquidCrystal.h>    

LiquidCrystal lcd( 12, 11, 5, 4, 3, 2); //(rs,en,D4,D5,D6,D7);
 
void setup() {
  
  analogReference(DEFAULT);
  pinMode(A0, INPUT);        
  pinMode(0, INPUT_PULLUP);  
  pinMode(1, OUTPUT);        
  lcd.begin(16, 2);          
  lcd.clear();
  lcd.setCursor(0, 0);
  lcd.print("Hi Reza");
}
void loop() {
  float a ;                     
  int   MQ9 , P;
 
  P = digitalRead(0);           
  if(P==1) digitalWrite(1, 0);   
  if(P==0) digitalWrite(1, 1);   
  a = analogRead(A0);            
  MQ9 = (a * 100) / 1023 ;       
 
  lcd.setCursor(0, 1);                  
  lcd.print("Gas amount= "); 
  lcd.setCursor(7, 1);    
  lcd.print(MQ9);                
  lcd.print("%");               
  lcd.setCursor(2, 1);               
  delay(1000); 
  lcd.clear();                  
}
