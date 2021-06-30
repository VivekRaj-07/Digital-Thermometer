# Digital-Thermometer
Digital Thermometer Project Based on Arduino &amp; TMP36 Temperature Sensor
#include <LiquidCrystal.h>

int InputPin=A5;
float temp,voAnalog;
int voDigital;
const int RS=2,E=3,D4=4,D5=5,D6=6,D7=7;
LiquidCrystal LCD(RS,E,D4,D5,D6,D7);
void setup()
{
  pinMode(InputPin,INPUT);
  LCD.begin(16,2);
}

void loop()
{
  voDigital=analogRead(A5);
  voAnalog=(voDigital*5000.0)/1023;
  temp=(voAnalog-500)/10;
  LCD.clear();
  LCD.setCursor(2,0);
  LCD.print("Temperature");
  LCD.setCursor(4,1);
  LCD.print(temp);
  LCD.write(178);
  LCD.print("C");
  delay(1000);
}
