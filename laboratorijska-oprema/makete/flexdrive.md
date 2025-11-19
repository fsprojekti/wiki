# FlexDrive

<figure><img src="../../.gitbook/assets/image (1) (1).png" alt=""><figcaption><p>FlexDrive maketa</p></figcaption></figure>

### Opis makete

Maketa FlexDrive je laboratorijska naprava namenjena za podrobno raziskovanje in razumevanje mehanike elastično sklopljenih pogonskih sistemov. Mehanski del naprave sestavljati dve gredi ki sta preko elastične sklopke mehko vpeti. Na vpeti gredi je togo pritrjen vztrajnik na gnani gredi pa je togo pritrjen elektro motor, ki poganja celoten sklop. Blokovna shema prikazuje vse elemente v obliki blokov in signale ki jih povezujejo

<figure><img src="../../.gitbook/assets/image (4).png" alt=""><figcaption><p>Bločna shema makete</p></figcaption></figure>

Bloki makete:

* mehanska naprava
* merilnik zasuka na gnani gredi (Drive shaft)
* merilnik zasuka na vpeti gredi (Load shaft)
* DC motor
* gonilnik motorja
* mikrokrmilnik
* računalnik

Signali makete:

* $$U_{DC}$$ zvezni napetostni signal za pogon DC motorja
* $$M(t)$$ navor ki ga motor dovaja na gnano gred
* $$\phi_1(t)$$zasuk vpete gredi
* $$\phi_2(t)$$zasuk gnane gredi
* $$AB(t)$$kvadratični signal enkoderja
* $$U_{an}$$analogni signal enkoderja (samo vpeta gred)
* $$PWM(t)$$digitalni signal za komunikacijo z gonilnikom motorja

### Mehanska naprava

Mehanska naprava je rotirajoči dinamičen sistem in je shematično prikazan na sliki

<figure><img src="../../.gitbook/assets/image (1) (1) (1).png" alt=""><figcaption><p>Shema mehanskega dela makete</p></figcaption></figure>

Napravo sestavljajo vpeta os, ki z vztrajnostjo $$J_2$$. Na vpeto os je togo pritrjen vztrajnih z vztrajnostjo $$J_1$$. Os je v podnožje vpeta preko dveh ležajev s skupnim dušenjem $$B_1$$. Gibanje vpete osi opisuje kot $$\phi_2(t)$$. Vpeta os je preko vzmetne sklopke s konstano $$k$$ mehko povezna na gnano os, katere vztrajnostni moment podaja $$J_3$$. Gnana os je togo vpeta na motor z dušenjem $$B_2$$. Gibanje gnane osi opisuje kot $$\phi_1(t)$$, navor $$M(t)$$pa dovaja elektro motor.

* Spremenljivke sistema

| Oznaka                                       | Opis                               | Enota  |
| -------------------------------------------- | ---------------------------------- | ------ |
| <p><span class="math">M(t)</span></p><p></p> | Navor, ki ga povzroča elektromotor | $$Nm$$ |
| $$\phi_1$$                                   | Kot rotacije gnane osi             | °      |
| $$\phi_2$$                                   | Kot rotacije vpeto osi             | °      |

* Parametri sistema

| Oznaka  | Opis                          | Vrednost | Enota          |
| ------- | ----------------------------- | -------- | -------------- |
| $$B_1$$ | Dušenje vpete osi             |          | $$kg/s$$       |
| $$B_2$$ | Dušenje gnane osi             |          | $$kg/s$$       |
| $$J_1$$ | Vztrajnosti moment vztrjanika | 0.612    | $$g \cdot m²$$ |
| $$J_2$$ | Vztrajnostni moment vpete osi | 0.0902   | $$g \cdot m²$$ |
| $$J_3$$ | Vztrajnostni moment gnane osi | \~0      | $$g \cdot m²$$ |
| $$k$$   | konstanta vzmeti              |          | $$N/m$$        |

### Merilnik zasuka gnana gred

Gnana gred je opremljena z merilnikom zasuka oz. kota. Nameščen je magnetni inkrementalni enkoder [RLS AM4096](https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FOjZ1XG64rvc2AeRBUH5H%2Fuploads%2FyzCheUulIy3s2L2ZKiW7%2FAM4096D02_09.pdf?alt=media\&token=98176deb-bbd0-47c8-8e04-4e16f1c4bee7) slovenskega podjetja [RLS d.o.o.](https://www.rls.si/). Merilnik je nameščen na razvojni ploščici [RMK-AM4096](https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FOjZ1XG64rvc2AeRBUH5H%2Fuploads%2FbyXYN1jzgBNJ6AE5CL2T%2FRMK4D01_02.pdf?alt=media\&token=79a8c043-1cb3-4de8-b4c9-b0015d1d1cb4). Merilnik meri relativno gibanje osi ter posreduje informacijo v obliki digitalnega signala mikrokrmilniku.&#x20;

### Merilnik zasuka vpeta gred

Vpeta gred je opremljena z merilnikom zasuke oz. kota. Nameščen je optični inkrementalni enkoder podjetja  [POLOLU](https://www.pololu.com/) z podatkovni listom  [POLOLU-4883](https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FOjZ1XG64rvc2AeRBUH5H%2Fuploads%2FFI9ruRMcNiLlxmRKPVba%2Fpololu-25d-metal-gearmotors.pdf?alt=media\&token=f1a4c430-3dc9-469c-b787-b65e03a61922).&#x20;

{% hint style="info" %}
Med enkoderjem in vpeto osjo je nameščen zobniški sistem z razmerjem 20.4:1. Kar je potrebno upoštevali pri izračunu zasuka!&#x20;
{% endhint %}

### Elektromotorski pogon

Vrtenje vpete osi dosežemo z elektromotorjem. Maketa ima vgrajen elektromotor [POLOLU-4883](https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FOjZ1XG64rvc2AeRBUH5H%2Fuploads%2FFI9ruRMcNiLlxmRKPVba%2Fpololu-25d-metal-gearmotors.pdf?alt=media\&token=f1a4c430-3dc9-469c-b787-b65e03a61922) podjetja [POLOLU](https://www.pololu.com/). Prestavno razmerje motorja je 20.4:1.

### Gonilnik elektromotorja

Za pogon enosmernega motorja skrbi motorski gonilnik[ MD10C R3 ](https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FOjZ1XG64rvc2AeRBUH5H%2Fuploads%2FsN0uYqGXUT1pKGO2iOuc%2FA1TemgvjKjL.pdf?alt=media\&token=e0621c34-4375-4835-b94b-6c76b18cf1ee)podjetja [Cytron](https://www.cytron.io/). Gonilnik upravljamo z dvema digitalnima signaloma $$power$$ in $$direction$$. Signal $$power$$ predstavlja PWM (Pulse Width Modulation) moduliran signal $$direction$$ pa smer toka na izhodu gonilnika, kar posledično določa smer vrtenja enosmernega elektromotorja.&#x20;

## Električni del

Električna shema naprave povezuje Arduino mikrokrmilnik z dvema inkrementalnima dajalnikoma in regulatorjem enosmernega motorja. Serijska povezave med mikrokrmilnikom in mikroračunalnikom ni prikazana. Povezave digitalnih signalov z Arduinom so predstavljene v tabeli

| Naprava          | Pin | Arduino Pin | Oznaka povezave | vhod/izhod |
| ---------------- | --- | ----------- | --------------- | ---------- |
| Magnetni enkoder | A   | 32          | A1              | vhod       |
| Magnetni enkoder | B   | 33          | B1              | vhod       |
| Optični enkoder  | A   | 36          | A2              |            |
| Optični enkoder  | B   | 37          | B2              |            |
| Gonilnik motor   | DIR | 25          | DIR             | izhod      |
| Gonilnik motor   | PWM | 26          | PWM             | izhod      |

### Električne komponente

Seznam vse uporabljenih električnih komponent:

<table><thead><tr><th>Komponenta</th><th width="174">Oznaka</th><th>Proizvajalec</th><th>Podatkovni list</th></tr></thead><tbody><tr><td>Magnetni enkoder</td><td>RLS AM4096</td><td><a href="https://www.rls.si/">RLS d.o.o.</a></td><td><a href="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FOjZ1XG64rvc2AeRBUH5H%2Fuploads%2FbyXYN1jzgBNJ6AE5CL2T%2FRMK4D01_02.pdf?alt=media&#x26;token=79a8c043-1cb3-4de8-b4c9-b0015d1d1cb4">datoteka</a></td></tr><tr><td>Optični enkoder</td><td>POLOLU</td><td><a href="https://www.pololu.com/">POLOLU</a></td><td><a href="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FOjZ1XG64rvc2AeRBUH5H%2Fuploads%2FFI9ruRMcNiLlxmRKPVba%2Fpololu-25d-metal-gearmotors.pdf?alt=media&#x26;token=f1a4c430-3dc9-469c-b787-b65e03a61922">datoteka</a></td></tr><tr><td>Gonilnik motor</td><td>MD10C R3</td><td><a href="https://www.cytron.io/">Cytron</a></td><td><a href="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FOjZ1XG64rvc2AeRBUH5H%2Fuploads%2FsN0uYqGXUT1pKGO2iOuc%2FA1TemgvjKjL.pdf?alt=media&#x26;token=e0621c34-4375-4835-b94b-6c76b18cf1ee">datoteka</a></td></tr><tr><td>Mikrokrmilnik</td><td>ESP32 - LILYGO</td><td><a href="https://www.espressif.com/en/products/modules/esp32">Espressif</a></td><td><a href="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FOjZ1XG64rvc2AeRBUH5H%2Fuploads%2Fzm4t7rH9GXGytU5nTjB7%2FESP-32%20Dev%20Kit%20C%20V2_EN.pdf?alt=media&#x26;token=bf2beae7-b3bd-435d-b155-cd2a164210b9">datoteka</a></td></tr></tbody></table>



## Programska oprema - CLI

***

V tem razdelku je predstavljeno, kako uporabnik komunicira z napravo neposredno preko serijske povezave. Vključeni so vsi ukazi (CLI), opis njihovih funkcij, primeri uporabe ter načini vizualizacije meritev preko Arduino Serial Plotterja.

### **1. Struktura ukazov (CLI)**

Maketa FlexDrive uporablja preprosto in pregledno tekstovno ukazno vrstico (CLI), ki omogoča neposredno komunikacijo med uporabnikom in ESP32 krmilnikom preko Arduino Serial Monitorja ali katerega koli drugega terminala (npr. PuTTY, CoolTerm, RealTerm).

Ukazi se vnašajo kot navadne besedilne vrstice, npr.:

```
mode 1
ref 0.5
kp 5
run
```

Vsak ukaz ima osnovno obliko:

```
<ukaz> <parameter>
```

Nekateri ukazi nimajo parametrov in se uporabljajo samostojno:

```
run
stop
list
```

### **1.2. Krmiljenje v odprti zanki (open loop)**

V odprti zanki (open-loop) sistem ne uporablja povratne informacije o hitrosti. Motor vrtiš neposredno s podajanjem PWM signala in nastavitvijo smeri. Ta način je primeren za testiranje, diagnostiko ali učenje osnov delovanja sistema.

Najpogostejši ukazi v open-loop načinu so:

```
mode 0
pwm 1200
dir 1
run
```

Pomen posameznih ukazov:

* **mode 0**\
  Preklopi način delovanja v odprto zanko (brez regulacije).
* **pwm**\
  Nastavi PWM med 0 in `pwm_max` (privzeto 4000).\
  Ta ukaz določa moč motorja.
* **dir <0|1>**\
  Nastavi smer vrtenja:
  * 0 = naprej
  * 1 = nazaj
* **run**\
  Zažene motor z zadnjimi nastavljenimi PWM in dir parametri.

Primer hitrega testiranja motorja:

```
mode 0
pwm 800
run
```

Primer spreminjanja smeri med delovanjem:

```
dir 1
pwm 1000
```

Za ustavitev sistema:

```
stop
```

### **1.3. Krmiljenje v zaprti zanki (PID)**

V zaprti zanki (closed-loop) FlexDrive uporablja povratno informacijo iz enkoderja za regulacijo hitrosti motorja.\
To pomeni, da sistem samodejno prilagaja PWM signal, da doseže željeno referenčno hitrost.

Closed-loop način omogoča:

* stabilno hitrost,
* kompenzacijo obremenitev,
* ponovljivost,
* učenje osnov PID regulacije.

Za vklop zaprte zanke uporabimo:

```
mode 1
```

Ključni ukazi za regulacijo hitrosti:

* **ref**\
  Nastavi referenčno hitrost v _obr/s_ (turns per second).\
  Primer: `ref 0.6` pomeni 0.6 obrata na sekundo.
* **kp**\
  Nastavi proporcionalni faktor (–1000 do +1000).\
  Višji Kp → hitrejši odziv, lahko pa povzroči oscilacije.
* **ki**\
  Nastavi integralni faktor (0 do 100).\
  Odpravlja statično napako, a lahko povzroči prekomerno integracijo.
* **kd**\
  Nastavi diferencialni faktor (0 do 100).\
  Duši hitre spremembe in zmanjšuje nihanje.

Po nastavitvi PID parametrov zapremo regulacijsko zanko z ukazom:

```
run
```

Primer popolne konfiguracije PID regulacije:

```
mode 1
ref 0.5
kp 8
ki 0.2
kd 0.05
run
```

Spreminjanje referenčne hitrosti med delovanjem:

```
ref 1.2
```

Spreminjanje PID parametrov v realnem času:

```
kp 12
ki 0.3
kd 0.1
```

Zaustavitev zaprte zanke:

```
stop
```

Nasvet: Če motor vibrira, sunkovito pospešuje ali preskakuje hitrost, zmanjšajte Kp ali povečajte Kd.

### **1.4. Branje položaja in hitrosti**

FlexDrive omogoča napredno spremljanje podatkov preko serijskega porta ter nastavitev pomembnih parametrov, ki vplivajo na stabilnost meritev, odzivnost regulacije in hitrost prikaza podatkov.

V tej skupini so ukazi:

* za filtriranje hitrosti (alpha),
* nastavitev časa vzorčenja regulacijske zanke (ts),
* klasični “raw” plot,
* napredni plotting za Arduino Serial Plotter,
* nastavitve intervala izrisa (plot\_period).

***

**FILTRIRANJE HITROSTI (LOW-PASS FILTER)**

Parameter **alpha** določa stopnjo glajenja merjene hitrosti iz enkoderja.

Večja alpha (npr. 0.4) → hitrejši odziv, manj glajenja\
Manjša alpha (npr. 0.05) → počasnejši odziv, bolj gladka hitrost

Nastavitev:

```
alpha 0.1
```

Veljavne vrednosti: 0.00 … 1.00

***

**NASTAVITEV ČASA VZORČENJA (ts)**

Ukaz **ts** nastavi čas med posameznimi cikli regulacije v milisekundah.

Manjši ts → hitrejše vzorčenje → hitrejša regulacija\
Večji ts → počasnejša regulacija → manj procesorske obremenitve

Primer:

```
ts 10
```

***

**“RAW” PLOT (KOMPATIBILNO Z ENOSTAVNIMI TERMINALI)**

To je starejši način pošiljanja podatkov, pri katerem ESP32 ciklično izpisuje:

* položaje enkoderjev
* hitrosti

Vklop:

```
plot 1
```

Izklop:

```
plot 0
```

***

**SERIJSKI PLOTTER – OPEN LOOP**

Za uporabo z Arduino Serial Plotter lahko prikazuje:

* pwm
* dejansko hitrost

Aktivacija:

```
plotSerialOpen
```

Primer izrisa med delovanjem open-loop:

```
mode 0
pwm 1200
run
plotSerialOpen
```

***

**SERIJSKI PLOTTER – CLOSED LOOP**

V zaprti zanki Serial Plotter izriše 3 signale:

* pwm
* referenčno hitrost
* dejansko hitrost

Aktivacija:

```
plotSerialClosed
```

Primer:

```
mode 1
ref 0.8
kp 10
run
plotSerialClosed
```

***

**NASTAVITEV FREKVENCE PLOTTINGA (plot\_period)**

Parameter določa, da se podatki izrišejo samo vsak _plot\_period-ti_ ciklus.

Primer:\
ts = 10 ms\
plot\_period = 5\
→ plotting vsakih 50 ms

Nastavitev:

```
plot_period 5
```

Minimalna vrednost:

```
plot_period 1
```

***

**HITRA KOMBINACIJA ZA TEST**

```
alpha 0.15
ts 10
plot_period 3
plotSerialClosed
```

### **1.5. Napredni ukazi (diagnostika, omejitve, informacije o sistemu)**

V tem poglavju so zbrani vsi ukazi, ki omogočajo pregled stanja, konfiguracijo varnostnih omejitev ter pridobivanje sistemskih informacij. Ti ukazi so posebej pomembni pri diagnostiki, učenju ter pravilnem nastavljanju sistema FlexDrive.

***

**IZPIS TRENUTNEGA STANJA SISTEMA (list)**

Ukaz **list** prikaže popolno stanje naprave:

* način delovanja (open/closed loop)
* stanje (run/stop)
* PWM vrednost in smer
* PID parametre
* referenčno hitrost
* filtriranje (alpha)
* čas vzorčenja (ts)
* plot način
* hitrost in položaje enkoderjev

Primer:

```
list
```

To je najpomembnejši ukaz za diagnostiko.

***

**INFORMACIJE O FIRMWARE (version)**

Ukaz izpiše verzijo naloženega firmware-a:

```
version
```

***

**OMEJITEV NAJVEČJE PWM VREDNOSTI (pwm\_max)**

Določa največjo dovoljeno PWM vrednost, ki jo lahko doseže ESC. S tem zaščitimo motor in napajalnik pred prevelikimi tokovi.

Primer:

```
pwm_max 3000
```

Minimalna dovoljena vrednost je 100.

***

**NASTAVITEV SMERI VRTENJA (dir)**

Določa smer rotacije motorja:

* 0 = forward
* 1 = reverse

Primer:

```
dir 0
```

***

**ROČNI NADZOR (pwm + dir) — DIAGNOSTIČNI MODE**

V open-loop načinu lahko ročno upravljamo motor:

```
mode 0
dir 1
pwm 1500
run
```

***

**ZAČETNA INICIALIZACIJA SISTEMA (init)**

Inicializira notranje spremenljivke, uporabno pri čistih testih:

```
init
```

***

**USTAVITEV IN ZAGON SISTEMA (stop / run)**

Zaustavitev motorja:

```
stop
```

Ponovni zagon z obstoječimi nastavitvami:

```
run
```

***

**KRATEK POVZETEK DIAGNOSTIČNIH UKAZOV**

```
list        # izpis stanja
version     # verzija firmware
pwm_max 4000 # omejitev PWM
dir 0       # smer
init        # ponastavitev notranjih vrednosti
stop        # zaustavi motor
run         # zažene motor
```

### 1.6. Pregledna tabela vseh ukazov (CLI)

Spodnja tabela povzema vse razpoložljive ukaze FlexDrive sistema, skupaj s parametri, dovoljenimi vrednostmi in opisom njihove funkcije.

| Ukaz             | Parameter     | Območje vrednosti     | Opis                                          |
| ---------------- | ------------- | --------------------- | --------------------------------------------- |
| mode             | 0 / 1         | 0 = open, 1 = closed  | Izbira načina delovanja                       |
| run              | –             | –                     | Zažene motor / regulacijo                     |
| stop             | –             | –                     | Ustavi motor                                  |
| ref              | vrednost      | –10.0 … 10.0 (obr/s)  | Nastavi referenčno hitrost                    |
| pwm              | vrednost      | 0 … pwm\_max          | Ročna nastavitev PWM v open-loop              |
| pwm\_max         | vrednost      | ≥ 100                 | Omeji največji PWM                            |
| dir              | 0 / 1         | 0 = naprej, 1 = nazaj | Smer vrtenja motorja                          |
| kp               | vrednost      | –1000 … 1000          | Proporcionalni faktor PID regulacije          |
| ki               | vrednost      | 0 … 100               | Integralni faktor PID regulacije              |
| kd               | vrednost      | 0 … 100               | Diferencialni faktor PID regulacije           |
| alpha            | vrednost      | 0.0 … 1.0             | Filter za glajenje hitrosti (low-pass filter) |
| ts               | vrednost (ms) | ≥ 1                   | Čas vzorčenja regulacijske zanke              |
| plot             | 0 / 1         | 0 = izklop, 1 = vklop | Stari “raw” način izrisa podatkov             |
| plotSerialOpen   | –             | –                     | Plot PWM + hitrost (open-loop)                |
| plotSerialClosed | –             | –                     | Plot PWM + ref + hitrost (closed-loop)        |
| plot\_period     | vrednost      | ≥ 1                   | Izris vsak _n_-ti cikel                       |
| list             | –             | –                     | Izpis trenutnega stanja celotnega sistema     |
| version          | –             | –                     | Prikaz verzije firmware                       |
| init             | –             | –                     | Ponastavi notranje vrednosti sistema          |

***

#### 2. Povezava z MATLAB-om

V tem razdelku je prikazano, kako MATLAB komunicira z maketo FlexDrive, bere podatke, pošilja ukaze ter izvaja meritve, ki se uporabljajo pri laboratorijskih vajah.

**2.1. Vzpostavitev serijske komunikacije v MATLAB-u**

**2.2. Pošiljanje ukazov iz MATLAB-a**

**2.3. Branje podatkov v realnem času**

**2.4. Zajem časovnih potekov (step response, sinus, šum)**

**2.5. Obdelava podatkov in izris grafov**

**2.6. Primeri MATLAB skript za laboratorijske naloge**

**2.7. Analiza in izvoz podatkov za PID nastavitve**
