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

Programiranja Controllino MINI se lahko izvaja v več okoljih.  Arduino IDE omogoča programiranje v programskem jeziku C.

### Nastavitev Arduino okolja

### Nastavitev komunikacijskega vmesnika

### Prenos programa na krmilnik

### Monitoring programa

### Pogoste težave

* stk500 error pri nalaganju na PLK

To težavo odpravimo s&#x20;

