# Installing the development environment

## Environment setup

Follow the [setup instructions](https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FOjZ1XG64rvc2AeRBUH5H%2Fuploads%2F7zWbbf79Gb7ZcregVAPd%2FGetting_Started.pdf?alt=media\&token=37552df5-3d68-4bd3-9d88-f2becd6be48b). This walkthrough uses Windows 11.

#### 1. Installing Quartus Prime

Download the software from the [Intel website](https://www.intel.com/content/www/us/en/software-kit/795188/intel-quartus-prime-lite-edition-design-software-version-23-1-for-windows.html).

<figure><img src="../../../.gitbook/assets/image (28).png" alt=""><figcaption></figcaption></figure>

Run the downloaded file and select the MAX 10 FPGA device family if it is not already selected.

<figure><img src="../../../.gitbook/assets/image (29).png" alt="" width="563"><figcaption></figcaption></figure>

After downloading the required files, the installer starts. Allow it to install the drivers as well.

<figure><img src="../../../.gitbook/assets/image (30).png" alt="" width="383"><figcaption></figcaption></figure>

The following window appears when installation is complete.

<figure><img src="../../../.gitbook/assets/image (31).png" alt=""><figcaption></figcaption></figure>

#### 2. Installing the development board drivers

After installing _Quartus Prime_, install the board drivers. If the drivers are missing, _Windows Device Manager_ shows the USB-Blaster device without a suitable driver.

<figure><img src="../../../.gitbook/assets/image (36).png" alt="" width="283"><figcaption></figcaption></figure>

The required drivers are in the _Quartus Prime_ installation directory:

```
C:\intelFPGA_lite\23.1std\quartus\drivers
```

Update the device driver and point Windows to the directory above so it can find the required files.

<figure><img src="../../../.gitbook/assets/image (33).png" alt=""><figcaption></figcaption></figure>
