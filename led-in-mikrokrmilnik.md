# LED in mikrokrmilnik

Če želimo prenesti informacijo iz mikrokrmilnika na LED moramo zgraditi električno vezje. Gradnjo električnega vezja pričnemo z izdelavo električne sheme.

## Električna shema

Električna shema povezuje LED in mikrokrmilnik kot je prikazano na sliki.

LED dioda z oznako **LED1** je povezana na eni strani na pin **D12** in na drugi strani na upor $R\_1$. Upor $R\_1$ je na drugi strani povezan na nizek potencial mikrokrmilnika.

Delovanje vezja:

* Ko program na izhod mikrokrmilnika zapiše informacijo logično visoke vrednosti se na pinu **D12** pojavi napetost $5V$. Skozi LED diodo in upor steče tok in LED dioda zasveti.

!> **POZOR** V električnih vezjih je potrebno poskrbeti za zaščito elementov. LED dioda za pravilno delovanje potrebuje zaščito upora.

Za pravilno delovanje LED diode moramo dodati upor v naše vezje ter ga pravilno dimenzionirati glede na lastnosti LED diode.

## Električne komponente

| Komponenta      | Koda         | Proizvajalec | Podatkovni list |
| --------------- | ------------ | ------------ | --------------- |
| LED             | HLMP-Y301    | AVAGO        | datoteka        |
| mikrokrmilnik   | ATmega328    | Microchip    | datoteka        |
| razvojna plošča | Arduino Nano | Gravitech    | datoteka        |
| upor            | /            | Multicomp    | datoteka        |

## Dimenzioniranje komponent

Pri dimenzioniranju komponent si pomagamo s shemo na sliki, ki prikazuje električne veličine vezja.

### Upor $R\_1$

Iz podatkovnega lista LED diode razberemo podatek o maksimalnemu toku diode (DC Forward Current), ki znaša $20mA$. Odločimo se, da LED dioda dovolj sveti tudi pri polovičnem toku $10mA$, zato bomo dimenzionirali vezje na ta tok. Padec napetosti na diodi pri toku $10mA$ je približno $2V$, kar razberemo iz karakteristike:

Vrednost upora $R\_1$ izračunamo po enačbi:

$$
R_1 = \frac{U_{R_1}}{I_F}=\frac{U_{CC}-U_F}{I_F}
$$

Vstavimo poznane veličine:

* $U\_{CC}=5V$ napajalna napetost mikrokontrolerja
* $U\_F=2V$ padec napetosti na LED diodi pri izbranem toku
* $I\_F=10mA$ izbrani tok skozi diodo

$$
R_1 = \frac{5V-2V}{10mA}=300\Omega
$$
