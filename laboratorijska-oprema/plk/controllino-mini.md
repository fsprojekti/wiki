# Controllino MINI

Controllino MINI podjetja [Controllino](https://www.controllino.com/) predstavlja pol-profesionalno implementacijo Arduino razvojnih ploščic v PLK sistem.&#x20;

Gradiva:

* [uporabniška navodila](https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FOjZ1XG64rvc2AeRBUH5H%2Fuploads%2FJbzJmQr460GY2c4w9Sxh%2FminiManual.pdf?alt=media\&token=3511fd91-3ec2-48f6-8e2a-197b98b8a069)
* [električna vezava signalov](https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FOjZ1XG64rvc2AeRBUH5H%2Fuploads%2F2AWveZKx8HxqJlxtXKGR%2FminiPinout.pdf?alt=media\&token=8fd727af-bfdc-4873-bf23-45ab0a9fd637)
* [podatkovni list](https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FOjZ1XG64rvc2AeRBUH5H%2Fuploads%2F1UuDSsDUpCvJkR7ZWQCb%2FminiDatasheet.pdf?alt=media\&token=3713ae3f-3bd8-40f1-8f5a-2e6e553e2f3b)

## Opis krmilnika

Na sliki je prikazan krmilnik CONTROLLINO MINI z označenimi sestavnimi deli. Jedro krmilnika CONTROLLINO MINI temelji na mikrokrmilniku ATmega328. Ta krmilnik ima 8 vhodov brez galvanske izolacije, 4 skupne analogni/digitalne vhode, 2 izključno digitalna vhoda in 2 izključno analogna vhoda. Poleg tega ima 8 digitalnih izhodov brez galvanske izolacije in 6 relejnih izhodov, ki so vzporedno z digitalnimi. CONTROLLINO MINI je zasnovan za različne aplikacije avtomatizacije in nadzora, ponuja fleksibilnost in kompaktno zasnovo, ki je primerna za projekte manjšega obsega.

<figure><img src="../../.gitbook/assets/image.png" alt="" width="375"><figcaption><p>Controllino MINI</p></figcaption></figure>

## Električna vezava

Krmilnik električno povežemo z napajanjem in z digitalnimi vhodi in digitalnimi izhodi.

### Napajanje PLK

PLK za svoje delovanje potrebuje napajanje, v našem primeru je to enosmerna napetost 24V. Priključne sponke napajanja na PLK so prikazane na spodnji sliki.

<figure><img src="../../.gitbook/assets/image (2).png" alt="" width="375"><figcaption><p>Priključitev napajanja</p></figcaption></figure>

Oznaka na sliki 12V/24V označuje pozitivni potencial in oznaka GND negativni potencial napajalne napetosti.

### Digitalni vhodi

Vezava digitalnih vhodov na PLK nam omogoča spremljanje stanja digitalnih naprav, kot so končna stikala, tlačni stikala in vse druge vrste digitalnih naprav. Primer priklopa stikala prikazuje spodnja slika.

<figure><img src="../../.gitbook/assets/image (3).png" alt="" width="337"><figcaption><p>Priključitev PLK na vhod A2 v digitalnem načinu</p></figcaption></figure>

### Digitalni izhodi

Vezava digitalnih izhodov na PLK nam omogoča izvajanje akcij oz. spreminjanje stanj digitalnih naprav, kot so luči, releji, motorji, črpalke in druge digitalne naprave. Primer povezave bremena na digitalni relejski izhod prikazuje spodnja slika.

<figure><img src="../../.gitbook/assets/image (4).png" alt="" width="234"><figcaption><p>Priklop bremena na relejski izhod D0</p></figcaption></figure>

Digitalni izhod PLK je izveden z relejem, zato lahko breme krmilimo samo preko relejskega stikala. Na prvo sponko relejskega stikala priključimo pozitivni potencial vira (24V) na drugo sponko pa prvi konec bremena. Drugi konec bremena zvežemo na negativni potencial vira (0V).

### Uporabniški vmesnik

Uporabniški vmesnik predstavljajo vgrajene LED ki prikazujejo stanje vhodno izhodnih naprav.

<figure><img src="../../.gitbook/assets/image (5).png" alt=""><figcaption><p>LED za prikzovanje stanja vhodno izhodnih naprav</p></figcaption></figure>

Uporabniški vmesnik omogoča spremljanje stanja vhodno izhodnih naprav ne omogoča pa njihovega upravljanja.

## Programsko orodje

Programiranja Controllino MINI se lahko izvaja v več okoljih. Tukaj bomo predstavili samo Arduino IDE, ki omogoča programiranje v programskem jeziku C.

### Programiranje

Programsko orodje omogoča programiranje v dveh standardih jezikih funkcijskem diagramu (FBD) in lestvičnem diagramu (Ladder). Način izberemo pri izbiri novega projekta, kot je prikazano na spodnji sliki.

<figure><img src="../../.gitbook/assets/logonewdoc.png" alt=""><figcaption><p>Ustvarjanje novega programa</p></figcaption></figure>

Programiranje v FBD poteka grafično s postavitvijo in povezovanjem različnih funkcijskih blokov, ki so pripravljeni za uporabo v knjižnici orodja. Na sliki je prikazana postavitev funkcijskega bloka, ki predstavlja prvi digitalni vhod krmilnika, v program.

<figure><img src="../../.gitbook/assets/logoplaceblock (1).png" alt=""><figcaption><p>Postavitev funkcijskega bloka digitalnega vhoda v program</p></figcaption></figure>

Podobno uporabljamo druge vrste blokov od logičnih funkcij AND, OR, ... do sekvenčnih blokov kot so RS flip-flopi pa časovnikov, števcev in še vrsto drugih blokov, ki nam jih ponuja orodje.

### Simulacija programa

Programsko orodje omogoča tudi simulacijo programa. S simulacijo programa lahko preverimo njegovo delovanje brez da bi vplivali na digitalne izhode sistema, kar pomeni da lahko testiramo program v izoliranem virtualnem okolju. Vključitev simulatorja prikazuje spodnja slika

<figure><img src="../../.gitbook/assets/logosim.png" alt=""><figcaption><p>Z levim klikom miške lahko iz menija izberemo simulacijo</p></figcaption></figure>

Simulator upravljamo preko ukaznega menija, ki se nam izriše pod shemo. Ko simulator poženemo lahko virtualno upravljamo digitalne vhode ter opazujemo reakcije uporabljenih blokov. Če so bloki in povezave modre barve predstavlja logično 1 če pa rdeče pa logično 0. Torej če je blok Q obrobljen z rdečo črto digitalni izhod ni aktiviran in obratno če ima rob modre barve je aktiviran. Spodnja slika prikazuje povezavo bloka digitalnega vhoda z blokom digitalnega izhoda. Ker je digitalni vhod aktiviran se ta informacija prenese do izhodnega bloka preko povezave in celotna pot se obarva modro.

<figure><img src="../../.gitbook/assets/logorunsim.png" alt=""><figcaption><p>Prikaz stanj v načinu simulacije programa</p></figcaption></figure>

### Nastavitev komunikacijskega vmesnika

Pred prvim programiranjem krmilnika je potrebno krmilnik in osebni računalnik povezati z programerskim vmesnikom. Če uporabljamo operacijski sistem Windows nam sistem ob priklopu vmesnika le njega avtomatsko zazna in namesti vse potrebne gonilnike za njegovo delovanje. Ta vmesnik moramo nato pravilno nastaviti tudi v programskem okolju Soft Comfort, kot prikazuje spodnja slika (Tools $$\rightarrow$$ Options)

<figure><img src="../../.gitbook/assets/logosetinterface.png" alt=""><figcaption><p>Nastavitev serijskega vmesnika</p></figcaption></figure>

### Prenos programa na krmilnik

Prenos programa na krmilnik poteka preko ukaznega menija kot je prikazano na sliki

<figure><img src="../../.gitbook/assets/logodownload.png" alt=""><figcaption><p>Prenos programa na PLK</p></figcaption></figure>

Po prenosu programa na krmilnik je potreben še njegov zagon, saj se krmilnik zaradi varnosti nikoli sam ne prične izvajati pravkar naloženega programa. To je mogoče izvesti na dva načina preko zaslona krmilnika ali pa preko programskega orodja.

### Monitoring programa

Programsko orodje tudi omogoča spremljanje delovanje programa v realnem času, kar nudi gobji vpogled v njegovo delovanje in omogoča lažje razhroščevanje oz. odpravljanje napak. Funkcija monitoringa je dosegljiva z desnim klikom na skico kot prikazuje spodnja slika

<figure><img src="../../.gitbook/assets/logomonitor.png" alt=""><figcaption><p>Online Test omogoča vpogled v stanje spremenljivk in blokov trenutnega programa v izvajanju</p></figcaption></figure>

Monitoring prikazuje stanje programa podobno kot simulator le, da pri monitoringu ni mogoče programsko spreminjati stanja digitalnih vhodov saj so ta odvisna od stanja povezanih naprav na PLK.

## Delovanja krmilnika na primeru

Spodnja slika shematsko prikazuje povezavo med PLK ter digitalnimi izhodi in vhodi.

<figure><img src="../../.gitbook/assets/logoprikaz.png" alt=""><figcaption><p>Prikaz prehajanja informacije od izvora (stikala) preko PLK do ponora (Luč)</p></figcaption></figure>

Primer prikazuje električno vezavo dveh stikal S1 in S2 na digitalne vhode I1 in I2, električno vezavo digitalnega izhoda Q1 na luč H1, ter program, ki ju logično povezuje. Stikali S1 in S2 dobita svoji virtualni sliki v programu FDB kot vhodna bloka (I) in sta označena z I1 in I2. Ko sta stikali pritisnjena se njuna stanja preneseta v program kot logična 1 na izhodu blokov I1 in I2. Vhodna bloka sta nato povezana na blok logične funkcije in (&), ki svoj izhod postavi na logično ena samo kadar so vsi njeni vhodi enaki logični 1 (ko pritisnemo oba stikala). Ko je izhod logične in funkcije enak 1 se postavi tudi izhodni blok Q1 na logično 1, kar pomeni, da se rele sklene in, preko električne povezave na izhodu, prižge luč H1.
