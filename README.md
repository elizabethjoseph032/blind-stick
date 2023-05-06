// blind-stick
#include <Ultrasonic.h>
Ultrasonic ultrasonic(11, 12);
int distance;
int w=10,val=2;
void setup() {
  Serial.begin(9600);
  pinMode(LED_BUILTIN, OUTPUT);
  pinMode(w, INPUT);
}

void loop() {
  // Pass INC as a parameter to get the distance in inches
  distance = ultrasonic.read();
  val=digitalRead(w);
  if(distance<100 || val==0){
    digitalWrite(LED_BUILTIN, HIGH);
  }else{
    digitalWrite(LED_BUILTIN, LOW);
  }
  
  Serial.print("Distance in CM: ");
  Serial.println(distance);
  delay(1000);
}
