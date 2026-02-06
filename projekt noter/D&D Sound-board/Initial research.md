Makro tastatur til kontrol af lydeffekter under D&D kampagner.
# komponent kandidater
## Micro processor:
### ~~ATMega32U4~~
~~denne processor har rimelig hukommelse og indbygget USB 2.0, der er derfor ikke behov for ekstern USB til seriel konvertering.~~

~~der kan adderes flash til ved behov for at gemme opsætning for eksempel, eller hvis der bliver programmeret UI ind i enheden~~

- ~~Datablad på ATMega32U4 - ~~https://www.microchip.com/en-us/product/atmega32u4

### ~~STM32G4~~
- ~~USB C interface~~
- ~~4 x SPI~~
~~stm32g4-~~ https://www.st.com/en/microcontrollers-microprocessors/stm32g431c6.html

### RP2040
Raspberry processor kompatibel de ønsker der er til telemetri
**Telemetri**
* 1 x QSPI 
* 2 x SPI
* 1 x UART
* 1 x USB PHY (USB 1.1)
## USB-C interface
1. Sikkerhed modstande 5.1 kohm
	- **CC1 & CC2:** Forbind en **5.1kΩ modstand** fra hver af disse pins til stel (GND). Uden dem vil en USB-C til USB-C forbindelse ikke levere strøm.
	- **Data:** Forbind USB D+ og D- direkte til RP2040 (husk at køre dem som et diff-par på dit PCB).
2. 12 MHz crystal er nødvendig for at USB timingen bliver korrekt

## Flash
RP2040 har ingen intern flash, så du **skal** have en ekstern QSPI chip (f.eks. **MX25L12872FM2I-10G** for 16MB lager).

- **Routing:** Hold banerne mellem RP2040 og flash-chippen så korte som overhovedet muligt. QSPI kører med høje frekvenser, så signalintegritet er vigtig her.
- **Pins:** Brug de dedikerede QSPI-pins på RP2040 (GPIO 0-5 bruges typisk ikke til dette; der er specifikke pins til flash).


## Buck converter
Hvorfor TPS561246DRLR er velegnet

- **Lille størrelse**: Den bruger en meget kompakt **SOT-563**-pakke (1.6 mm x 1.6 mm), hvilket er perfekt til et pladsbegrænset PCB-design.
- **Høj effektivitet**: Som en synkron buck-converter med integrerede FET'er er den meget effektiv, hvilket betyder mindre spildvarme sammenlignet med en lineær regulator.
- **Simpel implementering**: Den kræver et minimalt antal eksterne komponenter, hvilket forenkler dit kredsløbsdesign.
- **Passende specifikationer**:
    - **Inputspænding**: Fra 4.2V til 17V, så 5V fra USB er inden for området.
    - **Outputspænding**: Justerbar fra 0.6V til 7V. Du skal bruge to eksterne modstande for at indstille den præcist til **3.3V**.
    - **Strøm**: Kan levere op til 1A kontinuerlig strøm, hvilket er rigeligt til din RP2040 og de tilhørende komponenter.
## Knap
### Top up
- ~~MHM har en RGB knap liggende som sandsynligvis godt kan bruges~~
- ~~knappen styres med tre pwm signaler, der skal derfor laves noget elektronik til udvidelse af eksisterende pwm udgange på processor.~~

### Cherry knap
dyrere løsning 
### LED Driver
 Konstant strøms LED driver med SPI interface - https://www.nxp.com/part/PCA9957HN#/
top-up
# links til inspiration
- DIY keyboard med arduino leonardo  - https://www.youtube.com/watch?v=yTc2GLXfCOY
- DIY keyboard fedevel kursus - https://www.youtube.com/watch?v=rMoTqSC9wrY

## References
**RP2040 Datasheet** - https://pip-assets.raspberrypi.com/categories/814-rp2040/documents/RP-008371-DS-1-rp2040-datasheet.pdf?disposition=inline
**TPS561246DRLR Datasheet** - https://www.ti.com/lit/ds/symlink/tps561243.pdf?ts=1770406662679

