# Upravljanje digitalnih izhodov

Z mikrokrmilnikom bomo izmenično na $$1s$$ prižigali in ugašali LED. Z zapisovanjem na digitalne izhode, prenesemo informacijo iz krmilnika na izhodne pine mikrokrmilnika. Izhodni pini nato krmilijo aktuator, v našem primeru je to LED. Nalogo razdelimo v dva dela elektrotehnični in programski.

## Elektrotehnični del

Elektrotehnični del zahteva izgradnjo električnega vezja, ki ga sestavlja LED, mikrokrmilnik in pomožne komponente. Primer izgradnje takega vezja je na voljo v gradivu

### Programski del

Pri pisanju kode si bomo pomagali s funkcijami iz knjižnice Arduino projekta.

* [pinMode()](https://www.arduino.cc/reference/en/language/functions/digital-io/pinmode/)
* [digitalWrite()](https://www.arduino.cc/reference/en/language/functions/digital-io/digitalwrite/)

Primer programa, ki izmenično (na 1s) spreminja vrednost digitalnega izhoda.

```c
//Globalne konstante
//Pin 1 mikrokrmilnika
int K1pin = 1;

//Nastavitvena funkcija
void setup() {
  //K1pin nastavimo v način digitalnega izhoda
  pinMode(K1pin, OUTPUT);
}

//Krožna funkcija
void loop() {
  //Zapisovanje izhodov
  //Digitalni izhod K1pin nastavimo na visok napetostni potencial (5V za arduino Nano)
  digitalWrite(K1pin, HIGH);
  //Ustavimo izvajanje programa za 1s
  delay(1000);
  //Digitalni izhod K1pin nastavimo na nizek napetostni potencial (0V)
  digitalWrite(K1pin, LOW);
  //Ustavimo izvajanje programa za 1s
  delay(1000);
}
```
