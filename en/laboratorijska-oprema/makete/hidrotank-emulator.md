# HidroTank emulator

### 1. Opis

Maketa računalniško simulira delovanje enostavnega tekočinskega sistema v realnem času. Tekočinski sistem sestavljajo hranilnik tekočine ter ventil za dovod tekočine in ventil za odvod tekočine. Sistem je mogoče krmiliti ročno ali pa z uporabo mehanskega regulatorja.

### 2. Odprtozančni model

Odprtozančni sistem je prikazan na sliki. Sestavljajo ga dovodni ventil z merilnikom pretoka dovodne tekočine, hranilnik tekočine in odvodni ventil z merilnikom pretoka odvodne tekočine.

<figure><img src="../../.gitbook/assets/image.png" alt=""><figcaption><p>Odprtozančni model </p></figcaption></figure>

#### 2.1 Dovodni ventil

Dovodni ventil dovaja tekočino v hranilnik. Pretok tekočine v hranilnik v odvisnosti od odprtosti ventila (Position) opisuje enačba:

$$
\varphi_{\text{dovodni}}(\text{valve}) = 0.0025 \, \left[\frac{\text{m}^3}{\text{s}}\right] \cdot \text{valve} \, [\%]
$$

Povezava med odprtostjo ventila in pretokom je linearna in omejena pri 100% odprtosti ventila. Trenutno vrednost pretoka (Flow) meri merilnik, njegovo vrednost pa prikazuje prikazovalnik levo od ventila.

#### 2.2 Odvodni ventil

Odvodni ventil odvaja tekočino iz hranilnika. Pretok tekočine iz hranilnika je odvisen od odprtosti ventila in nivoja tekočine v hranilniku $$h(t)$$, opisuje pa ga enačba:

$$
\varphi_{\text{odvodni}}(\text{valve}, h) = 0.005 \, \left[\frac{\text{m}^3}{\text{s}}\right] \cdot \text{valve} \, [\%] \cdot \sqrt{2 \cdot g \cdot h(t)}
$$

Maksimalni odvodni pretok bo dosežen, ko bo nivo tekočine najvišji ($$h = 1 , \text{m}$$) in ventil popolnoma odprt ($$\text{valve} = 100%$$).

#### 2.3 Hranilnik tekočine

Nivo tekočine v hranilniku opisuje diferencialna enačba:

$$
h(t) = \int \frac{1}{S_{\text{hranilnik}}} \left( \varphi_{\text{dovodni}}(t) - \varphi_{\text{odvodni}}(t) \right) \, dt
$$

Nivo tekočine v hranilniku je odvisen od konstrukcije hranilnika in integrala razlike pretokov ter začetnega stanja nivoja, ki je implicitno podan v integralu. Hranilnik ima obliko kvadra s površino $$S = 0.1 , \text{m}^2$$ in maksimalno višino $$1  \text{m}$$. Minimalni nivo tekočine je $$0 \text{m}$$, pri nivoju več kot $$1  \text{m}$$ pa pride do preliva.

#### 2.4 Blokovna shema sistema

Blokovna shema sistema opisuje gradnike in povezave med njimi. Dovodni ventil nastavlja dovodni pretok tekočine. Dovodnemu pretoku tekočine se odšteje odvodni pretok, ki ga nastavlja odvodni ventil. Razlika pretokov nato polni hranilnik tekočine in spreminja nivo tekočine $$h(t)$$.

<figure><img src="../../.gitbook/assets/image (1).png" alt="" width="516"><figcaption><p>Blokovna shema odprtozančnega sistema</p></figcaption></figure>

### 3. Zaprtozančni model

Za razliko od odprtozančnega sistema, kjer niso podane zahteve glede vodenja, zaprtozančni sistem zahteva ustrezno vodenje sistema (nastavljanje ventilov) za dosego ustreznega nivoja tekočine v hranilniku.

<figure><img src="../../.gitbook/assets/image (2).png" alt=""><figcaption><p>Blokovna shema zaprtozančnega sistema</p></figcaption></figure>

Zaprtozančni sistem podaja zahtevan oz. referenčni nivo tekočine $$h_{\text{ref}}(t)$$. Razlika med referenčnim in dejanskim nivojem je pogrešek $$e(t) = h_{\text{ref}}(t) - h(t)$$. Regulator na podlagi pogreška izračuna ustrezno odprtje ventila $$u(t)$$ oz. dovodni pretok v hranilnik tekočine, da zmanjša pogrešek.

Maketa omogoča izvedbo dveh tipov:

* Ročni regulacijski sistem
* Mehanski regulacijski sistem

#### 3.1 Ročni regulacijski sistem

Ročni regulacijski sistem zagotavlja krmiljenje ventilov s pomočjo operaterja. Operater spremlja zahtevan oz. referenčni nivo ter ustrezno reagira z odpiranjem oz. zapiranjem ventilov.

#### 3.2 Mehanski regulacijski sistem

Mehanski regulacijski sistem zagotavlja krmiljenje dovodnega ventila preko mehanske povratne povezave.&#x20;

<figure><img src="../../.gitbook/assets/image (3).png" alt=""><figcaption><p>Mehanski regulacijski sistem</p></figcaption></figure>

Mehanski krmilnik uporablja ponton oz. plovec ter sistem mehanskih vzvodov za krmiljenje dovodnega ventila.

**Mehanski parametri**

| Oznaka | Velikost    | Enota | Opomba             |
| ------ | ----------- | ----- | ------------------ |
| l1     | 0.4         | m     | Fiksna ročica      |
| l2     | 0.5         | m     | Fiksna ročica      |
| l3     | \[0.5, 3.0] | m     | Nastavljiva ročica |
| l4     | \[0.5, 3.0] | m     | Nastavljiva ročica |
| ponton | 0.142       | m     | Višina pontona     |

**Lokacije točk glede na točko C**

| Oznaka | Lokacija (x, y) | Enota | Opomba                            |
| ------ | --------------- | ----- | --------------------------------- |
| A      | \[-0.75, y]     | m     | Prosto gibanje v vertikalni smeri |
| B      | \[x, y]         | m     | Spremenljiva točka                |
| C      | \[0, 0]         | m     | Fiksna točka                      |
| D      | \[0.5, 3.0]     | m     | Spremenljiva točka                |
| E      | \[1.34, y]      | m     | Prosto gibanje v vertikalni smeri |

Točka A krmili dovodni ventil z omejitvami gibanja: ventil je zaprt (0%) pri točki A nižje kot 0.31 m od točke C in popolnoma odprt pri točki A višje kot 0.085 m od točke C. Vmesne pozicije določa linearna enačba med skrajnima točkama.
