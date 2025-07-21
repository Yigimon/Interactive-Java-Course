# Kapitel 7: Methoden in Java - Theorie

## 🎯 Lernziele
Nach diesem Kapitel kannst du:
- Eigene Methoden erstellen und aufrufen
- Parameter übergeben und Rückgabewerte verwenden
- Den Unterschied zwischen static und non-static verstehen
- Methoden überladen (Overloading)
- Variable Parameterlisten verwenden
- Rekursion verstehen und anwenden

## 📚 Was sind Methoden?

**Methoden** sind wie **Maschinen** in einer Fabrik - du gibst etwas hinein (Parameter), sie verarbeiten es, und geben ein Ergebnis zurück (Rückgabewert).

```java
// Statt immer wieder denselben Code zu schreiben:
int summe1 = 5 + 3;
System.out.println("Summe: " + summe1);

int summe2 = 12 + 8;
System.out.println("Summe: " + summe2);

int summe3 = 15 + 7;
System.out.println("Summe: " + summe3);

// Besser: Eine Methode erstellen
public static void zeigeAddition(int a, int b) {
    int summe = a + b;
    System.out.println("Summe: " + summe);
}

// Und dann mehrfach verwenden:
zeigeAddition(5, 3);
zeigeAddition(12, 8);
zeigeAddition(15, 7);
```

**Vorteile von Methoden:**
- ✅ **Wiederverwendbarkeit** - einmal schreiben, oft nutzen
- ✅ **Übersichtlichkeit** - Code in kleine Häppchen aufteilen
- ✅ **Wartbarkeit** - Änderungen nur an einer Stelle
- ✅ **Testbarkeit** - einzelne Funktionen testen

## 🔧 1. Methoden-Grundlagen

### 1.1 Methoden-Syntax
```java
[sichtbarkeit] [static] rückgabetyp methodenName(parameter) {
    // Methodenkörper
    return wert;  // nur bei Rückgabewert ≠ void
}
```

### 1.2 Einfache Methode ohne Parameter
```java
public static void sayHello() {
    System.out.println("Hallo Welt!");
    System.out.println("Wie geht es dir?");
}

// Aufruf:
sayHello();  // Ausgabe: Hallo Welt! + Wie geht es dir?
```

### 1.3 Methode mit Parametern
```java
public static void begrüße(String name) {
    System.out.println("Hallo " + name + "!");
    System.out.println("Schön, dich zu sehen!");
}

// Aufruf:
begrüße("Max");    // Hallo Max!
begrüße("Anna");   // Hallo Anna!
```

### 1.4 Methode mit Rückgabewert
```java
public static int addiere(int a, int b) {
    int summe = a + b;
    return summe;  // Wert zurückgeben
}

// Aufruf:
int ergebnis = addiere(5, 3);  // ergebnis = 8
System.out.println("5 + 3 = " + ergebnis);

// Oder direkt verwenden:
System.out.println("10 + 7 = " + addiere(10, 7));
```

## 📨 2. Parameter und Argumente

### 2.1 Verschiedene Parameter-Typen
```java
// Verschiedene Datentypen als Parameter
public static void zeigeInfos(String name, int alter, double größe, boolean istSchüler) {
    System.out.println("Name: " + name);
    System.out.println("Alter: " + alter + " Jahre");
    System.out.println("Größe: " + größe + " m");
    System.out.println("Ist Schüler: " + istSchüler);
}

// Aufruf:
zeigeInfos("Lisa", 16, 1.65, true);
```

### 2.2 Arrays als Parameter
```java
public static void zeigeArray(int[] zahlen) {
    System.out.print("Array: ");
    for (int zahl : zahlen) {
        System.out.print(zahl + " ");
    }
    System.out.println();
}

public static int berechneSum(int[] zahlen) {
    int summe = 0;
    for (int zahl : zahlen) {
        summe += zahl;
    }
    return summe;
}

// Aufruf:
int[] meinArray = {1, 2, 3, 4, 5};
zeigeArray(meinArray);                    // Array: 1 2 3 4 5
int summe = berechneSum(meinArray);      // summe = 15
```

### 2.3 Call by Value vs. Call by Reference
```java
// Primitive Typen: Call by Value (Kopie wird übergeben)
public static void ändereZahl(int zahl) {
    zahl = 100;  // Ändert nur die lokale Kopie
}

int x = 5;
ändereZahl(x);
System.out.println(x);  // Immer noch 5!

// Arrays/Objekte: Call by Reference (Referenz wird übergeben)
public static void ändereArray(int[] array) {
    array[0] = 999;  // Ändert das ursprüngliche Array
}

int[] zahlen = {1, 2, 3};
ändereArray(zahlen);
System.out.println(zahlen[0]);  // 999!
```

## 📤 3. Rückgabewerte

### 3.1 Verschiedene Rückgabetypen
```java
// void: Keine Rückgabe
public static void druckeText(String text) {
    System.out.println(text);
}

// int: Ganze Zahl zurückgeben
public static int quadrat(int zahl) {
    return zahl * zahl;
}

// boolean: Wahrheitswert zurückgeben
public static boolean istGerade(int zahl) {
    return zahl % 2 == 0;
}

// String: Text zurückgeben
public static String erstelleGruß(String name) {
    return "Hallo " + name + ", wie geht es dir?";
}

// Array: Array zurückgeben
public static int[] erstelleZahlenreihe(int start, int ende) {
    int länge = ende - start + 1;
    int[] zahlen = new int[länge];
    for (int i = 0; i < länge; i++) {
        zahlen[i] = start + i;
    }
    return zahlen;
}
```

### 3.2 Mehrere return-Anweisungen
```java
public static String bewerteNote(double note) {
    if (note <= 1.5) {
        return "Sehr gut! 🌟";
    }
    if (note <= 2.5) {
        return "Gut! 👍";
    }
    if (note <= 3.5) {
        return "Befriedigend 👌";
    }
    if (note <= 4.0) {
        return "Ausreichend ✔️";
    }
    return "Nicht bestanden ❌";
}

// Verwendung:
double meinNote = 2.1;
String bewertung = bewerteNote(meinNote);
System.out.println("Note " + meinNote + ": " + bewertung);
```

## 🎭 4. Methoden Überladen (Overloading)

Du kannst **mehrere Methoden mit gleichem Namen** haben, solange sie unterschiedliche Parameter haben:

### 4.1 Überladung mit verschiedenen Typen
```java
// Verschiedene addiere-Methoden
public static int addiere(int a, int b) {
    return a + b;
}

public static double addiere(double a, double b) {
    return a + b;
}

public static String addiere(String a, String b) {
    return a + b;  // String-Verkettung
}

// Verwendung:
int summe1 = addiere(5, 3);        // int-Version
double summe2 = addiere(5.5, 3.2); // double-Version
String text = addiere("Hallo ", "Welt"); // String-Version
```

### 4.2 Überladung mit verschiedener Parameter-Anzahl
```java
public static void gibAus(String text) {
    System.out.println(text);
}

public static void gibAus(String text, int anzahl) {
    for (int i = 0; i < anzahl; i++) {
        System.out.println(text);
    }
}

public static void gibAus(String text, int anzahl, String trenner) {
    for (int i = 0; i < anzahl; i++) {
        System.out.print(text);
        if (i < anzahl - 1) {
            System.out.print(trenner);
        }
    }
    System.out.println();
}

// Verwendung:
gibAus("Hallo");                    // Einmal ausgeben
gibAus("Hi", 3);                    // 3x ausgeben
gibAus("Java", 3, " - ");          // Java - Java - Java
```

## 📦 5. Variable Parameterlisten (Varargs)

Mit `...` kannst du eine variable Anzahl Parameter übergeben:

### 5.1 Varargs-Syntax
```java
public static int addiere(int... zahlen) {
    int summe = 0;
    for (int zahl : zahlen) {
        summe += zahl;
    }
    return summe;
}

// Verschiedene Aufrufe möglich:
int summe1 = addiere(1, 2);              // 2 Parameter
int summe2 = addiere(1, 2, 3, 4);        // 4 Parameter  
int summe3 = addiere(5, 10, 15, 20, 25); // 5 Parameter

// Oder mit Array:
int[] zahlen = {1, 2, 3, 4, 5};
int summe4 = addiere(zahlen);
```

### 5.2 Praktisches Beispiel: printf-ähnlich
```java
public static void gibNachrichtAus(String template, Object... werte) {
    System.out.printf(template, werte);
}

// Verwendung:
gibNachrichtAus("Hallo %s, du bist %d Jahre alt!%n", "Max", 16);
gibNachrichtAus("Summe von %d + %d = %d%n", 5, 3, 8);
```

## 🔄 6. Rekursion

Eine Methode kann **sich selbst aufrufen** - das nennt man **Rekursion**:

### 6.1 Einfaches Beispiel: Fakultät
```java
public static int fakultät(int n) {
    // Abbruchbedingung (wichtig!)
    if (n <= 1) {
        return 1;
    }
    
    // Rekursiver Aufruf
    return n * fakultät(n - 1);
}

// fakultät(5) = 5 * fakultät(4)
//              = 5 * 4 * fakultät(3)  
//              = 5 * 4 * 3 * fakultät(2)
//              = 5 * 4 * 3 * 2 * fakultät(1)
//              = 5 * 4 * 3 * 2 * 1 = 120
```

### 6.2 Fibonacci-Folge
```java
public static int fibonacci(int n) {
    if (n <= 1) {
        return n;  // fibonacci(0) = 0, fibonacci(1) = 1
    }
    return fibonacci(n - 1) + fibonacci(n - 2);
}

// fibonacci(5) = fibonacci(4) + fibonacci(3)
//              = (fibonacci(3) + fibonacci(2)) + (fibonacci(2) + fibonacci(1))
//              = ... = 5
```

### 6.3 Rekursion vs. Iteration
```java
// Rekursiv: Elegant, aber langsamer
public static int summeRekursiv(int n) {
    if (n <= 0) return 0;
    return n + summeRekursiv(n - 1);
}

// Iterativ: Schneller, mehr Code
public static int summeIterativ(int n) {
    int summe = 0;
    for (int i = 1; i <= n; i++) {
        summe += i;
    }
    return summe;
}
```

## 🔧 7. Praktische Methoden-Beispiele

### 7.1 Mathematische Hilfsmethoden
```java
public static double kreisFlaeche(double radius) {
    return Math.PI * radius * radius;
}

public static double kreisUmfang(double radius) {
    return 2 * Math.PI * radius;
}

public static boolean istPrimzahl(int zahl) {
    if (zahl <= 1) return false;
    for (int i = 2; i < zahl; i++) {
        if (zahl % i == 0) return false;
    }
    return true;
}

public static int ggT(int a, int b) {  // Größter gemeinsamer Teiler
    while (b != 0) {
        int temp = b;
        b = a % b;
        a = temp;
    }
    return a;
}
```

### 7.2 String-Hilfsmethoden
```java
public static String umkehren(String text) {
    String umgekehrt = "";
    for (int i = text.length() - 1; i >= 0; i--) {
        umgekehrt += text.charAt(i);
    }
    return umgekehrt;
}

public static int zähleVokale(String text) {
    int anzahl = 0;
    String vowels = "aeiouAEIOU";
    for (int i = 0; i < text.length(); i++) {
        if (vowels.indexOf(text.charAt(i)) != -1) {
            anzahl++;
        }
    }
    return anzahl;
}

public static boolean istPalindrom(String text) {
    String sauber = text.toLowerCase().replaceAll("[^a-z]", "");
    return sauber.equals(umkehren(sauber));
}
```

### 7.3 Array-Hilfsmethoden
```java
public static int[] sortiereBubble(int[] array) {
    int[] kopie = Arrays.copyOf(array, array.length);
    
    for (int i = 0; i < kopie.length - 1; i++) {
        for (int j = 0; j < kopie.length - 1 - i; j++) {
            if (kopie[j] > kopie[j + 1]) {
                // Tauschen
                int temp = kopie[j];
                kopie[j] = kopie[j + 1];
                kopie[j + 1] = temp;
            }
        }
    }
    return kopie;
}

public static int lineareSuche(int[] array, int gesucht) {
    for (int i = 0; i < array.length; i++) {
        if (array[i] == gesucht) {
            return i;  // Index zurückgeben
        }
    }
    return -1;  // Nicht gefunden
}

public static void mische(int[] array) {
    for (int i = 0; i < array.length; i++) {
        int randomIndex = (int) (Math.random() * array.length);
        
        // Elemente tauschen
        int temp = array[i];
        array[i] = array[randomIndex];
        array[randomIndex] = temp;
    }
}
```

## ⚠️ 8. Häufige Fehler

### 1. Fehlende return-Anweisung
```java
// FALSCH:
public static int berechne(int x) {
    if (x > 0) {
        return x * 2;
    }
    // Fehlt: return für x <= 0!
}

// RICHTIG:
public static int berechne(int x) {
    if (x > 0) {
        return x * 2;
    }
    return 0;  // Standardwert
}
```

### 2. Falscher Rückgabetyp
```java
// FALSCH:
public static void addiere(int a, int b) {
    return a + b;  // void kann nichts zurückgeben!
}

// RICHTIG:
public static int addiere(int a, int b) {
    return a + b;
}
```

### 3. Endlose Rekursion
```java
// FALSCH: Keine Abbruchbedingung
public static int schlecht(int n) {
    return n + schlecht(n - 1);  // Läuft endlos!
}

// RICHTIG: Mit Abbruchbedingung
public static int gut(int n) {
    if (n <= 0) return 0;  // Abbruch!
    return n + gut(n - 1);
}
```

## 💡 9. Best Practices

### 9.1 Methoden-Design
```java
// GUT: Eine Aufgabe pro Methode
public static boolean istGerade(int zahl) {
    return zahl % 2 == 0;
}

public static void gibGeradeZahlenAus(int[] zahlen) {
    for (int zahl : zahlen) {
        if (istGerade(zahl)) {
            System.out.println(zahl);
        }
    }
}

// SCHLECHT: Zu viele Aufgaben in einer Methode
public static void machAlles(int[] zahlen, String name, double note) {
    // Gerade Zahlen ausgeben
    // Namen begrüßen  
    // Note bewerten
    // ... zu viel!
}
```

### 9.2 Aussagekräftige Namen
```java
// GUT: Namen erklären, was die Methode tut
public static double berechneKreisflaeche(double radius) { ... }
public static boolean istPasswortStark(String passwort) { ... }
public static int[] filtereGeradeZahlen(int[] zahlen) { ... }

// SCHLECHT: Unklare Namen
public static double calc(double x) { ... }
public static boolean check(String s) { ... }
public static int[] doStuff(int[] arr) { ... }
```

### 9.3 Parameter-Validierung
```java
public static double berechneKreisflaeche(double radius) {
    if (radius < 0) {
        throw new IllegalArgumentException("Radius darf nicht negativ sein!");
    }
    return Math.PI * radius * radius;
}

public static int fakultaet(int n) {
    if (n < 0) {
        throw new IllegalArgumentException("Fakultät nur für n >= 0 definiert!");
    }
    if (n <= 1) return 1;
    return n * fakultaet(n - 1);
}
```

## 🎮 10. Übungsaufgaben

### Aufgabe 1: Grundlagen
- Schreibe Methoden für Grundrechenarten (+, -, *, /, %)
- Erstelle eine Methode zur Temperatur-Umrechnung (C ↔ F)
- Implementiere eine Methode zur Notenbewertung

### Aufgabe 2: String-Methoden
- Methode zum Zählen von Zeichen in einem String
- Methode zum Entfernen von Leerzeichen
- Methode zur Prüfung auf Palindrome

### Aufgabe 3: Array-Methoden
- Methode zum Finden des größten/kleinsten Elements
- Methode zum Umkehren eines Arrays
- Methode zum Entfernen von Duplikaten

### Aufgabe 4: Rekursion
- Berechne die n-te Fibonacci-Zahl
- Implementiere die Türme von Hanoi
- Berechne die Summe der Ziffern einer Zahl

### Aufgabe 5: Komplexe Anwendung
- Erstelle ein Menü-System mit verschiedenen Methoden
- Implementiere einen einfachen Taschenrechner
- Programmiere ein Zahlenratespiel mit Hilfsmethoden

## 🏆 Zusammenfassung

**Methoden-Aufbau:**
- `[sichtbarkeit] [static] rückgabetyp name(parameter)`
- Verwende `void` wenn kein Rückgabewert
- `return` beendet Methode und gibt Wert zurück

**Parameter:**
- Primitive Typen: Call by Value (Kopie)
- Arrays/Objekte: Call by Reference
- Varargs mit `...` für variable Anzahl

**Überladung:**
- Gleicher Name, verschiedene Parameter
- Unterschied in Anzahl oder Typ der Parameter

**Rekursion:**
- Methode ruft sich selbst auf
- Braucht Abbruchbedingung!
- Elegant aber potentiell langsam

**Best Practices:**
- Eine Aufgabe pro Methode
- Aussagekräftige Namen
- Parameter validieren
- Code wiederverwenden

---

## 🚀 Weiter geht's!

Im nächsten Kapitel lernst du **Objektorientierte Programmierung** - wie du eigene Klassen und Objekte erstellst!
