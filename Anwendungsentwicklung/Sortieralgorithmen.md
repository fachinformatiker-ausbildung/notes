Sortieralgorithmen

# Sortieralgorithmen

## Index der Kleinsten Zahl innerhalb eines Bereichs vom Offset

```
public static int bestimmeIndexKleinsterZahl(int[] array, int offset) {
    int vorherigeZahl = array[offset];
    int indexBisherKleinsteZahl = 0;
    int bisherKleinsteZahl = array[offset];
    for (int i = offset+1; i < array.length; i++) {
        if (array[i] < vorherigeZahl && array[i] < bisherKleinsteZahl) {
            indexBisherKleinsteZahl = i;
            bisherKleinsteZahl = array[i];
        }
        vorherigeZahl = array[i];
    }
    return indexBisherKleinsteZahl;
}
```

## Selectionsort

Der Selectionsort beginnt am Anfang eines Arrays. Dann wird das kleinste Element im Rest des Arrays gesucht und mit der aktuellen Zeigerposition vertauscht.

Aktuelle Position i = 0

5 7 9 2 4 3 6 1 8

**5** 7 9 2 4 3 6 **1** 8 -> 5 mit 1 tauschen, i = 1

1 **7** 9 **2** 4 3 6 5 8 -> 7 und 2 tauschen, i = 2

1 2 **9** 7 4 **3** 6 5 8 -> 9 und 3 tauschen, i = 3

...

### Beispiel:

```
public static void selectionSort(int[] array) {
    for (int i = 0; i < array.length-1; i++) {
        int indexKleinsteZahl = bestimmeIndexKleinsterZahl(array, i);
        if (indexKleinsteZahl > i) {
            int tmp = array[i];
            array[i] = array[indexKleinsteZahl];
            array[indexKleinsteZahl] = tmp;
        }
    }
}
```

## Insertionsort

Der Insertionsort iteriert alle Stellen einer Liste. Dabei wird von der aktuellen Zeigerposition (ab 1) mit jedem Vorgänger vertauscht und die Zeigerposition bis zum Anfang (0) zurückgesetzt, so lange der Vorgänger größer ist als der Wert der aktuellen Stelle. Dort wird dann der aktuelle Wert eingefügt.

### Beispiel:

```
public static void insertionSort(int[] array) {
    for (int i = 1; i < array.length; i++) {
        int num = array[i];
        for (int k = i; k >= 0; k -= 1) {
            if (k > 0) {
                // Setze Zahl an aktueller
                // Rückwärtsposition auf den Wert des
                // Vorgängers, da Später num eingefügt wird
                if (num < array[k-1]) {
                    array[k] = array[k - 1];
                    // fortsetzen
                    continue;
                }
                // Setze Wert auf num, da hier eingefügt wird
                array[k] = num;
                break;
            }
            // nötig, da auch das Ende der Liste erreicht sein könnte
            // und dann nicht weiter rückwärts iteriert wird
            else {
                array[k] = num;
                break;
            }
        }
    }
}
```

## Shellsort

### Beispiel:

```
public static void shellSort(int[] array, int startwidth) {
    while(startwidth > 0) {
        for (int offset = 0; offset < startwidth; offset++) {
            preSort(array, startwidth, offset);
        }
        startwidth /= 2;
    }
}

public static void preSort(int[] array, int width, int offset) {
    for (int i = width + offset; i < array.length; i += width) {
        int num = array[i];
        int pos = i;
        while (pos >= 0) {
            if (pos > 0 && (pos - width) >= 0) {
                if (num < array[pos-width]) {
                    array[pos] = array[pos-width];
                    pos -= width;
                    continue;
                }
                array[pos] = num;
                break;
            }
            else {
                array[pos] = num;
                break;
            }
        }
    }
}
```

## Mergesort