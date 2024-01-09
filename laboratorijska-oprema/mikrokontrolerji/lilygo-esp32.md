# LILYGO - ESP32

## Opis

<figure><img src="../../.gitbook/assets/image.png" alt="" width="375"><figcaption><p>Razvojna plošča LILYGO</p></figcaption></figure>

Razvojna plošča TTGO, z ESP32 mikrokrmilnik in TFT zaslonom, je napredna in vsestranska platforma, namenjena za razvoj in implementacijo IoT (Internet of Things) projektov. Tu so ključne značilnosti:

1. **Mikrokrmilnik ESP32**: Srce razvojne plošče je ESP32, zmogljiv mikrokrmilnik, ki podpira Wi-Fi in Bluetooth povezljivost. Ponuja veliko procesorsko moč, nizko porabo energije in je idealen za različne aplikacije, vključno s pametnimi domovi, avtomatizacijo, nadzornimi sistemi itd.
2. **TFT Zaslon**: Plošča vključuje barvni TFT zaslon, ki omogoča prikazovanje grafike, besedila in vmesnikov uporabnikov. Ta zaslon je primeren za aplikacije, ki potrebujejo vizualni izhod, kot so pametne ure, vremenske postaje ali interaktivni nadzorni sistemi.
3. **GPIO Vhodi/Izhodi**: Razvojna plošča TTGO s ESP32 in TFT zaslonom ima več GPIO (General Purpose Input/Output) priključkov, ki omogočajo povezavo z različnimi senzorji, aktuatorji in drugimi moduli.
4. **Programiranje in Razvojno Okolje**: TTGO ploščo je mogoče programirati z uporabo priljubljenih razvojnih okolij, kot so Arduino IDE, Espressif IDF ali celo MicroPython. To olajša razvoj za širok spekter razvijalcev, od začetnikov do izkušenih.
5. **Napajanje in Baterija**: Plošča je zasnovana za delovanje z različnimi viri napajanja, vključno z možnostjo priključitve na baterijo, kar omogoča njeno uporabo v prenosnih ali oddaljenih aplikacijah.

Ta razvojna plošča je idealna za hobiste, izobraževalne namene, prototipiranje in majhne do srednje velike IoT projekte.

## Arduino delovno okolje

Nastavitev delovnega okolja za razvojno ploščo TTGO obsega naslednje korake:

### 1. Inštalacija modula razvojne plošče

V Arduino okolju je potrebno dodati povezavo do zunanjega modula, saj v osnovnem IDE ni podpore za to razvojno ploščo

<figure><img src="../../.gitbook/assets/image (2).png" alt="" width="312"><figcaption><p>Pot do pojavnega okna za nastavitve Arduino okolja</p></figcaption></figure>

Ko odpremo nastavitve Arduino okolja dodamo povezavo do razvojne plošče v okno (Additional board managers URL).&#x20;

```
https://espressif.github.io/arduino-esp32/package_esp32_index.json
```

<figure><img src="../../.gitbook/assets/image (1).png" alt=""><figcaption><p>Dodajanje zunanje povezave za razvojno ploščo ESP32</p></figcaption></figure>

Ko smo dodali povezavo lahko sedaj izberemo razvojno ploščo iz nabora. Izberemo ploščo TTGO LoRa32-OLED.

<figure><img src="../../.gitbook/assets/image (3).png" alt="" width="563"><figcaption><p>Izbira razvojne plošče</p></figcaption></figure>

### 2. Inštalacija TFT prikazovalnika

TFT prikazovalnik uporablja SPI komunikacijo z ravojno ploščo LILYGO. Če želimo uporabljati ta prikazovalnik lahko izkoristimo knjižnico, ki bo poskrbela za komunikacijo ter omogočala lažjo in predvsem hitrejšo uporabo prikazovalnika.

<figure><img src="../../.gitbook/assets/image (4).png" alt="" width="423"><figcaption><p>Knjižnica za prikazovalnik</p></figcaption></figure>

Ko smo naložili knjižnico za prikazovalnik je potrebno še nastaviti pravilno konfiguracijo namreč knjižnica je splošna tako za različne dimenzije prikazovalnikov kot različnih tipov komunikacij z krmilniki. Potrebno bo urediti že dokument že nameščene knjižnice.

<figure><img src="../../.gitbook/assets/image (5).png" alt=""><figcaption><p>Dostop do datoteke za nastavitev TFT prikazovalnika</p></figcaption></figure>

Dokument najdemo med nameščenimi Arduino knjižnicami pod imenom _User\_Setup\_Select.h_

Najprej onemogočimo  (za-komentiramo) vrstico 32&#x20;

<figure><img src="../../.gitbook/assets/image (6).png" alt=""><figcaption><p>Vrstica 32</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (7).png" alt=""><figcaption><p>Onemogočimo (za-komentiramo) vrstico 32</p></figcaption></figure>

Omogočimo (od-komentiramo) vrstico 58

<figure><img src="../../.gitbook/assets/image (8).png" alt=""><figcaption><p>Izbira prave konfiguracije TFT prikazovalnika in razvojne plošče</p></figcaption></figure>

### 3. Namestitev demonstracijskega programa

V Arduino okolju izberemo enega izmed demonstracijskih programov.

<figure><img src="../../.gitbook/assets/image (9).png" alt=""><figcaption><p>Izbira demonstacijskega programa digitalna ura</p></figcaption></figure>

Priključimo ploščo in izberemo pravilni prehod (port) za namestitev

<figure><img src="../../.gitbook/assets/image (10).png" alt=""><figcaption><p>Izbira razvojne plošče in prehoda</p></figcaption></figure>

Po namestitvi se na prikazovalniku izpiše trenutni čas

<figure><img src="../../.gitbook/assets/image (13).png" alt=""><figcaption><p>Izpis na prikazovalniku po namestitvi demonstracijskega programa</p></figcaption></figure>

