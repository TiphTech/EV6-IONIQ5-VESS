
Fork from the very good job of hughsie https://github.com/hughsie/mobis-vess
Thank you Hunghsie for this impressive work

The VESS is the Virtual Engine Sound System found in many KIA and Hyundai
branded vehicles. A system like VESS has been required by law for electric
vehicles (EVs) since 2020 by EU law.

Roadmap:
===

Buy a VESS system from an used EV6/IONIQ5 -> DONE
inspect the electronic board, list the relevant components -> DONE
finding UART signals to connect with RS485 module -> DONE

connecting the board to a computer with a terminal and RS485 bus
extracting the row SPI flash content
exploiting flash content (audio) -> DONE (flash dump by SPI)
editting audio with: lower backup sound (dong) and other sound like ASD inside sound of my Kia EV6 (Dynamic sound)
upload this modified content on the SPI Flash
Test and enjoy!


This research is not aimed at disabling VESS as you can do that very simply
by just unplugging it. The work here is some reverse engineering based on the
physical inspection only.

Many thanks to [Eric Reuter](https://www.youtube.com/watch?v=OLT1aKdpYhs) with
open source [code](https://github.com/ereuter/vess).
Done on older VESS sytem (kia Eniro probably?) https://github.com/hughsie/mobis-vess


VESS Diagram (EV6/ioniq5)
===

<img width="450" height="315" alt="VESS Diagram" src="https://github.com/user-attachments/assets/4f5528ee-c480-480e-a99d-62734dd28519" />


PCB
===

![Carte avec tags](https://github.com/user-attachments/assets/ab245523-b0b8-4015-b4ed-f4498b058b0b)


Components:

Yellow
----

BF704CCPZ Analog Devices 400Mhz DSP

Red
----

U1169A3 high-speed CAN

Green
----

Q128JVEAQ WINBOND SERIAL FLASH MEMORY WITH DUAL/QUAD SPI 128mb

Orange
----

FDA803 (1x45W Class D amplifier)





UART RS485 bus on BF704CCPZ Analog Devices 400Mhz DSP :

<img width="230" height="237" alt="Sans titre2" src="https://github.com/user-attachments/assets/fcaa7ccc-e3df-4d2f-ad48-d1f8d475b604" />

<img width="230" height="237" alt="Sans titre" src="https://github.com/user-attachments/assets/b1986c53-ca0f-4a05-bb7c-4a0be1a09777" />




Flash Dump:
===

After unsoldering the SPI flash memory and extracting the data with a CH341A flash drive and Neoprogrammer ->

<img width="480" height="250" alt="Capture Néoprogrammer" src="https://github.com/user-attachments/assets/314620f0-2071-4ecd-915f-0c38c92ec5b0" />




I can hear the different soundtracks emitted by the VESS with Audacity by going to File/Import/Raw Data ->

<img width="700" height="230" alt="Audacity" src="https://github.com/user-attachments/assets/d632944b-e75a-4903-957d-459841d533e2" />




I will now be able to modify these different sounds by replacing them with the ASD (Active Sound Design) samples, which I find more pleasant, and reduce the volume of the reverse beep



