# Kapitel 6: Arrays in Java - Theorie

## 🎯 Lernziele
Nach diesem Kapitel kannst du:
- Arrays deklarieren, erstellen und initialisieren
- Auf Array-Elemente zugreifen und sie ändern
- Arrays mit Schleifen durchlaufen
- Mehrdimensionale Arrays verwenden
- Häufige Array-Operationen implementieren
- Arrays als Parameter und Rückgabewerte nutzen

## 📚 Was sind Arrays?

Ein **Array** ist wie ein **Schrank mit nummerierten Fächern** - jedes Fach kann einen Wert speichern, und du findest jeden Wert über seine **Nummer (Index)**.

```java
// Statt vieler einzelner Variablen:
int note1 = 85;
int note2 = 92;
int note3 = 78;
int note4 = 89;
int note5 = 94;

// Ein Array für alle Noten:
int[] noten = {85, 92, 78, 89, 94};
```

**Vorteile von Arrays:**
- ✅ Viele Werte gleichen Typs speichern
- ✅ Über Index schnell zugreifen
- ✅ Perfekt für Schleifen
- ✅ Organisierte Datenhaltung

## 📦 1. Array-Grundlagen

### 1.1 Array deklarieren und erstellen
```java
// Variante 1: Deklaration + Erstellung + Initialisierung
int[] zahlen = {1, 2, 3, 4, 5};

// Variante 2: Erst deklarieren, dann erstellen
int[] zahlen;
zahlen = new int[5];  // Array für 5 int-Werte

// Variante 3: Alles in einem
int[] zahlen = new int[5];

// Variante 4: Deklaration mit Initialisierung
int[] zahlen = new int[]{1, 2, 3, 4, 5};
```

### 1.2 Array-Syntax im Detail
```java
datentyp[] arrayName = new datentyp[größe];

// Beispiele:
int[] ganzZahlen = new int[10];        // 10 int-Werte
double[] kommaZahlen = new double[5];  // 5 double-Werte
String[] namen = new String[3];        // 3 String-Referenzen
boolean[] flags = new boolean[8];      // 8 boolean-Werte
```

### 1.3 Index verstehen
```java
int[] noten = {85, 92, 78, 89, 94};

// Index:     0   1   2   3   4
// Werte:    85  92  78  89  94

System.out.println(noten[0]);  // 85 (erstes Element)
System.out.println(noten[1]);  // 92 (zweites Element)
System.out.println(noten[4]);  // 94 (letztes Element)

// WICHTIG: Index startet bei 0!
// Letzter Index = array.length - 1
```

## 🔍 2. Auf Array-Elemente zugreifen

### 2.1 Lesen und Schreiben
```java
int[] punkte = new int[5];

// Werte setzen
punkte[0] = 100;
punkte[1] = 85;
punkte[2] = 92;
punkte[3] = 78;
punkte[4] = 89;

// Werte lesen
int erstePunktzahl = punkte[0];
int letztePunktzahl = punkte[4];

// Werte ändern
punkte[2] = 95;  // 92 → 95

System.out.println("Erste Punktzahl: " + erstePunktzahl);
System.out.println("Neue dritte Punktzahl: " + punkte[2]);
```

### 2.2 Array-Länge ermitteln
```java
int[] zahlen = {1, 2, 3, 4, 5, 6, 7};

int länge = zahlen.length;  // 7 (Anzahl Elemente)
int letzterIndex = zahlen.length - 1;  // 6

System.out.println("Array hat " + länge + " Elemente");
System.out.println("Letztes Element: " + zahlen[letzterIndex]);
```

## 🔄 3. Arrays und Schleifen

### 3.1 Mit for-Schleife durchlaufen
```java
String[] fächer = {"Mathematik", "Deutsch", "Englisch", "Informatik", "Sport"};

// Alle Elemente ausgeben
for (int i = 0; i < fächer.length; i++) {
    System.out.println("Fach " + (i + 1) + ": " + fächer[i]);
}

// Rückwärts durchlaufen
for (int i = fächer.length - 1; i >= 0; i--) {
    System.out.println(fächer[i]);
}
```

### 3.2 Enhanced for-Schleife (for-each)
```java
String[] namen = {"Max", "Anna", "Tom", "Lisa"};

// Elegant und sicher
for (String name : namen) {
    System.out.println("Hallo " + name + "!");
}

// Vorteil: Kein Index-Fehler möglich!
```

### 3.3 Wann welche Schleife?
```java
int[] noten = {85, 92, 78, 89, 94};

// For-each: Nur lesen
for (int note : noten) {
    System.out.println("Note: " + note);
}

// Klassische for: Lesen + Schreiben + Index benötigt
for (int i = 0; i < noten.length; i++) {
    System.out.println("Note " + (i + 1) + ": " + noten[i]);
    noten[i] += 5;  // Alle Noten um 5 verbessern
}
```

## 🎲 4. Array-Initialisierung

### 4.1 Verschiedene Initialisierungsarten
```java
// Mit konkreten Werten
int[] zahlen = {1, 2, 3, 4, 5};
String[] wochentage = {"Mo", "Di", "Mi", "Do", "Fr", "Sa", "So"};

// Mit Standardwerten (new)
int[] punkte = new int[10];     // Alle Werte = 0
boolean[] flags = new boolean[5]; // Alle Werte = false
String[] namen = new String[3];  // Alle Werte = null

// Mit berechneten Werten
int[] quadrate = new int[10];
for (int i = 0; i < quadrate.length; i++) {
    quadrate[i] = i * i;  // 0, 1, 4, 9, 16, 25, ...
}
```

### 4.2 Standard-Werte bei Initialisierung
```java
// Numerische Typen → 0
int[] ints = new int[3];        // {0, 0, 0}
double[] doubles = new double[3]; // {0.0, 0.0, 0.0}

// Boolean → false
boolean[] bools = new boolean[3]; // {false, false, false}

// Objekt-Referenzen → null
String[] strings = new String[3]; // {null, null, null}
```

## 📊 5. Häufige Array-Operationen

### 5.1 Summe und Durchschnitt
```java
int[] noten = {85, 92, 78, 89, 94, 87, 91};

// Summe berechnen
int summe = 0;
for (int note : noten) {
    summe += note;
}

// Durchschnitt berechnen
double durchschnitt = (double) summe / noten.length;

System.out.println("Summe: " + summe);
System.out.println("Durchschnitt: " + String.format("%.1f", durchschnitt));
```

### 5.2 Minimum und Maximum finden
```java
int[] zahlen = {45, 23, 89, 12, 67, 34, 91};

// Minimum finden
int min = zahlen[0];
for (int i = 1; i < zahlen.length; i++) {
    if (zahlen[i] < min) {
        min = zahlen[i];
    }
}

// Maximum finden  
int max = zahlen[0];
for (int zahl : zahlen) {
    if (zahl > max) {
        max = zahl;
    }
}

System.out.println("Minimum: " + min);
System.out.println("Maximum: " + max);
```

### 5.3 Element suchen
```java
String[] namen = {"Max", "Anna", "Tom", "Lisa", "Ben"};
String gesucht = "Tom";

// Linear Search
int position = -1;
for (int i = 0; i < namen.length; i++) {
    if (namen[i].equals(gesucht)) {
        position = i;
        break;  // Gefunden, kann aufhören
    }
}

if (position != -1) {
    System.out.println(gesucht + " gefunden an Position " + position);
} else {
    System.out.println(gesucht + " nicht gefunden");
}

// Elegant mit enhanced for + eigene Variable
boolean gefunden = false;
for (String name : namen) {
    if (name.equals(gesucht)) {
        gefunden = true;
        break;
    }
}
```

### 5.4 Array kopieren
```java
int[] original = {1, 2, 3, 4, 5};

// Flache Kopie (neue Referenz auf gleiche Daten)
int[] referenz = original;
referenz[0] = 99;  // Ändert auch original[0]!

// Echte Kopie erstellen
int[] kopie = new int[original.length];
for (int i = 0; i < original.length; i++) {
    kopie[i] = original[i];
}

// Oder mit System.arraycopy()
int[] kopie2 = new int[original.length];
System.arraycopy(original, 0, kopie2, 0, original.length);

// Oder mit Arrays.copyOf() (import java.util.Arrays)
int[] kopie3 = Arrays.copyOf(original, original.length);
```

## 📐 6. Mehrdimensionale Arrays

### 6.1 2D-Arrays (Matrix)
```java
// 2D-Array erstellen
int[][] matrix = new int[3][4];  // 3 Zeilen, 4 Spalten

// Mit Werten initialisieren
int[][] noten = {
    {85, 92, 78, 89},  // Schüler 1
    {91, 87, 82, 95},  // Schüler 2
    {79, 88, 93, 86}   // Schüler 3
};

// Zugriff auf Elemente
int note = noten[1][2];  // Schüler 2, Fach 3 → 82
noten[0][1] = 94;        // Schüler 1, Fach 2 → 94

System.out.println("Note von Schüler 2 in Fach 3: " + note);
```

### 6.2 2D-Arrays durchlaufen
```java
int[][] matrix = {
    {1, 2, 3, 4},
    {5, 6, 7, 8},
    {9, 10, 11, 12}
};

// Verschachtelte for-Schleifen
for (int zeile = 0; zeile < matrix.length; zeile++) {
    for (int spalte = 0; spalte < matrix[zeile].length; spalte++) {
        System.out.print(matrix[zeile][spalte] + "\t");
    }
    System.out.println();  // Neue Zeile
}

// Enhanced for-Schleifen
for (int[] zeile : matrix) {
    for (int wert : zeile) {
        System.out.print(wert + "\t");
    }
    System.out.println();
}
```

### 6.3 Praktisches Beispiel: Notentabelle
```java
// Notentabelle: [Schüler][Fach]
double[][] noten = {
    {2.1, 1.8, 2.3, 1.9},  // Max
    {1.7, 2.0, 1.5, 2.2},  // Anna
    {2.8, 3.1, 2.5, 2.9}   // Tom
};

String[] schüler = {"Max", "Anna", "Tom"};
String[] fächer = {"Mathe", "Deutsch", "Englisch", "Info"};

// Durchschnitt pro Schüler
for (int s = 0; s < schüler.length; s++) {
    double summe = 0;
    for (int f = 0; f < fächer.length; f++) {
        summe += noten[s][f];
    }
    double durchschnitt = summe / fächer.length;
    System.out.printf("%s: Durchschnitt %.2f%n", schüler[s], durchschnitt);
}
```

## 🛠️ 7. Arrays als Parameter und Rückgabewerte

### 7.1 Array als Parameter
```java
public static void gibArrayAus(int[] array) {
    for (int wert : array) {
        System.out.print(wert + " ");
    }
    System.out.println();
}

public static double berechneeDurchschnitt(double[] noten) {
    double summe = 0;
    for (double note : noten) {
        summe += note;
    }
    return summe / noten.length;
}

// Verwendung
int[] zahlen = {1, 2, 3, 4, 5};
double[] schulnoten = {2.1, 1.8, 2.5, 1.9};

gibArrayAus(zahlen);
double durchschnitt = berechneeDurchschnitt(schulnoten);
```

### 7.2 Array als Rückgabewert
```java
public static int[] erstelleZufallsZahlen(int anzahl) {
    int[] zahlen = new int[anzahl];
    for (int i = 0; i < anzahl; i++) {
        zahlen[i] = (int) (Math.random() * 100) + 1;  // 1-100
    }
    return zahlen;
}

public static String[] filtereNamen(String[] alle, int minLänge) {
    // Erst zählen, wie viele passen
    int anzahl = 0;
    for (String name : alle) {
        if (name.length() >= minLänge) {
            anzahl++;
        }
    }
    
    // Array in passender Größe erstellen
    String[] gefiltert = new String[anzahl];
    int index = 0;
    for (String name : alle) {
        if (name.length() >= minLänge) {
            gefiltert[index++] = name;
        }
    }
    
    return gefiltert;
}
```

## ⚠️ 8. Häufige Fehler

### 1. Index-Fehler (ArrayIndexOutOfBoundsException)
```java
int[] zahlen = {1, 2, 3};

// FALSCH:
System.out.println(zahlen[3]);  // Fehler! Index 3 existiert nicht

// RICHTIG:
if (index >= 0 && index < zahlen.length) {
    System.out.println(zahlen[index]);
}
```

### 2. Null-Pointer-Exception
```java
String[] namen = new String[3];  // Alle Werte sind null

// FALSCH:
for (String name : namen) {
    System.out.println(name.length());  // null.length() → Fehler!
}

// RICHTIG:
for (String name : namen) {
    if (name != null) {
        System.out.println(name.length());
    }
}
```

### 3. Array-Größe zur Laufzeit ändern
```java
int[] zahlen = {1, 2, 3};

// UNMÖGLICH: Array-Größe ist fix!
// zahlen.length = 5;  // Kompilerfehler!

// LÖSUNG: Neues Array erstellen
int[] neuZahlen = new int[5];
System.arraycopy(zahlen, 0, neuZahlen, 0, zahlen.length);
zahlen = neuZahlen;
```

### 4. Referenz vs. Wert-Kopie
```java
int[] original = {1, 2, 3};
int[] kopie = original;  // ACHTUNG: Nur Referenz kopiert!

kopie[0] = 99;
System.out.println(original[0]);  // 99! Original wurde geändert

// RICHTIG: Echte Kopie
int[] echtekopie = Arrays.copyOf(original, original.length);
```

## 🎮 9. Übungsaufgaben

### Aufgabe 1: Grundlagen
- Erstelle ein Array mit 10 Zufallszahlen (1-100)
- Finde die größte und kleinste Zahl
- Berechne Summe und Durchschnitt

### Aufgabe 2: Suchen und Sortieren
- Implementiere eine Suche nach einem bestimmten Wert
- Zähle, wie oft ein Wert vorkommt
- Sortiere ein Array aufsteigend (Bubble Sort)

### Aufgabe 3: Text-Arrays
- Erstelle ein Array mit Namen deiner Klasse
- Finde alle Namen, die mit einem bestimmten Buchstaben beginnen
- Sortiere die Namen alphabetisch

### Aufgabe 4: 2D-Arrays
- Erstelle eine 4x4 Multiplikationstabelle
- Implementiere ein einfaches Tic-Tac-Toe-Spielfeld
- Berechne Zeilen- und Spaltensummen einer Matrix

### Aufgabe 5: Fortgeschritten
- Implementiere ein einfaches Adressbuch (Namen + Telefonnummern)
- Erstelle einen Notenrechner für mehrere Schüler und Fächer
- Programmiere ein einfaches Sudoku-Spielfeld (9x9)

## 🏆 Zusammenfassung

**Array-Grundlagen:**
- Container für mehrere Werte gleichen Typs
- Index startet bei 0, letzter Index = length - 1
- Größe ist nach Erstellung fix

**Zugriff:**
- `array[index]` für Lesen/Schreiben
- `array.length` für Anzahl Elemente

**Durchlaufen:**
- Klassische for-Schleife: wenn Index benötigt
- Enhanced for (for-each): nur zum Lesen

**Mehrdimensional:**
- `int[][] matrix = new int[zeilen][spalten]`
- Verschachtelte Schleifen zum Durchlaufen

**Best Practices:**
- Index-Grenzen prüfen
- Null-Checks bei Objekt-Arrays
- Arrays als Parameter/Rückgabewerte nutzen
- Sinnvolle Variablennamen wählen

---

## 🚀 Weiter geht's!

Im nächsten Kapitel lernst du **Methoden** - wie du deinen Code organisierst und wiederverwendbar machst!
