# Digital-Thermometer
Digital Thermometer Project Based on Arduino &amp; TMP36 Temperature SensorFi
Final Year Project (based on Electronics )
<br>
DESCRIPTION

I have worked with my team and made a Digital Thermometer project that controls and manages the temperature using sensor.

In this project we have made an Arduino based digital thermometer to display the

current ambient temperature on a 16x2 LCD unit in real time . It can be deployed

in houses, offices, industries etc. to measure the temperature. We can divide this

Arduino based thermometer into three sections - The first section senses the

temperature by using temperature sensor TMP36, second section converts the

temperature value into a suitable number in Celsius scale which is done by

Arduino, and the last part of the system displays temperature on LCD Display.
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
