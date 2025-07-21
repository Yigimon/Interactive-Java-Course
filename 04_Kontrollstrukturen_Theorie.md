# Kapitel 4: Kontrollstrukturen in Java - Theorie

## 🎯 Lernziele
Nach diesem Kapitel kannst du:
- Mit `if-else` Entscheidungen treffen
- Mehrfache Verzweigungen mit `else if` erstellen
- `switch`-Anweisungen für multiple Optionen verwenden
- Verschachtelte Bedingungen verstehen und anwenden
- Ternäre Operatoren (`? :`) für kurze Entscheidungen nutzen

## 📚 Was sind Kontrollstrukturen?

**Kontrollstrukturen** steuern den **Ablauf** deines Programms. Ohne sie würde dein Code nur von oben nach unten abgearbeitet - wie ein Roboter ohne Gehirn!

Mit Kontrollstrukturen kann dein Programm:
- 🤔 **Entscheidungen treffen** (`if-else`)
- 🔄 **Abläufe wiederholen** (Schleifen - nächstes Kapitel)
- 🎯 **Zwischen vielen Optionen wählen** (`switch`)

## 🤔 1. If-Else: Die Grundlage aller Entscheidungen

### 1.1 Einfaches if
```java
int alter = 16;

if (alter >= 18) {
    System.out.println("Du bist volljährig!");
}
```

**Syntax:**
```java
if (bedingung) {
    // Code, der ausgeführt wird, wenn bedingung true ist
}
```

### 1.2 If-Else
```java
int alter = 16;

if (alter >= 18) {
    System.out.println("Du bist volljährig!");
} else {
    System.out.println("Du bist noch minderjährig.");
}
```

### 1.3 Else-If (Mehrfache Verzweigungen)
```java
int punkte = 85;

if (punkte >= 90) {
    System.out.println("Sehr gut!");
} else if (punkte >= 80) {
    System.out.println("Gut!");
} else if (punkte >= 70) {
    System.out.println("Befriedigend");
} else if (punkte >= 60) {
    System.out.println("Ausreichend");
} else {
    System.out.println("Nicht bestanden");
}
```

## 🎮 2. Praktische Beispiele

### 2.1 Login-System
```java
String benutzername = "admin";
String passwort = "geheim123";

String eingabeName = "admin";
String eingabePasswort = "geheim123";

if (benutzername.equals(eingabeName) && passwort.equals(eingabePasswort)) {
    System.out.println("✅ Login erfolgreich!");
} else {
    System.out.println("❌ Login fehlgeschlagen!");
}
```

### 2.2 Notenklassifikation
```java
double note = 2.3;

if (note >= 1.0 && note <= 1.5) {
    System.out.println("Sehr gut! 🌟");
} else if (note <= 2.5) {
    System.out.println("Gut! 👍");
} else if (note <= 3.5) {
    System.out.println("Befriedigend 👌");
} else if (note <= 4.0) {
    System.out.println("Ausreichend ✔️");
} else {
    System.out.println("Nicht bestanden ❌");
}
```

### 2.3 Wetterberatung
```java
int temperatur = 22;
boolean regnet = false;

if (temperatur > 25 && !regnet) {
    System.out.println("🌞 Perfektes Wetter für draußen!");
} else if (temperatur > 20) {
    System.out.println("🧥 Nimm eine Jacke mit!");
} else if (regnet) {
    System.out.println("☔ Vergiss den Regenschirm nicht!");
} else {
    System.out.println("🏠 Heute lieber drinnen bleiben.");
}
```

## 🎯 3. Switch-Anweisung: Der Mehrfach-Schalter

Wenn du viele gleichwertige Optionen hast, ist `switch` oft sauberer als viele `else if`:

### 3.1 Grundsyntax
```java
int tag = 3;

switch (tag) {
    case 1:
        System.out.println("Montag");
        break;
    case 2:
        System.out.println("Dienstag");
        break;
    case 3:
        System.out.println("Mittwoch");
        break;
    default:
        System.out.println("Unbekannter Tag");
        break;
}
```

### 3.2 Wichtig: break-Statement
**Ohne `break` wird weitergemacht (Fall-through):**
```java
int note = 2;

switch (note) {
    case 1:
        System.out.println("Sehr gut!");
        // FEHLT: break; 
    case 2:
        System.out.println("Gut!");
        break;
    case 3:
        System.out.println("Befriedigend");
        break;
}
// Bei note=1 wird ausgegeben: "Sehr gut!" UND "Gut!"
```

### 3.3 Praktisches Beispiel: Menü-System
```java
char auswahl = 'B';

switch (auswahl) {
    case 'A':
    case 'a':
        System.out.println("🎮 Spiel starten");
        break;
    case 'B':
    case 'b':
        System.out.println("⚙️ Einstellungen");
        break;
    case 'C':
    case 'c':
        System.out.println("❌ Spiel beenden");
        break;
    default:
        System.out.println("Ungültige Auswahl!");
        break;
}
```

### 3.4 Switch mit Strings (ab Java 7)
```java
String fach = "Informatik";

switch (fach) {
    case "Mathematik":
        System.out.println("📐 Zahlen und Formeln");
        break;
    case "Deutsch":
        System.out.println("📚 Sprache und Literatur");
        break;
    case "Informatik":
        System.out.println("💻 Programmieren und Logik");
        break;
    default:
        System.out.println("Interessantes Fach!");
        break;
}
```

## ⚡ 4. Ternärer Operator: Kurze Entscheidungen

Für einfache if-else-Entscheidungen gibt es eine Kurzform:

### 4.1 Syntax
```java
ergebnis = (bedingung) ? wertWennTrue : wertWennFalse;
```

### 4.2 Beispiele
```java
int alter = 17;
String status = (alter >= 18) ? "volljährig" : "minderjährig";
System.out.println("Du bist " + status);

int a = 10, b = 20;
int max = (a > b) ? a : b;
System.out.println("Maximum: " + max);

// Statt:
String note;
if (punkte >= 50) {
    note = "bestanden";
} else {
    note = "nicht bestanden";
}

// Kurz:
String note = (punkte >= 50) ? "bestanden" : "nicht bestanden";
```

## 🔗 5. Verschachtelte Bedingungen

Du kannst if-else-Anweisungen ineinander schachteln:

```java
int alter = 16;
boolean fuehrerschein = false;
double geld = 50.0;

if (alter >= 16) {
    System.out.println("Alt genug für Moped!");
    
    if (fuehrerschein) {
        System.out.println("Führerschein vorhanden ✅");
        
        if (geld >= 30.0) {
            System.out.println("Genug Geld für Benzin! 🚗");
        } else {
            System.out.println("Kein Geld für Benzin 💸");
        }
    } else {
        System.out.println("Erst Führerschein machen! 📖");
    }
} else {
    System.out.println("Noch zu jung 👶");
}
```

## ⚠️ 6. Häufige Fehler

### 1. Zuweisung statt Vergleich
```java
int x = 5;

// FALSCH:
if (x = 10) { ... }  // Zuweisung!

// RICHTIG:
if (x == 10) { ... }  // Vergleich!
```

### 2. Vergessene break in switch
```java
// FALSCH:
switch (tag) {
    case 1:
        System.out.println("Montag");
        // break; vergessen!
    case 2:
        System.out.println("Dienstag");
        break;
}
```

### 3. Falsche String-Vergleiche
```java
String name = "Max";

// FALSCH:
if (name == "Max") { ... }  // Referenz-Vergleich!

// RICHTIG:
if (name.equals("Max")) { ... }  // Inhalt-Vergleich!
```

### 4. Logik-Fehler bei Bereichen
```java
int note = 2;

// FALSCH:
if (note >= 1 && note >= 2) { ... }  // Beide Bedingungen können nicht gleichzeitig optimal sein

// RICHTIG:
if (note >= 1 && note <= 2) { ... }  // Bereich 1-2
```

## 💡 7. Best Practices

### 7.1 Lesbare Bedingungen
```java
// GUT: Klare Variablennamen
boolean istVolljährig = (alter >= 18);
boolean hatGenugGeld = (geld >= preis);

if (istVolljährig && hatGenugGeld) {
    // Aktion
}

// SCHLECHT: Komplexe Bedingung
if (alter >= 18 && geld >= 50.0 && !gesperrt && verfügbar) {
    // Schwer zu verstehen
}
```

### 7.2 Guard Clauses (Frühe Rückgaben)
```java
// GUT: Frühe Prüfungen
if (alter < 18) {
    System.out.println("Zu jung!");
    return;
}

if (!hatFührerschein) {
    System.out.println("Kein Führerschein!");
    return;
}

// Hauptlogik hier...

// SCHLECHT: Tiefe Verschachtelung
if (alter >= 18) {
    if (hatFührerschein) {
        // Hauptlogik tief verschachtelt
    }
}
```

### 7.3 Switch vs. If-Else
```java
// Switch für gleichwertige Optionen:
switch (wochentag) {
    case "Montag": ...
    case "Dienstag": ...
}

// If-Else für Bereiche/komplexe Bedingungen:
if (note <= 1.5) {
    // Sehr gut
} else if (note <= 2.5) {
    // Gut
}
```

## 🎮 8. Übungsaufgaben

### Aufgabe 1: Taschenrechner mit Menü
Erstelle ein Menü mit den Optionen +, -, *, / und verwende switch für die Auswahl.

### Aufgabe 2: Passwort-Checker
Prüfe ein Passwort auf:
- Mindestens 8 Zeichen
- Enthält Zahlen
- Enthält Großbuchstaben

### Aufgabe 3: Rabatt-System
Berechne Rabatte basierend auf:
- Alter (Schüler/Student/Senior)
- Einkaufswert
- Mitgliedschaft

### Aufgabe 4: Spiel: Schere, Stein, Papier
Implementiere das Spiel mit allen Gewinn-/Verlust-Bedingungen.

### Aufgabe 5: Notensystem
Wandle Punkte (0-100) in Noten (1-6) um und gib eine Bewertung aus.

## 🏆 Zusammenfassung

**If-Else:**
- Grundlage für alle Entscheidungen
- `if`, `else if`, `else` für verschiedene Pfade
- Logische Operatoren für komplexe Bedingungen

**Switch:**
- Elegant für viele gleichwertige Optionen
- Vergiss nicht das `break`!
- Funktioniert mit int, char, String, enum

**Ternärer Operator:**
- Kurze Alternative für einfache if-else
- `(bedingung) ? wennTrue : wennFalse`

**Best Practices:**
- Lesbare Bedingungen schreiben
- Guard Clauses verwenden
- Richtige String-Vergleiche mit `.equals()`

---

## 🚀 Weiter geht's!

Im nächsten Kapitel lernst du **Schleifen** - wie dein Programm Aufgaben wiederholt!
