Makro tastatur til kontrol af lydeffekter under D&D kampagner.
# komponent kandidater
## Micro processor:
***ATMega32U4***
denne processor har rimelig hukommelse og indbygget USB 2.0, der er derfor ikke behov for ekstern USB til seriel konvertering.

der kan adderes flash til ved behov for at gemme opsætning for eksempel, eller hvis der bliver programmeret UI ind i enheden

- Datablad på ATMega32U4 - https://www.microchip.com/en-us/product/atmega32u4
## Knap
- MHM har en RGB knap liggende som sandsynligvis godt kan bruges
- knappen styres med tre pwm signaler, der skal derfor laves noget elektronik til udvidelse af eksisterende pwm udgange på processor.

# links til inspiration
- DIY keyboard med arduino leonardo  - https://www.youtube.com/watch?v=yTc2GLXfCOY
- DIY keyboard fedevel kursus - https://www.youtube.com/watch?v=rMoTqSC9wrY
# USB 2.0 interface
- max strøm træk på USB A port - 500 mA @ 5 V -> 2.5 W
