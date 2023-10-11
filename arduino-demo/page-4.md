# Branje digitalnih signalov

Brali bomo stanje tipke ter ga shranili v pomnilnik mikrokrmilnika. Z branjem digitalnih signalov prenesemo informacijo digitalnega senzorja v krmilnik, preko vhodnega pina. Nalogo razdelimo v dva dela elektrotehnični in programski.

## Elektrotehnični del

Elektrotehnični del zahteva izgradnjo električnega vezja, ki ga sestavlja tipka, mikrokrmilnik in pomožne komponente. Primer izgradnje takega vezja je na voljo v[ gradivu](<../README (1).md>).

### Programski del

Pri pisanju kode si bomo pomagali s funkcijami iz knjižnice Arduino projekta.

* [pinMode()](https://www.arduino.cc/reference/en/language/functions/digital-io/pinmode/)
* [digitalRead()](https://www.arduino.cc/reference/en/language/functions/digital-io/digitalread/)

Primer programske kode, ki prebere informacijo digitalnega vhoda in jo zapiše v globalno spremenljivko programa.

```c
//Globalne konstante
//Pin 0 tipka
int S0pin = 0;

//Globalne spremenljivke
//Spremenljivka tipke
bool S0 = false;

//Nastavitvena funkcija
void setup() {
  //S0pin nastavimo v način digitalnega vhoda
  pinMode(S0pin, INPUT);
}

//Krožna funkcija
void loop() {
  //Branje digitalnih vhodov
  S0 = digitalRead(S0pin);
}
```
