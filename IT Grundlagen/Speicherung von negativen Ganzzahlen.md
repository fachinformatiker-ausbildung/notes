Speicherung von negativen Ganzzahlen

# Speicherung von negativen Ganzzahlen

-98 (10er) -> 8 bit Negative Binärziffer

98 -> | 0 | 1 | 1 | 0 | 0 | 0 | 1 | 0 |

## Rechnung

&nbsp;&nbsp;&nbsp;0 1 1 0 0 0 1 0 (98)
\______________________________

&nbsp;&nbsp;&nbsp;1 0 0 1 1 1 0 1 (98 invertiert)

\+&nbsp;0 0 0 0 0 0 0 1
\______________________________
=&nbsp;1 0 0 1 1 1 1 0

-98 (10er) -> 1001 1110 (2er mit Vorzeichen=signed)

Die Zahlen werden in 8 bit gespeichert: 8 bit = 1 byte = 256 Kombinationsmöglichkeiten. Bei Vorzeichenbehafteten Zahlen lässt sich sm 8. bit erkennen, wenn eine Zahl negativ ist: Ist das 8. bit 1, ist die Zahl negativ. Um eine negative Zahl zu speichern, wird das positive Äquivalent invertiert und mit 1 (10er) = 0000 0001 (2er) addiert. Dieses Verfahren nennt man 2er Komplement. Um die Zahl zurück zu erhalten, wird bei einer negativen Binärzahl (8. Bit ist 1) wieder invertiert und mit 1 addiert.