# 📊 Java Datentypen - Theorie für Anfänger

## 🤔 Was sind Datentypen?

Stellen Sie sich vor, Sie haben verschiedene Behälter:
- 📦 **Kleine Schachtel** für einzelne Buchstaben
- 🗃️ **Ordner** für ganze Zahlen  
- 💰 **Tresor** für Geld (mit Kommastellen)
- ✅ **Ja/Nein-Stempel** für Wahrheitswerte
- 📚 **Bücherregal** für längere Texte

Genauso funktionieren **Datentypen** in Java - sie sagen dem Computer, welche Art von Information in einer Variable gespeichert wird.

## 🔢 Ganze Zahlen (Integer-Typen)

### `byte` - Der kleinste Behälter
- **Speichert**: Zahlen von -128 bis +127
- **Wann verwenden**: Sehr kleine Zahlen, um Speicher zu sparen
- **Beispiele**: Alter (0-120), Monat (1-12), Schulnoten (1-6)

```java
byte alter = 16;        // ✅ Passt
byte note = 2;          // ✅ Passt  
byte groesseInCm = 175; // ❌ Zu groß! (max. 127)
```

### `short` - Kleine Zahlen
- **Speichert**: Zahlen von -32.768 bis +32.767
- **Wann verwenden**: Mittlere Zahlen
- **Beispiele**: Jahr, Anzahl Schüler, Seitenzahl

```java
short jahr = 2025;           // ✅ Passt
short anzahlSchueler = 1200; // ✅ Passt
short weltbevoelkerung = 8000000000; // ❌ Viel zu groß!
```

### `int` - Standard für ganze Zahlen
- **Speichert**: Zahlen von ca. -2 Milliarden bis +2 Milliarden
- **Wann verwenden**: Meistens! Standard für ganze Zahlen
- **Beispiele**: Geld in Cent, Einwohnerzahl, Punkte im Spiel

```java
int punktestand = 1500;
int einwohner = 80000000;    // Deutschland
int geldInCent = 299;        // 2,99€ in Cent
```

### `long` - Sehr große Zahlen
- **Speichert**: Riesige Zahlen (19 Stellen!)
- **Wann verwenden**: Astronomie, Finanzen, Zeitstempel
- **Besonderheit**: Muss mit `L` am Ende geschrieben werden

```java
long weltbevoelkerung = 8000000000L;  // Das L ist wichtig!
long abstandZurSonne = 149600000000L; // km
long millisekundenSeit1970 = System.currentTimeMillis();
```

## 💰 Dezimalzahlen (Floating-Point-Typen)

### `float` - Einfache Genauigkeit
- **Speichert**: Zahlen mit ~7 Nachkommastellen
- **Wann verwenden**: Selten, meist reicht double
- **Besonderheit**: Muss mit `f` am Ende geschrieben werden

```java
float pi = 3.14159f;          // Das f ist wichtig!
float temperatur = 23.5f;
float preis = 19.99f;
```

### `double` - Standard für Dezimalzahlen
- **Speichert**: Zahlen mit ~15 Nachkommastellen
- **Wann verwenden**: Immer für Kommazahlen!
- **Beispiele**: Noten, Preise, Maße, wissenschaftliche Berechnungen

```java
double note = 2.3;
double preis = 49.99;
double pi = 3.141592653589793;
double körpergröße = 1.75;    // in Metern
```

## ✅ Wahrheitswerte (Boolean)

### `boolean` - Nur wahr oder falsch
- **Speichert**: Nur `true` oder `false`
- **Wann verwenden**: Ja/Nein-Entscheidungen, Zustände, Bedingungen
- **Beispiele**: Ist angemeldet? Hat bestanden? Ist Wochenende?

```java
boolean istSchueler = true;
boolean hatBestanden = false;
boolean istWochenende = false;
boolean istVolljährig = alter >= 18;  // Ergebnis einer Bedingung
```

## 📝 Zeichen und Text

### `char` - Einzelne Zeichen
- **Speichert**: Genau EIN Zeichen
- **Schreibweise**: In einfachen Anführungszeichen `'A'`
- **Beispiele**: Noten-Buchstaben, Initialen, Symbole

```java
char noteBuchstabe = 'A';
char initial = 'M';
char symbol = '★';
char leerzeichen = ' ';
char ziffer = '5';      // Das ist ein Zeichen, nicht die Zahl 5!
```

### `String` - Längere Texte
- **Speichert**: Beliebig lange Texte
- **Schreibweise**: In doppelten Anführungszeichen `"Text"`
- **Besonderheit**: Ist eigentlich eine Klasse, nicht ein primitiver Typ
- **Beispiele**: Namen, Adressen, Nachrichten

```java
String name = "Max Mustermann";
String adresse = "Musterstraße 123, 12345 Musterstadt";
String nachricht = "Hallo Welt!";
String leerString = "";           // Leerer Text
String einZeichen = "A";          // Auch möglich, aber char wäre besser
```

## 🔄 Typumwandlungen (Casting)

### Automatische Umwandlung (Implicit Casting)
Java wandelt automatisch von "kleinen" zu "großen" Typen um:

```java
byte → short → int → long → float → double

byte b = 42;
int i = b;        // ✅ Automatisch: byte → int
double d = i;     // ✅ Automatisch: int → double
```

### Explizite Umwandlung (Explicit Casting)
Für "große" zu "kleine" Typen müssen wir explizit umwandeln:

```java
double d = 3.7;
int i = (int) d;        // ✅ Explizit: double → int (wird zu 3!)
char c = (char) 65;     // ✅ Wird zu 'A'

// ACHTUNG: Datenverlust möglich!
int groß = 1000;
byte klein = (byte) groß;  // ❌ Datenverlust! (1000 passt nicht in byte)
```

### String-Umwandlungen
```java
// String zu Zahl
String text = "123";
int zahl = Integer.parseInt(text);       // String → int
double kommaZahl = Double.parseDouble("3.14"); // String → double

// Zahl zu String
int alter = 16;
String alterText = String.valueOf(alter);      // int → String
String alterText2 = Integer.toString(alter);   // Alternative
String alterText3 = "" + alter;                // Trick mit Konkatenation
```

## 💾 Speicherverbrauch

| Typ | Bytes | Bits | Wertebereich |
|-----|-------|------|--------------|
| `byte` | 1 | 8 | -128 bis 127 |
| `short` | 2 | 16 | -32.768 bis 32.767 |
| `int` | 4 | 32 | -2.147.483.648 bis 2.147.483.647 |
| `long` | 8 | 64 | -9.223.372.036.854.775.808 bis 9.223.372.036.854.775.807 |
| `float` | 4 | 32 | ±1.4E-45 bis ±3.4028235E38 |
| `double` | 8 | 64 | ±4.9E-324 bis ±1.7976931348623157E308 |
| `char` | 2 | 16 | 0 bis 65.535 (Unicode) |
| `boolean` | 1 | 8 | true oder false |

## 🎯 Welchen Typ wann verwenden?

### 🎮 **Alltägliche Programmierung:**
- **`int`** für ganze Zahlen (Alter, Punkte, Anzahlen)
- **`double`** für Dezimalzahlen (Preise, Noten, Maße)
- **`boolean`** für Ja/Nein-Entscheidungen
- **`String`** für alle Texte
- **`char`** nur für einzelne Zeichen

### 📊 **Besondere Fälle:**
- **`byte`** bei sehr vielen kleinen Zahlen (Speicher sparen)
- **`long`** für sehr große Zahlen (Zeitstempel, Astronomie)
- **`float`** fast nie (double ist besser)

### ✅ **Faustregel für Anfänger:**
- Ganze Zahl? → **`int`**
- Kommazahl? → **`double`**
- Wahr/Falsch? → **`boolean`**  
- Text? → **`String`**
- Einzelnes Zeichen? → **`char`**

## ⚠️ Häufige Anfängerfehler

### 1. Vergessene Suffixe
```java
long groß = 9000000000;   // ❌ Fehler! Zu groß für int
long groß = 9000000000L;  // ✅ Korrekt mit L

float f = 3.14;           // ❌ Fehler! 3.14 ist double
float f = 3.14f;          // ✅ Korrekt mit f
```

### 2. Char vs. String verwechseln
```java
char c = "A";             // ❌ Falsche Anführungszeichen
char c = 'A';             // ✅ Einfache Anführungszeichen

String s = 'Text';        // ❌ Falsche Anführungszeichen  
String s = "Text";        // ✅ Doppelte Anführungszeichen
```

### 3. Integer-Division vergessen
```java
int a = 5;
int b = 2;
double ergebnis = a / b;  // ❌ Ergebnis ist 2.0, nicht 2.5!

double ergebnis = (double) a / b;  // ✅ Ergebnis ist 2.5
double ergebnis = a / (double) b;  // ✅ Alternative
double ergebnis = a / 2.0;         // ✅ Trick mit 2.0 statt 2
```

### 4. Überlauf ignorieren
```java
byte max = 127;
max = max + 1;            // ❌ Überlauf! Wird zu -128
```

## 🎯 Übungsvorschläge

1. **Deklarieren Sie Variablen** für Ihre persönlichen Daten (passende Typen wählen!)
2. **Experimentieren Sie** mit Typumwandlungen
3. **Testen Sie Grenzen** - was passiert bei Überlauf?
4. **String-Operationen** - Namen zusammensetzen
5. **Boolean-Logik** - Bedingungen formulieren

---

*Jetzt sind Sie bereit für das praktische Experimentieren im Jupyter Notebook! 🚀*
