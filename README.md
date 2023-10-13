<br>
Using a HC_SR04 Ultrasonic sensor to measure distance in centimeters
<br/>
<br>
<img src="https://github.com/S0undWav3s/ARDUINO_HC_SR04_Distance_Measuring/blob/main/PIC_01.jpg" width=360 HEIGHT=540>
<img src="https://github.com/S0undWav3s/ARDUINO_HC_SR04_Distance_Measuring/commit/54cda9409f4b4b8b77440b2ab373f65f24d75f2d#diff-596e74f324b2d002c68c8102cdf57e5a64380fdd7d7190af10cbd75a9367133e" width=360 HEIGHT=540>
<br/>



<br>
Arduino Code:
<br/>

```ruby
int Trigger_Pin = 10;
int Echo_Pin = 11;
float signalTime;
float Time;
float D;
// speed of sound=343 m/s

void setup() {
Serial.begin(9600);
pinMode(Trigger_Pin,OUTPUT);
pinMode(Echo_Pin,INPUT);  
}

void loop() {
digitalWrite(Trigger_Pin,LOW);             //Low Trigger
delayMicroseconds(10);                     //delay in uS
digitalWrite(Trigger_Pin,HIGH);            //High Trigger
delayMicroseconds(10);                     //delay in uS
digitalWrite(Trigger_Pin,LOW);             //Low Trigger
delayMicroseconds(10);                     //delay in uS
signalTime = pulseIn(Echo_Pin,HIGH);       //measuring time in uS when the Signal is received
delay(20);
//Serial.println(signalTime);
Time = (signalTime/1000000/2); //Convert Micro-Seconds to Seconds(divide by 1,000,000).
                               //Divide by 2 beceause the signal goes from the HC-SR04 to the object and back to the sensor(we need to measure the distance only to the object).

delay(200);
D=(34300*Time);  //  Distance = Speed * Time, Speed_of_sound = 343,000 cm/s and the time we have it from the 25 code line.
Serial.print(D);
Serial.println(" Centimeters");

}


```
