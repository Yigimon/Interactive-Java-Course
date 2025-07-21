# Kapitel 5: Schleifen in Java - Theorie

## 🎯 Lernziele
Nach diesem Kapitel kannst du:
- `for`-Schleifen für zählende Wiederholungen verwenden
- `while`-Schleifen für bedingte Wiederholungen nutzen
- `do-while`-Schleifen verstehen und anwenden
- Enhanced `for`-Schleifen (for-each) für Arrays/Collections verwenden
- Verschachtelte Schleifen erstellen
- `break` und `continue` für Schleifensteuerung nutzen

## 📚 Was sind Schleifen?

**Schleifen** lassen deinen Code **wiederholen**, ohne dass du ihn mehrfach schreiben musst. Stell dir vor, du müsstest 100 Mal "Hallo" ausgeben - ohne Schleifen wären das 100 Zeilen Code!

```java
// OHNE Schleife (schlecht):
System.out.println("Hallo 1");
System.out.println("Hallo 2");
System.out.println("Hallo 3");
// ... 97 weitere Zeilen

// MIT Schleife (gut):
for (int i = 1; i <= 100; i++) {
    System.out.println("Hallo " + i);
}
```

## 🔢 1. For-Schleife: Der Zähler

Die `for`-Schleife verwendest du, wenn du **genau weißt**, wie oft etwas wiederholt werden soll.

### 1.1 Grundsyntax
```java
for (Initialisierung; Bedingung; Iteration) {
    // Code, der wiederholt wird
}
```

### 1.2 Beispiel: Von 1 bis 10 zählen
```java
for (int i = 1; i <= 10; i++) {
    System.out.println("Zahl: " + i);
}
```

**Erklärung:**
- `int i = 1` - Startwert (wird einmal am Anfang ausgeführt)
- `i <= 10` - Bedingung (geprüft vor jeder Wiederholung)
- `i++` - Iteration (ausgeführt nach jeder Wiederholung)

### 1.3 Verschiedene For-Schleifen
```java
// Vorwärts zählen
for (int i = 0; i < 5; i++) {
    System.out.println(i);  // 0, 1, 2, 3, 4
}

// Rückwärts zählen
for (int i = 10; i >= 1; i--) {
    System.out.println(i);  // 10, 9, 8, ..., 1
}

// In 2er-Schritten
for (int i = 0; i <= 20; i += 2) {
    System.out.println(i);  // 0, 2, 4, 6, ..., 20
}

// Nur gerade Zahlen
for (int i = 2; i <= 10; i += 2) {
    System.out.println(i);  // 2, 4, 6, 8, 10
}
```

## 🔄 2. While-Schleife: Solange wie...

Die `while`-Schleife verwendest du, wenn du **nicht genau weißt**, wie oft wiederholt wird, aber eine **Bedingung** hast.

### 2.1 Grundsyntax
```java
while (bedingung) {
    // Code, der wiederholt wird
    // WICHTIG: Bedingung muss irgendwann false werden!
}
```

### 2.2 Beispiele
```java
// Countdown
int countdown = 5;
while (countdown > 0) {
    System.out.println("Noch " + countdown + " Sekunden...");
    countdown--;  // WICHTIG: Bedingung ändern!
}
System.out.println("Start! 🚀");

// Zahlen raten
int gesucht = 42;
int geraten = 0;
while (geraten != gesucht) {
    // In echtem Programm: Scanner-Eingabe
    geraten = 42;  // Simulation
    System.out.println("Du hast " + geraten + " geraten");
}
```

### 2.3 Endlos-Schleife vermeiden
```java
// GEFAHR: Endlos-Schleife!
int x = 1;
while (x > 0) {
    System.out.println(x);
    x++;  // x wird immer größer, nie <= 0!
}

// RICHTIG: Bedingung wird irgendwann false
int x = 10;
while (x > 0) {
    System.out.println(x);
    x--;  // x wird kleiner und erreicht 0
}
```

## 🎯 3. Do-While-Schleife: Erst machen, dann prüfen

Die `do-while`-Schleife wird **mindestens einmal** ausgeführt, auch wenn die Bedingung von Anfang an false ist.

### 3.1 Grundsyntax
```java
do {
    // Code, der wiederholt wird
} while (bedingung);
```

### 3.2 Wann verwenden?
**Perfekt für Menüs und Eingabevalidierung:**

```java
// Menü-System
int auswahl;
do {
    System.out.println("=== HAUPTMENÜ ===");
    System.out.println("1. Spiel starten");
    System.out.println("2. Einstellungen");
    System.out.println("3. Beenden");
    
    // Simulation einer Eingabe
    auswahl = 3;  // In echt: Scanner.nextInt()
    
    switch (auswahl) {
        case 1:
            System.out.println("🎮 Spiel gestartet!");
            break;
        case 2:
            System.out.println("⚙️ Einstellungen geöffnet");
            break;
        case 3:
            System.out.println("👋 Auf Wiedersehen!");
            break;
        default:
            System.out.println("❌ Ungültige Auswahl!");
    }
} while (auswahl != 3);
```

### 3.3 Unterschied While vs. Do-While
```java
// While: Kann 0 Mal ausgeführt werden
int x = -1;
while (x > 0) {
    System.out.println("Das siehst du nie!");  // Wird nicht ausgeführt
}

// Do-While: Wird mindestens 1 Mal ausgeführt
int y = -1;
do {
    System.out.println("Das siehst du einmal!");  // Wird ausgeführt
} while (y > 0);
```

## 🔁 4. Enhanced For-Loop (For-Each)

Für Arrays und Collections gibt es eine elegante Kurzform:

### 4.1 Syntax
```java
for (datentyp variable : array/collection) {
    // Code für jedes Element
}
```

### 4.2 Beispiele
```java
// Array durchlaufen
int[] zahlen = {1, 2, 3, 4, 5};

// Klassische for-Schleife
for (int i = 0; i < zahlen.length; i++) {
    System.out.println("Zahl: " + zahlen[i]);
}

// Enhanced for-Schleife (eleganter)
for (int zahl : zahlen) {
    System.out.println("Zahl: " + zahl);
}

// Mit Strings
String[] namen = {"Max", "Anna", "Tom"};
for (String name : namen) {
    System.out.println("Hallo " + name + "!");
}
```

## 🏗️ 5. Verschachtelte Schleifen

Du kannst Schleifen ineinander verschachteln - nützlich für 2D-Strukturen:

### 5.1 Multiplikationstabelle
```java
System.out.println("📊 MULTIPLIKATIONSTABELLE");
System.out.println("==========================");

for (int i = 1; i <= 10; i++) {
    for (int j = 1; j <= 10; j++) {
        System.out.printf("%4d", i * j);
    }
    System.out.println();  // Neue Zeile nach jeder Reihe
}
```

### 5.2 Muster erstellen
```java
// Dreieck aus Sternen
for (int zeile = 1; zeile <= 5; zeile++) {
    for (int stern = 1; stern <= zeile; stern++) {
        System.out.print("* ");
    }
    System.out.println();
}

// Ausgabe:
// * 
// * * 
// * * * 
// * * * * 
// * * * * *
```

### 5.3 2D-Array durchlaufen
```java
int[][] matrix = {
    {1, 2, 3},
    {4, 5, 6},
    {7, 8, 9}
};

// Klassisch
for (int zeile = 0; zeile < matrix.length; zeile++) {
    for (int spalte = 0; spalte < matrix[zeile].length; spalte++) {
        System.out.print(matrix[zeile][spalte] + " ");
    }
    System.out.println();
}

// Enhanced for
for (int[] zeile : matrix) {
    for (int wert : zeile) {
        System.out.print(wert + " ");
    }
    System.out.println();
}
```

## ⏭️ 6. Break und Continue: Schleifensteuerung

### 6.1 Break: Schleife verlassen
```java
// Erste gerade Zahl finden
for (int i = 1; i <= 100; i++) {
    if (i % 2 == 0) {
        System.out.println("Erste gerade Zahl: " + i);
        break;  // Schleife verlassen
    }
}

// Suche in Array
String[] namen = {"Max", "Anna", "Tom", "Lisa"};
String gesucht = "Tom";

for (String name : namen) {
    if (name.equals(gesucht)) {
        System.out.println("Gefunden: " + name);
        break;  // Suche beenden
    }
}
```

### 6.2 Continue: Diese Iteration überspringen
```java
// Nur ungerade Zahlen ausgeben
for (int i = 1; i <= 10; i++) {
    if (i % 2 == 0) {
        continue;  // Gerade Zahlen überspringen
    }
    System.out.println("Ungerade: " + i);
}

// Output: 1, 3, 5, 7, 9

// Negative Zahlen ignorieren
int[] zahlen = {-3, 1, -1, 4, -2, 7};
for (int zahl : zahlen) {
    if (zahl < 0) {
        continue;  // Negative überspringen
    }
    System.out.println("Positive Zahl: " + zahl);
}
```

### 6.3 Break in verschachtelten Schleifen
```java
// Labeled break für äußere Schleife
outer: for (int i = 1; i <= 3; i++) {
    for (int j = 1; j <= 3; j++) {
        if (i == 2 && j == 2) {
            break outer;  // Verlässt beide Schleifen
        }
        System.out.println(i + "," + j);
    }
}
```

## 💡 7. Praktische Anwendungen

### 7.1 Summe berechnen
```java
int summe = 0;
for (int i = 1; i <= 100; i++) {
    summe += i;
}
System.out.println("Summe 1-100: " + summe);  // 5050

// Fakultät berechnen
int n = 5;
int fakultät = 1;
for (int i = 1; i <= n; i++) {
    fakultät *= i;
}
System.out.println(n + "! = " + fakultät);  // 5! = 120
```

### 7.2 Primzahlen finden
```java
int zahl = 29;
boolean istPrimzahl = true;

if (zahl <= 1) {
    istPrimzahl = false;
} else {
    for (int i = 2; i < zahl; i++) {
        if (zahl % i == 0) {
            istPrimzahl = false;
            break;  // Teiler gefunden, kann aufhören
        }
    }
}

System.out.println(zahl + " ist " + (istPrimzahl ? "" : "keine ") + "Primzahl");
```

### 7.3 String umkehren
```java
String original = "Hallo";
String umgekehrt = "";

for (int i = original.length() - 1; i >= 0; i--) {
    umgekehrt += original.charAt(i);
}

System.out.println(original + " → " + umgekehrt);  // Hallo → ollaH
```

## ⚠️ 8. Häufige Fehler

### 1. Off-by-one-Fehler
```java
// FALSCH: Läuft zu lang
for (int i = 0; i <= 10; i++) {  // 11 Durchläufe (0-10)
    System.out.println(i);
}

// RICHTIG: 10 Durchläufe
for (int i = 0; i < 10; i++) {   // 10 Durchläufe (0-9)
    System.out.println(i);
}
```

### 2. Endlos-Schleife
```java
// FALSCH: Endlos-Schleife
int i = 0;
while (i < 10) {
    System.out.println(i);
    // i wird nie erhöht!
}

// RICHTIG:
int i = 0;
while (i < 10) {
    System.out.println(i);
    i++;  // Bedingung ändern!
}
```

### 3. Variable im falschen Scope
```java
// FALSCH: Variable außerhalb nicht verfügbar
for (int i = 0; i < 10; i++) {
    // i nur hier verfügbar
}
System.out.println(i);  // Fehler! i nicht bekannt

// RICHTIG: Variable vorher deklarieren
int i;
for (i = 0; i < 10; i++) {
    // ...
}
System.out.println(i);  // Funktioniert
```

## 🏆 9. Welche Schleife wann?

| Schleife | Wann verwenden | Beispiel |
|----------|----------------|----------|
| `for` | Anzahl bekannt | 10 Mal wiederholen |
| `while` | Bedingung prüfen | Bis Eingabe korrekt |
| `do-while` | Mindestens 1 Mal | Menü anzeigen |
| `for-each` | Array/Collection durchlaufen | Alle Namen ausgeben |

## 🎮 10. Übungsaufgaben

### Aufgabe 1: Zahlenspiele
- Gib alle geraden Zahlen von 2 bis 20 aus
- Berechne die Summe aller ungeraden Zahlen von 1 bis 99
- Finde alle Zahlen von 1 bis 100, die durch 3 und 5 teilbar sind

### Aufgabe 2: Muster erstellen
- Erstelle ein Rechteck aus Sternen (5x3)
- Erstelle eine Pyramide aus Zahlen
- Erstelle ein Schachbrettmuster mit X und O

### Aufgabe 3: Suchen und Zählen
- Zähle Vokale in einem String
- Finde das größte Element in einem Array
- Suche alle Positionen eines Zeichens in einem String

### Aufgabe 4: Interaktive Programme
- Zahlenratespiel (1-100)
- Einfacher Passwort-Generator
- Taschenrechner mit Menü (mit do-while)

### Aufgabe 5: Fortgeschritten
- Primzahlen von 1 bis 100 finden
- Fibonacci-Folge berechnen
- Palindrom-Checker

## 🏆 Zusammenfassung

**For-Schleife:**
- Für bekannte Anzahl Wiederholungen
- `for (start; bedingung; iteration)`

**While-Schleife:**
- Für bedingte Wiederholungen
- Kann 0 Mal ausgeführt werden

**Do-While-Schleife:**
- Mindestens 1 Mal ausgeführt
- Perfekt für Menüs

**Enhanced For (For-Each):**
- Elegant für Arrays/Collections
- `for (element : collection)`

**Schleifensteuerung:**
- `break` - Schleife verlassen
- `continue` - Iteration überspringen

**Best Practices:**
- Endlos-Schleifen vermeiden
- Richtige Schleife für den Zweck wählen
- Off-by-one-Fehler beachten

---

## 🚀 Weiter geht's!

Im nächsten Kapitel lernst du **Arrays** - wie du viele Werte organisiert speicherst!
