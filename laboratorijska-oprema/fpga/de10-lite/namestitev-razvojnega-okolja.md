# Namestitev razvojnega okolja

## Priprava okolja

Priprava okolja sledi [navodilom. ](https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FOjZ1XG64rvc2AeRBUH5H%2Fuploads%2F7zWbbf79Gb7ZcregVAPd%2FGetting\_Started.pdf?alt=media\&token=37552df5-3d68-4bd3-9d88-f2becd6be48b)Namestitev bo potekala na OS Windows 11.

#### 1. Namestitev programa Quartus Prime&#x20;

Program je dostopen preko spletne strani IBM [povezava](https://www.intel.com/content/www/us/en/software-kit/795188/intel-quartus-prime-lite-edition-design-software-version-23-1-for-windows.html)

<figure><img src="../../../.gitbook/assets/image (15).png" alt=""><figcaption></figcaption></figure>

Poženemo datoteko in izberemo MAX 10FPGA družino čipovja (če ni že izbrano)

<figure><img src="../../../.gitbook/assets/image (16).png" alt="" width="563"><figcaption></figcaption></figure>

Ko program konča s prenosom ustreznih datotek se požene inštalacijski postopek. Dovolimo tudi namestitev gonilnikov

<figure><img src="../../../.gitbook/assets/image (17).png" alt="" width="383"><figcaption></figcaption></figure>

Po končani namestitvi se pojavi okno

<figure><img src="../../../.gitbook/assets/image (18).png" alt=""><figcaption></figcaption></figure>

#### 2. Namestitev gonilnikov za razvojno ploščo

Po končani namestitvi programa _Quartus Prime_ je potrebna še namestitev gonilnikov saj _Windows_ le teh ne ponuja. Če odpremo _Upravljalnik Naprav_ (Device Manager) lahko vidimo, da napravi USB-blaster manjkajo ustrezni gonilniki

<figure><img src="../../../.gitbook/assets/image (23).png" alt="" width="283"><figcaption></figcaption></figure>

Ustrezne gonilnike najdemo v namestitveni mapi programa _Quartus Prime_

```
C:\intelFPGA_lite\23.1std\quartus\drivers
```

Posodobimo gonilnike tako da program za posodobitev usmerimo na zgornjo pot, kjer bo OS sam našel ustrezne datoteke.

<figure><img src="../../../.gitbook/assets/image (20).png" alt=""><figcaption></figcaption></figure>
