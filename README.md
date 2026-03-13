
Fork from the very good job of hughsie https://github.com/hughsie/mobis-vess
Thank you Hunghsie for this impressive work

The VESS is the Virtual Engine Sound System found in many KIA and Hyundai
branded vehicles. A system like VESS has been required by law for electric
vehicles (EVs) since 2020 by EU law.

Roadmap:
===

Buy a VESS system from an used EV6/IONIQ5 -> DONE

inspect the electronic board, list the relevant components -> DONE

extracting the raw SPI flash content -> DONE (flash dump by SPI on the WINDBOND chip)

exploiting flash content (audio) -> DONE

editting audio with: a more discrete backup sound (dong) and other sound more sportly/loud (like Porsche Taycan / Audi Etron GT) -> DONE

upload this modified content on the SPI Flash -> DONE

Test and enjoy! -> DONE :)


This research is not for disabling VESS as you can do that very simply
by just unplugging it / remove the fuse
The work here is some reverse engineering




VESS Diagram (EV6/ioniq5)
===

<img width="450" height="315" alt="VESS Diagram" src="https://github.com/user-attachments/assets/3e467a28-4e12-439f-9f10-0f62ec27a568" />


PCB
===


![Carte avec tags](https://github.com/user-attachments/assets/46a87d98-69b4-4499-974d-78e8195dd8b8)


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


<img width="230" height="237" alt="Sans titre" src="https://github.com/user-attachments/assets/35ab83cf-156b-4bb8-bb3a-474fdc6200b3" />


Flash Dump:
===

After unsoldering the SPI flash memory and extracting the data with a CH341A flash drive and Neoprogrammer ->


<img width="480" height="250" alt="Capture Néoprogrammer" src="https://github.com/user-attachments/assets/9562ee37-46fc-452f-9dfa-46fbd7b1247c" />



First section is the firmware, contains the DSP parameters (Blackfin)
I can hear the different soundtracks emitted by the VESS with Audacity by going to File/Import/Raw Data/Signed 16bits ->
Some sounds are not used on this VESS, only the last three sounds are used (idle, on mouvement and backup dong)

<img width="700" height="230" alt="Audacity" src="https://github.com/user-attachments/assets/b3710b9e-4010-4f11-8438-653b70597a88" />

[VESS_ORIGINAL_EV6.wav](https://github.com/user-attachments/files/22508095/VESS_ORIGINAL_EV6.wav)


I will now be able to modify these different sounds by replacing them with the ASD (Active Sound Design) samples, which I find more pleasant, and reduce the volume of the reverse beep

Now I'm using a programming probe I can change/update my custom firmware easily than unsolder/solder the flash or soldering wires

[![Watch the video](https://img.youtube.com/vi/AxEAFgkC4BY/maxresdefault.jpg)](https://www.youtube.com/shorts/AxEAFgkC4BY)

[![Watch the video](https://img.youtube.com/vi/nm0Z0WLq8IQ/maxresdefault.jpg)](https://www.youtube.com/shorts/nm0Z0WLq8IQ)
