# Bildcodierung – Lösungen

## Aufgabe 1: Pixel, Auflösung & Bildgrösse

Pixel: Kleinste Einheit eines digitalen Bildes. Jedes Bild ist ein Raster aus Pixeln mit je einem Farbwert.

Auflösung: Anzahl Pixel als Breite × Höhe (z.B. 1920 × 1080). Höhere Auflösung = mehr Detail.

Bildgrösse berechnen:
```
Grösse (Byte) = Breite × Höhe × Farbtiefe (Bit) / 8
```

Beispiel – Farbbild 1920 × 1080, 24 Bit (RGB):
```
1920 × 1080 × 24 / 8 = 6'220'800 Byte ≈ 5.9 MB
```

| Farbtiefe | Farben | Typ |
|-----------|--------|-----|
| 1 Bit | 2 | Schwarz/Weiss |
| 8 Bit | 256 | Graustufen |
| 24 Bit | 16.7 Mio. | RGB (True Color) |
| 32 Bit | 16.7 Mio. + Alpha | RGBA |

---

## Aufgabe 2: Bildformate

| Format | Komprimierung | Transparenz | Einsatz |
|--------|--------------|-------------|---------|
| **JPG** | Verlustbehaftet | Nein | Fotos |
| **PNG** | Verlustfrei | Ja | Logos, Screenshots |
| **GIF** | Verlustfrei (max. 256 Farben) | Ja (1 Bit) | Animationen |
| **BMP** | Keine | Nein | Windows-intern |

## Aufgabe 3

Die Grafiken wurden mit GIMP erstellt und je als [test.jpg](test.jpg), [test.png](test.png), [test.gif](test.gif) und [test.bmp](test.bmp) exportiert.
test.bmp`

## Aufgabe 4

### RGB Hex-Codes:
| Hex-Code | Farbe |
|----------|-------|
| #FF0000 | Rot |
| #00FF00 | Grün |
| #0000FF | Blau |
| #FFFF00 | Gelb |
| #00FFFF | Cyan |
| #FF00FF | Magenta |
| #000000 | Schwarz |
| #FFFFFF | Weiss |
| #00BC00 | Dunkelgrün |
### CMYK-Codes:
| CMYK | Farbe |
|------|-------|
| C:0% M:100% Y:100% K:0% | Rot |
| C:100% M:0% Y:100% K:0% | Grün |
| C:100% M:100% Y:0% K:0% | Blau |
| C:0% M:0% Y:100% K:0% | Gelb |
| C:100% M:0% Y:0% K:0% | Cyan |
| C:0% M:100% Y:0% K:0% | Magenta |
| C:100% M:100% Y:100% K:0% | Dunkles Grau/Schwarz |
| C:0% M:0% Y:0% K:100% | Schwarz |
| C:0% M:0% Y:0% K:0% | Weiss |
| C:0% M:46% Y:38% K:22% | Altrosa/Lachsfarben |

---

## A4.7 Aufgabe 1: Matterhorn-Bild

Gespeicherte Dateigrössen:
| Datei | Grösse |
|-------|--------|
| matterhorn.png | 627.6 KiB |
| matterhornhoch.jpg | 412.1 KiB |
| matterhorntief.jpg | 6.4 KiB |

Theoretischer unkomprimierter Speicherbedarf (1280×720, 24 Bit):
```
1280 × 720 × 24 / 8 = 2'764'800 Byte ≈ 2.64 MiB
```

Vergleich:
| Datei | Grösse | Anteil unkomprimiert |
|-------|--------|----------------------|
| Unkomprimiert (theoretisch) | 2.64 MiB | 100% |
| PNG | 627.6 KiB | ~23% |
| JPG hoch | 412.1 KiB | ~15% |
| JPG tief | 6.4 KiB | ~0.2% |

Erklärung: PNG ist verlustfrei komprimiert, daher grösser als JPG. JPG hoch hat kaum sichtbare Qualitätsverluste bei deutlich kleinerer Datei. JPG tief ist extrem klein, aber mit starken Kompressionsartefakten. Alle drei sind massiv kleiner als das unkomprimierte Original.

---

## A4.8 Aufgabenblock 2
Aufgabe 1 – Speicherbedarf HD720p50, True Color:
```
HD720p = 1280 × 720 Pixel, True Color = 24 Bit
1280 × 720 × 24 / 8 = 2'764'800 Byte ≈ 2.64 MiB pro Bild
```
Aufgabe 2 – Speicherbedarf Video 3 Minuten (50 Bilder/Sek.):
```
3 Min = 180 Sek × 50 Bilder = 9'000 Bilder
9'000 × 2'764'800 Byte = 24'883'200'000 Byte ≈ 23.2 GiB
```
Aufgabe 3 – RAW / TIF / JPG:
- RAW:** Rohdaten direkt vom Sensor, unkomprimiert, maximale Qualität, nur mit spezieller Software bearbeitbar. Einsatz: professionelle Fotografie.
- TIF: Verlustfreie Komprimierung, hohe Qualität, grosse Dateien. Einsatz: Druckvorstufe, Archivierung.
- JPG: Verlustbehaftete Komprimierung, kleine Dateien. Einsatz: Web, Alltagsfotos.

Aufgabe 4 – YouTube Vorgaben:
- Format: MP4 (empfohlen)
- Videocodec: H.264
- Audiocodec: AAC
- Bildrate: 24, 25, 30, 48, 50 oder 60 fps
- Farbauflösung: 8 Bit, YUV 4:2:0
- Rechtlich: Keine urheberrechtlich geschützte Musik/Bilder ohne Lizenz verwenden.

Aufgabe 5 – 30-Zoll-Display, 16:10, 100 ppi:
```
Diagonale: 30 Zoll
Verhältnis 16:10 → a² + b² = 30²
x = 30 / √(16² + 10²) = 30 / 18.87 = 1.59 Zoll pro Einheit
Horizontal: 16 × 1.59 × 100 = 2'540 Pixel
Vertikal:   10 × 1.59 × 100 = 1'588 Pixel
→ Auflösung: ca. 2540 × 1588 Pixel
```
Aufgabe 6 – Foto 2000×2000 px bei 600 dpi drucken:
```
1 Inch = 2.54 cm
2000 px / 600 dpi = 3.33 Inch
3.33 × 2.54 = 8.47 cm
→ Das Foto wird ca. 8.5 × 8.5 cm gross
```
Aufgabe 7 – Mikrofon vs. Lautsprecher / A/D-Wandler:
- Mikrofon: Wandelt Schallwellen (mechanische Schwingungen) in elektrische Signale um. Eine Membran schwingt mit dem Schall und erzeugt eine Spannung.
- Lautsprecher: Umgekehrtes Prinzip – elektrische Signale werden in mechanische Schwingungen (Schall) umgewandelt.
- A/D-Wandler: Tastet das analoge Signal in festen Zeitabständen ab (Abtastung) und weist jedem Messwert einen digitalen Zahlenwert zu (Quantisierung). So entsteht aus dem kontinuierlichen Signal eine Folge von 0 und 1.

Aufgabe 8 – GIF vs. PNG Logo:
- GIF: Nur 256 Farben, Transparenz nur 1-Bit (an/aus), kann animiert werden. Kanten wirken treppenartig.
- PNG: Millionen Farben, voller Alphakanal (weiche Transparenz), keine Animation. Schärfere, sauberere Kanten.
- Wahl: PNG, weil die Transparenz sauberer ist und mehr Farben unterstützt werden.