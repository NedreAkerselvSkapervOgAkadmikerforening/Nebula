# Nebula
## Introduksjon
Nebula er foreningen NASAs neste generasjons flydatamaskin til bruk i foreningens modellrakketter.

## 🎯 Mål
1. Nebula skal være rask, kompakt, pålitelig, effektiv og enkel i bruk.
2. Nebula skal være bygd modulært, så nye sensorer og systemer kan innbyttes.
3. Sensorene i Nebula skal være nøyaktige og pålitelige.

## 💽 Oppbygning
Nebula kan overordnet deles i to kategorier:
1. Hovedkort
2. Modulene

### 🏠 Hovedkortet
Hovedkortet er hjernen og master i hele flydatamaskinen. Kortet bruker primært SPI-protokoll til å kommunisere med modulene.

Systemet drives av et enkelt 3.7 V LiPo-batteri, med 3.3 V logikk for alle moduler.

**Sensorer:**
- BMP390 - Trykk- og temperatursensor
- BNO085 - Akselerometer, gyroskop og magnetometer
- ADXL377 - High G akselerometer (+-200g)

**Datalogging:**
- MEM2067-02-180-00-A - Hengslet SD kort modul ([lenke](https://no.mouser.com/ProductDetail/GCT/MEM2067-02-180-00-A?qs=KUoIvG%2F9IlYTw%2Fcc1GlNJA%3D%3D&srsltid=AfmBOooPYGt0VKhHioGUMaVG0J4CpHVvJOKDjSTnPHolRedy0QrVqX5W))

**Telemetri:**
- SX1262 - LoRa transceiver for trådløs kommunikasjon med bakken

**Kommunikasjon:**
- USB-C (alternativt micro USB) – for kommunikasjon med PC og programmering

**Strømforsyning:**
- Voltage divider - For å måle spenningen på batteriet gjennom ADC på mikrokontrolleren
- TPS63020 - 3.3V spenningsregulator (VURDER)
- JST 2-pin - For å koble til batteriet
- Power switch - For å slå av og på hele systemet

**Debugging:**
- Power LED - For å indikere at systemet er på
- Status LED - For å indikere systemstatus (f.eks. feil, normal drift, etc.)

### 📨 SPI
Hovedkortet fungerer som master, modulene som slaves. Hver modul har egen CS‑pin, som kan velges ved å lodde over riktig solder pad (CS1–CS6).

Mikrokontrolleren har totalt fire SPI-busser. 2 reserveres til selve hovedkortet, og 2 til modulene.

### 🖇️ Konnektorer
I alle moduler skal det være en 20 pin konnektor som kobler modulen til hovedkortet. Denne skal ha følgende pinout:
- CS: 6 stk
- MISO: 2 stk
- MOSI: 2 stk
- SCK: 2 stk
- 3vO: 1 stk
- GND: 1 stk
- GPIO: 6 stk
