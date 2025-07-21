# Kapitel 3: Ein- und Ausgabe in Java - Theorie

## 🎯 Lernziele
Nach diesem Kapitel kannst du:
- Daten mit `System.out.println()` ausgeben
- Formatierte Ausgaben mit `System.out.printf()` erstellen
- Benutzereingaben mit `Scanner` einlesen
- Verschiedene Datentypen vom Benutzer abfragen
- Interaktive Programme schreiben

## 📚 Was ist Ein- und Ausgabe?

**Ausgabe** bedeutet, dass dein Programm Informationen an den Benutzer **sendet** (auf dem Bildschirm anzeigt).
**Eingabe** bedeutet, dass dein Programm Informationen vom Benutzer **empfängt** (über Tastatur).

Ohne Ein- und Ausgabe wäre dein Programm wie ein stummes Rätsel - niemand würde wissen, was es macht!

## 📤 1. Ausgabe (Output)

### 1.1 System.out.println()
Das ist dein **Megafon** zum Benutzer:

```java
System.out.println("Hallo Welt!");
System.out.println("Ich bin ein Java-Programm!");
```

**Wichtige Methoden:**

| Methode | Wirkung | Beispiel |
|---------|---------|----------|
| `println()` | Gibt Text aus + neue Zeile | `System.out.println("Hallo");` |
| `print()` | Gibt Text aus (keine neue Zeile) | `System.out.print("Hallo");` |
| `printf()` | Formatierte Ausgabe | `System.out.printf("%.2f", 3.14159);` |

### 1.2 Variablen ausgeben
```java
String name = "Max";
int alter = 16;
System.out.println("Name: " + name);
System.out.println("Alter: " + alter);

// Oder alles in einer Zeile:
System.out.println("Hallo " + name + ", du bist " + alter + " Jahre alt!");
```

### 1.3 Formatierte Ausgabe mit printf()
`printf()` ist wie ein **Textbaukasten** mit Platzhaltern:

```java
String name = "Anna";
double note = 2.3;
int punkte = 87;

System.out.printf("Schülerin: %s%n", name);
System.out.printf("Note: %.1f%n", note);
System.out.printf("Punkte: %d%n", punkte);
```

**Wichtige Platzhalter:**

| Platzhalter | Datentyp | Beispiel |
|-------------|----------|----------|
| `%s` | String | `"Max"` |
| `%d` | int (ganze Zahl) | `42` |
| `%f` | double/float | `3.14159` |
| `%.2f` | double mit 2 Nachkommastellen | `3.14` |
| `%n` | Neue Zeile | (Zeilenumbruch) |
| `%%` | Prozentzeichen | `%` |

## 📥 2. Eingabe (Input) mit Scanner

Um Daten vom Benutzer zu bekommen, brauchst du die `Scanner`-Klasse:

### 2.1 Scanner einrichten
```java
import java.util.Scanner;  // Am Anfang der Datei!

Scanner eingabe = new Scanner(System.in);
```

### 2.2 Verschiedene Eingaben lesen

| Methode | Datentyp | Beispiel |
|---------|----------|----------|
| `nextLine()` | String (ganze Zeile) | `"Max Mustermann"` |
| `next()` | String (ein Wort) | `"Max"` |
| `nextInt()` | int | `42` |
| `nextDouble()` | double | `3.14` |
| `nextBoolean()` | boolean | `true` oder `false` |

### Beispiel: Vollständige Eingabe
```java
import java.util.Scanner;

Scanner eingabe = new Scanner(System.in);

System.out.print("Wie heißt du? ");
String name = eingabe.nextLine();

System.out.print("Wie alt bist du? ");
int alter = eingabe.nextInt();

System.out.println("Hallo " + name + ", du bist " + alter + " Jahre alt!");

eingabe.close();  // Scanner schließen (gute Praxis)
```

## 🔍 3. Wichtige Details

### 3.1 Der Unterschied: next() vs. nextLine()
```java
Scanner eingabe = new Scanner(System.in);

// Bei Eingabe: "Max Mustermann"
String wort = eingabe.next();      // Liest nur "Max"
String zeile = eingabe.nextLine(); // Liest " Mustermann" (Rest der Zeile)
```

### 3.2 Gemischte Eingaben (Vorsicht!)
```java
Scanner eingabe = new Scanner(System.in);

System.out.print("Alter: ");
int alter = eingabe.nextInt();       // Liest Zahl, aber nicht den Zeilenumbruch!

System.out.print("Name: ");
eingabe.nextLine();                  // Leert den Zeilenpuffer
String name = eingabe.nextLine();    // Jetzt funktioniert es richtig
```

### 3.3 Fehlerbehandlung
```java
Scanner eingabe = new Scanner(System.in);

System.out.print("Gib eine Zahl ein: ");
if (eingabe.hasNextInt()) {
    int zahl = eingabe.nextInt();
    System.out.println("Deine Zahl: " + zahl);
} else {
    System.out.println("Das war keine Zahl!");
}
```

## 🎨 4. Schöne Ausgaben gestalten

### 4.1 Boxen und Rahmen
```java
System.out.println("╔═══════════════════╗");
System.out.println("║  MEIN PROGRAMM    ║");
System.out.println("╚═══════════════════╝");
```

### 4.2 Emojis und Symbole
```java
System.out.println("🎮 Willkommen im Spiel!");
System.out.println("⭐ Du hast 100 Punkte!");
System.out.println("❌ Fehler aufgetreten!");
System.out.println("✅ Erfolgreich gespeichert!");
```

### 4.3 Tabellen
```java
System.out.println("Name         | Alter | Note");
System.out.println("-------------|-------|-----");
System.out.printf("%-12s | %5d | %4.1f%n", "Max", 16, 2.3);
System.out.printf("%-12s | %5d | %4.1f%n", "Anna", 15, 1.8);
```

## ⚠️ 5. Häufige Fehler

### 1. Import vergessen
```java
// FEHLER: Scanner ohne Import
Scanner eingabe = new Scanner(System.in);  // Fehler!

// RICHTIG:
import java.util.Scanner;  // Am Anfang der Datei
// ... später im Code:
Scanner eingabe = new Scanner(System.in);
```

### 2. Scanner nicht geschlossen
```java
Scanner eingabe = new Scanner(System.in);
// ... Code ...
eingabe.close();  // Nicht vergessen!
```

### 3. Falsche Eingabemethode
```java
Scanner eingabe = new Scanner(System.in);

// User gibt "3.14" ein
int zahl = eingabe.nextInt();  // FEHLER: nextInt() kann keine Kommazahlen!

// RICHTIG:
double zahl = eingabe.nextDouble();
```

### 4. Zeilenpuffer-Problem
```java
Scanner eingabe = new Scanner(System.in);

int alter = eingabe.nextInt();       // User: "16<ENTER>"
String name = eingabe.nextLine();    // Bekommt nur den leeren Zeilenumbruch!

// LÖSUNG:
int alter = eingabe.nextInt();
eingabe.nextLine();                  // Puffer leeren
String name = eingabe.nextLine();    // Jetzt funktioniert es
```

## 💡 6. Praktische Anwendungen

### 6.1 Einfacher Taschenrechner
```java
import java.util.Scanner;

Scanner eingabe = new Scanner(System.in);

System.out.print("Erste Zahl: ");
double a = eingabe.nextDouble();

System.out.print("Zweite Zahl: ");
double b = eingabe.nextDouble();

System.out.println("Summe: " + (a + b));
System.out.println("Differenz: " + (a - b));
System.out.println("Produkt: " + (a * b));
System.out.println("Quotient: " + (a / b));

eingabe.close();
```

### 6.2 Benutzerfreundliche Eingabe
```java
import java.util.Scanner;

Scanner eingabe = new Scanner(System.in);

System.out.println("🎓 SCHÜLER-REGISTRIERUNG");
System.out.println("========================");

System.out.print("Vorname: ");
String vorname = eingabe.nextLine();

System.out.print("Nachname: ");
String nachname = eingabe.nextLine();

System.out.print("Alter: ");
int alter = eingabe.nextInt();

System.out.print("Durchschnittsnote (z.B. 2.3): ");
double note = eingabe.nextDouble();

System.out.println("\n✅ REGISTRIERUNG ERFOLGREICH!");
System.out.printf("Name: %s %s%n", vorname, nachname);
System.out.printf("Alter: %d Jahre%n", alter);
System.out.printf("Durchschnitt: %.1f%n", note);

eingabe.close();
```

## 🎮 7. Übungsaufgaben

### Aufgabe 1: Persönlicher Assistent
Erstelle ein Programm, das nach Name, Alter, Lieblingsfach und Hobbys fragt und dann eine schöne Zusammenfassung ausgibt.

### Aufgabe 2: Notenrechner
Frage nach 3 Noten, berechne den Durchschnitt und gib aus, ob bestanden wurde (≥4.0).

### Aufgabe 3: Einkaufsliste
Frage nach Produktname, Preis und Anzahl. Berechne den Gesamtpreis und formatiere die Ausgabe schön.

### Aufgabe 4: Quiz-Spiel
Stelle 3 Fragen, sammle die Antworten und gib am Ende die Punktzahl aus.

## 🌟 8. Tipps für schöne Programme

### 8.1 Benutzerfreundlichkeit
```java
// GUT: Klare Anweisungen
System.out.print("Gib dein Alter ein (nur Zahlen): ");

// SCHLECHT: Unklare Anweisung  
System.out.print("Alter: ");
```

### 8.2 Eingabe-Validierung
```java
Scanner eingabe = new Scanner(System.in);

System.out.print("Alter (1-120): ");
while (!eingabe.hasNextInt()) {
    System.out.print("Bitte nur Zahlen eingeben: ");
    eingabe.next();  // Falsche Eingabe überspringen
}
int alter = eingabe.nextInt();
```

### 8.3 Schöne Formatierung
```java
// Zahlen rechtsbündig, Text linksbündig
System.out.printf("%-15s: %8.2f€%n", "Produktname", preis);
System.out.printf("%-15s: %8d Stk%n", "Anzahl", anzahl);
```

## 🏆 Zusammenfassung

**Ausgabe:**
- `System.out.println()` für einfache Ausgaben
- `System.out.printf()` für formatierte Ausgaben
- Emojis und Boxen für schöne Gestaltung

**Eingabe:**
- `Scanner` für Benutzereingaben
- Verschiedene `next...()`-Methoden für verschiedene Datentypen
- Zeilenpuffer beachten!
- Scanner am Ende schließen

**Goldene Regel:** Mache dein Programm benutzerfreundlich - klare Anweisungen, schöne Ausgaben, Fehlerbehandlung!

---

## 🚀 Weiter geht's!

Im nächsten Kapitel lernst du **Kontrollstrukturen** - wie dein Programm Entscheidungen trifft!
