Speicherung von Gleitommazahlen

# Speicherung von Gleitommazahlen


| Typ | Gesamtgröße | Mantisse | Exponent | Bias |
| --- | ----------- | -------- | -------- | ---- |
| single | 32 bit | 23 bit | 8 bit | 127 |
| double | 64 bit | 52 bit | 11 bit | 1023 |

Aufbau der Gleitkommazahl vom Typ single:

SEEEEEEE EMMMMMMM MMMMMMMM MMMMMMMM

S = Vorzeichen
E = Exponent
M = Mantisse

## Darstellbare Werte

| Exponent | Mantisse | Bedeutung |
| -------- | -------- | --------- |
| 111 ... 111 | 000 ... 000 | +/- unendlich |
| 111 ... 111 | != 000 ... 000 | Keine Zahl (Not a Number=NaN) |
| 000 ... 000 | 000 ... 000 | +/- 0 |
| 000 ... 000 | != 000 ... 000 | Denormalisierte Zahl |
| 000 ... 001 bis 111 ... 110 | beliebig | Normalisierte Zahl |

### Unendlich:
Zahlen, die zu klein oder groß zum Darstellen sind. 1,0:0,0 ist ebenfalls unendlich

### NaN:
Ungültige Zahl, z.B. bei Quadratwurzel aus negativer Zahl.

### Denormalisierte Zahl:
Wenn eine Zahl zu klein ist, um mit Exponent gespeichert zu werden, wird die Gleitkommazahl nicht mehr mit +/- 1,Mantisse\*2^Exponent gespeichert, sondern mit +/- 0,Mantisse\*2^-128 bei typ Single bzw. 2^-32768 beim Typ Double. Es wird also der kleinstmögliche Exponent genommen.

### Normalisierte Zahl:
Normale Darstellung mit +/- 1,Mantisse\*2^Exponent

Der Zahlenbereich liegt bei:

- single: +/- 1,18\*10^-38 ... +/- 3,40\*10^+38
- double: +/- 2,23\*10^-308 ... +/- 1,80\*10^+308

## Umwandlung

166,125 -> 2er

| 128 | 64 | 32 | 16 | 8 | 4 | 2 | 1 | 1/2 | 1/4 | 1/8 |
| - | - | - | - | - | - | - | - | - | - | - |
| 1 | 0 | 1 | 0 | 0 | 1 | 1 | 0 | 0 | 0 | 1 |

### Nachkommastellen
0,125:

0,125\*2 = 0,**25**
0,**25**\*2 = 0,**5**
0,**5**\*2 = 1,**0**
0,**0**\*2 = 0,0
...
0,125 -> 0,001

0,3:

0,**3**\*2 = 0,**6**
0,**6**\*2 = 1,**2**
0,**2**\*2 = 0,**4**
0,**4**\*2 = 0,**8**
0,**8**\*2 = 1,**6**
0,**6**\*2 = 1,**2**
...
0,3 -> 0,0 1001 1001 1001...


1. 166,125 (10er) = 1010 0110,001 (2er)
2. Komma verschieben: 1010 0110,001 = 1, 0100 1100 01\*2⁷
3. Exponent: 7 + Bias = 7 + 127 = 134 = 1000 0110 (2er)

Ergebnis:
| 0 | 1000 0110 | 0100 1100 0100 0000 0000 000 |