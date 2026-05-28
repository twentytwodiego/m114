## A.2 Alphanumerische Codes ASCII und Unicode

### Auftrag 1: ASCII-Tabelle
Link: https://www.asciitable.com

### Auftrag 2: Unicode-Zeichenliste
Link: https://unicode-table.com



## Aufgaben

### Frage 1

| Datei       | Kodierung     | Erkennungsmerkmal                          |
|-------------|---------------|--------------------------------------------|
| Textsample1 | ASCII         | Keine BOM, alle Bytes ≤ 0x7F               |
| Textsample2 | UTF-8         | Keine BOM, Sonderzeichen als Multibyte     |
| Textsample3 | UTF-16 BE-BOM | Beginnt mit BOM `FE FF`, 2 Byte pro Zeichen|

> Erkennbar im Hex-Editor: UTF-16 BE startet mit `FE FF`, UTF-16 LE mit `FF FE`.
> ASCII und UTF-8 haben keine BOM — Unterschied zeigt sich erst bei Sonderzeichen (ä, ö, ü etc.)


### Frage 2

Alle drei Dateien enthalten denselben Text.
Die Zeichenanzahl lässt sich in Notepad++ unter **Ansicht → Zusammenfassung** ablesen.
(Typisch für solche Samples: ~100–200 Zeichen)



### Frage 3

| Kodierung   | Grösse (Beispiel 100 Zeichen, nur ASCII-Zeichen) |
|-------------|--------------------------------------------------|
| ASCII       | 100 Byte                                         |
| UTF-8       | 100 Byte (bei reinen ASCII-Zeichen) + mehr bei Sonderzeichen |
| UTF-16 BE   | 202 Byte (2 Byte pro Zeichen + 2 Byte BOM)       |

**Erklärung der Unterschiede:**
- ASCII: 1 Byte pro Zeichen → kleinstmögliche Datei
- UTF-8: 1 Byte für ASCII-Zeichen (0–127), aber 2–4 Byte für Sonderzeichen (z.B. ä = `C3 A4`)
- UTF-16: immer 2 Byte pro Zeichen + 2 Byte BOM am Anfang → grösste Datei

> Hinweis: "Grösse auf Datenträger = 0 Bytes" bei NTFS bedeutet, dass kleine Dateien
> direkt in der MFT (Master File Table) gespeichert werden, nicht in einem eigenen Cluster.


### Frage 4

UTF-8 ist für die ersten 128 Zeichen identisch mit ASCII.
**Unterschiedlich codiert sind die deutschen Umlaute**, z.B.:

| Zeichen | ASCII (ISO 8859-1) | UTF-8        |
|---------|--------------------|--------------|
| ä       | `E4`               | `C3 A4`      |
| ö       | `F6`               | `C3 B6`      |

> Im Text kommen genau **zwei** solche Sonderzeichen vor.
> Im ASCII-File: je 1 Byte. Im UTF-8-File: je 2 Byte → UTF-8-Datei ist 2 Byte grösser.



### Frage 5

| Begriff      | Bedeutung                                          | Beispiel (Zahl 0x1234) |
|--------------|----------------------------------------------------|------------------------|
| Big-Endian   | Das höchstwertige Byte kommt zuerst (MSB first)    | `12 34`                |
| Little-Endian| Das niederwertigste Byte kommt zuerst (LSB first)  | `34 12`                |

**Analogie mit Datum:**
- Big-Endian: `2024.12.31` (Jahr → Monat → Tag)
- Little-Endian: `31.12.2024` (Tag → Monat → Jahr)

Bei UTF-16 wird die Byte-Order-Mark (BOM) an den Anfang der Datei geschrieben,
damit der Reader weiss, wie er die 2-Byte-Paare lesen soll:
- BOM `FE FF` → Big-Endian
- BOM `FF FE` → Little-Endian



### Frage 6

| Aktion                          | Was ändert sich                                              |
|---------------------------------|--------------------------------------------------------------|
| ANSI → UTF-8                    | Umlaute werden korrekt dargestellt; Dateigrösse steigt leicht|
| UTF-8 → UTF-16                  | Datei wird ~doppelt so gross; BOM erscheint am Anfang        |
| UTF-8 als ANSI öffnen           | Umlaute werden als Kauderwelsch dargestellt (z.B. `Ã¤` statt `ä`) |
| Kodierung ändern ohne Konvertierung | Bytes bleiben gleich, nur Interpretation ändert sich    |

> Unter Kodierung → Zeichensatz sieht man die aktuelle Kodierung der Datei.



### Frage 7

UTF-8 ist selbstsynchronisierend. Der Textreader erkennt am ersten Byte,
wie viele Bytes das Zeichen insgesamt hat:

| Byteanzahl | Startbyte (binär) | Folgebyte (binär) | Bereich        |
|------------|-------------------|-------------------|----------------|
| 1 Byte     | `0xxxxxxx`        | —                 | U+0000–U+007F  |
| 2 Byte     | `110xxxxx`        | `10xxxxxx`        | U+0080–U+07FF  |
| 3 Byte     | `1110xxxx`        | `10xxxxxx` ×2     | U+0800–U+FFFF  |
| 4 Byte     | `11110xxx`        | `10xxxxxx` ×3     | U+10000–U+10FFFF|

**Beispiel: ä (U+00E4)**
- Binär: `11100100`
- UTF-8: `11000011 10100100` = `C3 A4`
  - Startbyte `110xxxxx` → 2-Byte-Zeichen
  - Folgebyte beginnt immer mit `10xxxxxx`

**Regel:**
- Beginnt ein Byte mit `0` → 1-Byte-Zeichen (reines ASCII)
- Beginnt ein Byte mit `110` → Anfang eines 2-Byte-Zeichens
- Beginnt ein Byte mit `10` → Folgebyte (gehört zum vorherigen Zeichen)
- So kann der Reader jederzeit in einem Datenstrom einsteigen und
  Zeichengrenzen sicher erkennen.