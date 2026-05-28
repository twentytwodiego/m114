# auftrag2

### aufgabe 1

| Dezimal | Binär |
|---------|-------|
| 1       | 0001  |
| 2       | 0010  |
| 3       | 0011  |
| 4       | 0100  |
| 5       | 0101  |
| 6       | 0110  |
| 7       | 0111  |
| 8       | 1000  |
| 9       | 1001  |
| 10      | 1010  |
| 11      | 1011  |
| 12      | 1100  |
| 13      | 1101  |
| 14      | 1110  |
| 15      | 1111  |


### aufgabe 2

meine ssd hat 949.9GiB

| Einheit | Wert            |
|---------|-----------------|
| GiB     | 949.9           |
| GB      | 1,019.89        |
| MiB     | 972,697.6       |
| MB      | 1,019,892.22    |
| KiB     | 996,202,086.4   |
| KB      | 1,019,892,224   |
| TiB     | 0.9276          |
| TB      | 1.0199          |

### aufgabe 3
??wha

### aufgabe 4
[trainingsrechner](binaer_dezimal_trainer.html)

### aufgabe 5

## A1

### 1
| BIN(MSB) | BIN | BIN | BIN(LSB) | DEC | HEX |
|----------|-----|-----|----------|-----|-----|
| 0        | 0   | 0   | 0        | 0   | 0   |
| 0        | 0   | 0   | 1        | 1   | 1   |
| 0        | 0   | 1   | 0        | 2   | 2   |
| 0        | 0   | 1   | 1        | 3   | 3   |
| 0        | 1   | 0   | 0        | 4   | 4   |
| 0        | 1   | 0   | 1        | 5   | 5   |
| 0        | 1   | 1   | 0        | 6   | 6   |
| 0        | 1   | 1   | 1        | 7   | 7   |
| 1        | 0   | 0   | 0        | 8   | 8   |
| 1        | 0   | 0   | 1        | 9   | 9   |
| 1        | 0   | 1   | 0        | 10  | A   |
| 1        | 0   | 1   | 1        | 11  | B   |
| 1        | 1   | 0   | 0        | 12  | C   |
| 1        | 1   | 0   | 1        | 13  | D   |
| 1        | 1   | 1   | 0        | 14  | E   |
| 1        | 1   | 1   | 1        | 15  | F   |

### 2
1110001111

### 3
182

### 4
58021

### 5
Schritt 1

| Zahl   | BIN       | DEC |
|--------|-----------|-----|
| Zahl-A | 1101'1001 | 217 |
| Zahl-B | 0111'0101 | 117 |

Schritt 2

1 1 0 1 1 0 0 1   (Zahl-A = 217)
+ 0 1 1 1 0 1 0 1   (Zahl-B = 117)
─────────────────
1 0 1 0 0 1 1 1 0   (Resultat)

Schritt 3

| Resultat (9-bit) | BIN        | DEC | HEX |
|------------------|------------|-----|-----|
| Mit Carry        | 1'0100'1110| 334 | 14E |
| Nur 8-bit        | 0100'1110  |  78 | 4E  |


### 6
192.168.76.211
IP Adresse

192.168.x.x ist privater IP-Adressbereich

### 7
BE:83:85:D5:E4:FE
MAC Adresse
Adresse um das Gerät physisch zu erreichen

### 8

chmod 751 CreateWeeklyReport

chmod: CHange MODe - ändert Zugriffsrechte
751: 7 (Owner), 5 (Group), 1 (Others)

Owner: 111 (Lesen, schreiben, ausführen)
Group: 101 (Lesen, ausführen)
Others: 001 (ausführen)

### 9

1. 7 bits = 127
2. 16 bits = 65'536

### 10

    1 0 0 1 1 1 1 0     (R1 = 158)
  + 1 1 0 0 1 1 0 1     (R2 = 205)
  ─────────────────
  1 0 1 1 0 1 0 1 1     (= 363)

8-Bit overflow
9te Bit geht verloren = 01101011 = 107
ALU setz Carry und Overflow - Flag

### 11
32'768 Bit

### 12
speicherstellen = 2¹²= 4'096
pro adresse = 16 bit = 2 byte
4'096*2 = 8192Byte = 8 kiB 

Erste: 0000'0000'0000
Letzte: 1111'1111'1111

### 13
1 MHz = 1'000'000 Takte/s
1 Byte = 8 Bit
1'000'000 / 8 = 125'000 Byte/s

1 Takt = 1 Byte
1'000'000 Byte/s

### 14

a. unsigned
kleinste = 0000'0000
grösste = 1111'1111
0-255

b. signed
kleinste = 1000'0000
grösste = 0111'1111
-128 - +127

## Aufgabe 15

### Problem mit Ganzzahlen

Ganzzahl-Division: `1 ÷ 3 × 3 = 0` (falsch!)
→ Das Zwischenresultat `0.333...` wird als `0` gespeichert.

### Mein Vorschlag: Eigenes Floating-Point-Format

Angelehnt an den **IEEE 754 Standard** (wie echte CPUs es machen):

#### Aufbau (32-Bit Beispiel)

| Feld | Bits | Bedeutung |
|------|------|-----------|
| **S** (Vorzeichen) | 1 | 0 = positiv, 1 = negativ |
| **E** (Exponent) | 8 | Grösse der Zahl (Bias: +127) |
| **M** (Mantisse) | 23 | Die eigentlichen Ziffern |
| S | EEEEEEEE | MMMMMMMMMMMMMMMMMMMMMMM |
  1      8                 23


#### Formel

Wert = (-1)^S × 1.Mantisse × 2^(Exponent - 127)


#### Beispiel: die Zahl −6.5

1. Vorzeichen: negativ → `S = 1`
2. Binär: `6.5 = 110.1`
3. Normalisieren: `1.101 × 2²`
4. Exponent: `2 + 127 = 129 = 1000'0001`
5. Mantisse: `10100000000000000000000`

**Resultat:** `1 | 10000001 | 10100000000000000000000`

#### Warum funktioniert das?

- `1 ÷ 3` → wird als `0.3333...` in der Mantisse gespeichert (nicht abgehackt)
- `× 3` → ergibt korrekt `≈ 1.0`
- **Nachteil:** Kleine Rundungsfehler möglich, aber viel besser als Ganzzahlen


## Aufgabe 16

### Datenspeicherung

**10-Bit-Register** für Parkslot-Status (1 Bit pro Slot):

| Bit | 10 | 9 | 8 | 7 | 6 | 5 | 4 | 3 | 2 | 1 |
|-----|----|---|---|---|---|---|---|---|---|---|
| Wert | 0 | 1 | 0 | 0 | 1 | 0 | 1 | 0 | 1 | 0 |

`0` = frei (Lampe blinkt), `1` = belegt (Lampe aus)

### Ablauf: Fahrzeug einlagern

1. Kunde fährt auf Laderampe
2. Terminal zeigt freie Slots (blinkende Lampen)
3. Kunde drückt Zahl (z.B. `7`) → BCD-Kodierung → Steuerlogik
4. Steuerlogik prüft: Bit 7 == 0? (frei?)
   - **JA** → Lift fährt zu Slot 7, Fahrzeug einlagern, Bit 7 = 1
   - **NEIN** → Fehlersignal, andere Wahl verlangen

### Ablauf: Fahrzeug auslagern

1. Kunde drückt Slot-Nummer (z.B. `7`)
2. Steuerlogik prüft: Bit 7 == 1? (belegt?)
   - **JA** → Lift holt Fahrzeug, deponiert es an Ausgabestelle, Bit 7 = 0
   - **NEIN** → Fehlersignal (Slot leer)

### BCD-Eingabe (vom Bild)

- Kunde tippt `1`–`9` oder `10` am Terminal
- BCD kodiert die Zahl in 4-Bit-Gruppen: z.B. `7` → `0111`
- Steuerlogik dekodiert BCD → Slot-Nummer → Bit im Register ansprechen

### Sicherheit

- Doppelbelegung verhindert: Slot nur wählbar wenn Bit = 0
- Notaus: Alle Bewegungen stoppen, aktueller Zustand im Register erhalten
