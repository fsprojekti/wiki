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



## Programska oprema

Omogoča nadzor makete **FlexDrive** s pomočjo **ESP32** mikrokontrolerja in **MATLAB/Simulink** v realnem času.&#x20;

**Repozitorij:** [fsprojekti/flexDrive-mcu](https://github.com/fsprojekti/flexDrive-mcu)

Repozitorij vsebuje dve glavni programski komponenti:

### Arduino koda (ESP32)

📌 **Lokacija**: `firmware/`\
📌 **Opis**:

* Koda je pripravljena za **ESP32**, ki deluje kot **krmilnik za FlexDrive maketo**.
* Omogoča nadzor **DC motorja** in branje podatkov iz **enkoderjev**.
* Podpira dva načina delovanja:
  * **Odprtozančni način** – Motor se poganja z neposrednim PWM signalom.
  * **Zaprtozančni način** – PID regulacija hitrosti z enkoderji.
* Vključuje **serijski vmesnik** (CLI) za upravljanje prek **računalnika**.

📌 **Ključne funkcije**:\
✅ Nastavitev hitrosti motorja z PWM signalom.\
✅ Spreminjanje smeri vrtenja motorja.\
✅ Branje podatkov iz **enkoderjev** v realnem času.\
✅ Pošiljanje podatkov preko **serijskega porta** (UART).\
✅ Nastavitev PID regulatorja (zaprtozančni način).

### **MATLAB/Simulink komunikacijski blok**

📌 **Lokacija**: `matlab/`\
📌 **Opis**:

* **MATLAB/Simulink blok NI simulacijski model**, ampak omogoča **realnočasovno povezavo** z ESP32.
* Omogoča branje podatkov in pošiljanje ukazov **direktno iz MATLAB-a/Simulinka**.
* Uporaben za spremljanje sistema in **eksperimentiranje** v realnem času.

📌 **Ključne funkcije**:\
✅ Pošiljanje ukazov ESP32 za nadzor motorja.\
✅ Pridobivanje podatkov iz enkoderjev v MATLAB-u.\
✅ Možnost implementacije lastnih **regulacijskih algoritmov** v Simulinku.

### **Kako uporabljati ta repozitorij?**

#### **1️⃣ Namestitev kode na ESP32**

1. Prenesi repozitorij ali skopiraj kodo iz `firmware/`.
2. Odpri projekt v **Arduino IDE** ali **PlatformIO**.
3. Priključi ESP32 na računalnik.
4. Naloži program (`Upload`).

#### **2️⃣ Uporaba CLI za nadzor**

Po naložitvi kode lahko ESP32 upravljaš preko **serijske povezave**.\
📌 **Primeri ukazov**:

<pre class="language-bash"><code class="lang-bash"><strong>set_pwm 100       // Nastavi PWM signal na 100
</strong>set_dir 1         // Nastavi smer vrtenja motorja (1 = naprej, 0 = nazaj)
read_encoder 1    // Preberi vrednost enkoderja 1
</code></pre>

#### **3️⃣ Povezava z MATLAB/Simulink**

1. Odpri **MATLAB** in naloži skripte iz `matlab/`.
2. Poveži MATLAB s **serijskim portom** ESP32.
3. Uporabi Simulink blok za komunikacijo z napravo v realnem času.

### **🔌 Povezava in konfiguracija**

ESP32 komunicira z računalnikom preko **serijskega porta**.\
📌 **Privzete serijske nastavitve**:

* **Baudrate**: `115200`
* **Data bits**: `8`
* **Parity**: `None`
* **Stop bits**: `1`

Uporabnik lahko pošilja ukaze prek **serijskega monitorja** v Arduino IDE, PuTTY, CoolTerm ali MATLAB.

### **🛠️ Struktura ukazov**

Ukazi so v obliki:

```bash
code<ukaz> [parametri]
```

* Argumenti so ločeni s presledki.
* Nekateri ukazi vračajo **potrditev** ali podatke.
* Če ukaz ni pravilno vnesen, ESP32 vrne napako.

***

### **📌 Seznam spremenljivk**

| Spremenljivka | Vrednost (privzeta) | Pomen in uporaba                                                                                                                              |
| ------------- | ------------------- | --------------------------------------------------------------------------------------------------------------------------------------------- |
| **mode**      | `0`                 | <p>Način delovanja:<br>• <code>0</code>: Odprtozančni (brez PID regulacije)<br>• <code>1</code>: Zaprtozančni (z uporabo PID regulatorja)</p> |
| **state**     | `0`                 | <p>Stanje sistema:<br>• <code>0</code>: Ustavljeno<br>• <code>1</code>: V teku (motor deluje)</p>                                             |
| **pwmESC**    | `0`                 | Trenutna PWM vrednost za krmiljenje motorja (uporabno v odprtozančnem načinu)                                                                 |
| **dir**       | `1`                 | <p>Smer vrtenja motorja:<br>• <code>1</code>: Naprej<br>• <code>0</code>: Nazaj (reverse)</p>                                                 |
| **ref**       | `0.3`               | Referenčna hitrost (obratov/s), uporabljena v zaprtozančnem načinu                                                                            |
| **Kp**        | `0.1`               | Proporcionalni faktor PID regulatorja                                                                                                         |
| **Ki**        | `0.0`               | Integralni faktor PID regulatorja                                                                                                             |
| **Kd**        | `0.0`               | Diferencialni faktor PID regulatorja                                                                                                          |
| **pwmMax**    | `4000`              | Maksimalna dovoljena PWM vrednost                                                                                                             |
| **plot**      | `false`             | Zastavica, ki omogoča (true) ali onemogoča (false) realnočasovno risanje/pošiljanje podatkov                                                  |

***

### **📌 Seznam CLI ukazov**&#x20;

#### **🔧 Sistem nadzor**

| Ukaz   | Opis                                                                                       |
| ------ | ------------------------------------------------------------------------------------------ |
| `init` | Inicializira sistem in pripravi vse module.                                                |
| `run`  | Zažene sistem (motor začne delovati).                                                      |
| `stop` | Ustavi sistem (motor ustavi delovanje).                                                    |
| `list` | Izpiše trenutno stanje sistema (način, stanje, PWM, smer, PID nastavitve, enkoderji itd.). |

#### **⚙️ Nadzor motorja**

| Ukaz                 | Opis                                                                                                                                                                                                                                                                                |
| -------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `mode <0 or 1>`      | <p>Nastavi način delovanja:<br>• <strong>0 (odprtozančni):</strong> Motor deluje s fiksno PWM vrednostjo, brez PID regulacije.<br>• <strong>1 (zaprtozančni):</strong> Motor deluje s PID regulatorjem, ki prilagaja PWM glede na razliko med referenčno in dejansko hitrostjo.</p> |
| `pwm <vrednost>`     | Nastavi PWM vrednost motorja (vrednost med 0 in `pwmMax`). Velja predvsem v odprtozančnem načinu.                                                                                                                                                                                   |
| `dir <0 or 1>`       | <p>Nastavi smer vrtenja:<br>• <strong>0:</strong> Nazaj (reverse)<br>• <strong>1:</strong> Naprej (forward)</p>                                                                                                                                                                     |
| `pwm_max <vrednost>` | Nastavi maksimalno PWM vrednost (vrednost mora biti vsaj 100).                                                                                                                                                                                                                      |

#### **📏 PID regulacija**

| Ukaz             | Opis                                                                        |
| ---------------- | --------------------------------------------------------------------------- |
| `ref <vrednost>` | <p>Nastavi referenčno hitrost <br>(v obratih/s, med -10.0 in 10.0).<br></p> |
| `kp <vrednost>`  | <p>Nastavi proporcionalni faktor </p><p>(omejeno med 0 in 100).<br></p>     |
| `ki <vrednost>`  | <p>Nastavi integralni faktor </p><p>(omejeno med 0 in 100).<br></p>         |
| `kd <vrednost>`  | <p>Nastavi diferencialni faktor </p><p>(omejeno med 0 in 100).<br></p>      |

#### **🛠 Enkoderji in podatki**

| Ukaz                     | Opis                                                                                                                              |
| ------------------------ | --------------------------------------------------------------------------------------------------------------------------------- |
| `read_encoder <1 or 2>`  | Prebere in izpiše trenutno vrednost izbranega enkoderja (1 ali 2).                                                                |
| `reset_encoder <1 or 2>` | Ponastavi števec izbranega enkoderja (1 ali 2) na 0.                                                                              |
| `plot <0 or 1>`          | Omogoči (1) ali onemogoči (0) realnočasovno pošiljanje podatkov (enkoderske vrednosti, hitrost, PWM ipd.) prek serijske povezave. |

***
