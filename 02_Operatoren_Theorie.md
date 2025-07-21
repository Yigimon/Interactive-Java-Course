# Kapitel 2: Operatoren in Java - Theorie

## 🎯 Lernziele
Nach diesem Kapitel kannst du:
- Verschiedene Operatortypen in Java unterscheiden und anwenden
- Arithmetische Berechnungen durchführen
- Vergleiche zwischen Werten erstellen
- Logische Verknüpfungen verstehen und nutzen
- Die Operator-Prioritäten beachten

## 📚 Was sind Operatoren?

Operatoren sind spezielle Symbole, die dem Computer sagen, welche **Operationen** er mit Werten durchführen soll. Stell dir vor, Operatoren sind wie mathematische Zeichen (+, -, *, /) - nur gibt es in Java noch viele mehr!

## 🔢 1. Arithmetische Operatoren

Diese Operatoren kennst du bereits aus der Mathematik:

| Operator | Name | Beispiel | Ergebnis |
|----------|------|----------|----------|
| `+` | Addition | `5 + 3` | `8` |
| `-` | Subtraktion | `5 - 3` | `2` |
| `*` | Multiplikation | `5 * 3` | `15` |
| `/` | Division | `15 / 3` | `5` |
| `%` | Modulo (Rest) | `15 % 4` | `3` |

### 🔍 Besonderheit: Der Modulo-Operator (%)
Der Modulo-Operator gibt den **Rest** einer Division zurück:
- `10 % 3 = 1` (10 geteilt durch 3 ist 3, Rest 1)
- `8 % 2 = 0` (8 geteilt durch 2 ist 4, Rest 0)

**Praktischer Nutzen:** Prüfung auf gerade/ungerade Zahlen!

```java
int zahl = 7;
if (zahl % 2 == 0) {
    System.out.println("Gerade Zahl");
} else {
    System.out.println("Ungerade Zahl");
}
```

## 📊 2. Vergleichsoperatoren

Diese Operatoren vergleichen zwei Werte und geben `true` oder `false` zurück:

| Operator | Name | Beispiel | Ergebnis |
|----------|------|----------|----------|
| `==` | Gleich | `5 == 5` | `true` |
| `!=` | Ungleich | `5 != 3` | `true` |
| `>` | Größer als | `5 > 3` | `true` |
| `<` | Kleiner als | `3 < 5` | `true` |
| `>=` | Größer oder gleich | `5 >= 5` | `true` |
| `<=` | Kleiner oder gleich | `3 <= 5` | `true` |

### ⚠️ Wichtiger Hinweis: == vs =
- `=` ist die **Zuweisung**: `int x = 5;` (x bekommt den Wert 5)
- `==` ist der **Vergleich**: `x == 5` (ist x gleich 5?)

## 🧠 3. Logische Operatoren

Logische Operatoren verknüpfen `boolean`-Werte:

| Operator | Name | Beispiel | Ergebnis |
|----------|------|----------|----------|
| `&&` | UND (AND) | `true && false` | `false` |
| `\|\|` | ODER (OR) | `true \|\| false` | `true` |
| `!` | NICHT (NOT) | `!true` | `false` |

### 🔍 Wahrheitstabellen:

**UND (&&):** Beide Bedingungen müssen wahr sein
| A | B | A && B |
|---|---|--------|
| true | true | true |
| true | false | false |
| false | true | false |
| false | false | false |

**ODER (||):** Mindestens eine Bedingung muss wahr sein
| A | B | A \|\| B |
|---|---|----------|
| true | true | true |
| true | false | true |
| false | true | true |
| false | false | false |

## 🔄 4. Zuweisungsoperatoren

### Einfache Zuweisung
```java
int x = 10;  // x bekommt den Wert 10
```

### Kombinierte Zuweisungsoperatoren
| Operator | Langform | Kurzform |
|----------|----------|----------|
| `+=` | `x = x + 5` | `x += 5` |
| `-=` | `x = x - 3` | `x -= 3` |
| `*=` | `x = x * 2` | `x *= 2` |
| `/=` | `x = x / 4` | `x /= 4` |
| `%=` | `x = x % 3` | `x %= 3` |

## ⬆️⬇️ 5. Inkrement- und Dekrement-Operatoren

| Operator | Name | Wirkung |
|----------|------|---------|
| `++` | Inkrement | Erhöht um 1 |
| `--` | Dekrement | Verringert um 1 |

### Unterschied: Präfix vs. Postfix
```java
int x = 5;
int y = ++x;  // Präfix: x wird ERST erhöht, DANN zugewiesen → x=6, y=6
int z = x++;  // Postfix: x wird ERST zugewiesen, DANN erhöht → z=6, x=7
```

## 🎯 6. Operator-Prioritäten (Reihenfolge)

Wie in der Mathematik gibt es auch in Java eine **Reihenfolge**, in der Operatoren ausgewertet werden:

1. **Klammern** `()`
2. **Inkrement/Dekrement** `++`, `--`
3. **Multiplikation, Division, Modulo** `*`, `/`, `%`
4. **Addition, Subtraktion** `+`, `-`
5. **Vergleichsoperatoren** `<`, `>`, `<=`, `>=`
6. **Gleichheit** `==`, `!=`
7. **Logisches UND** `&&`
8. **Logisches ODER** `||`
9. **Zuweisung** `=`, `+=`, `-=`, etc.

### Beispiel:
```java
int ergebnis = 2 + 3 * 4;  // = 2 + 12 = 14 (nicht 20!)
int ergebnis2 = (2 + 3) * 4;  // = 5 * 4 = 20
```

## 🔍 7. String-Verkettung mit +

Bei Strings funktioniert der `+`-Operator anders:

```java
String vorname = "Max";
String nachname = "Mustermann";
String vollname = vorname + " " + nachname;  // "Max Mustermann"

int alter = 25;
String text = "Ich bin " + alter + " Jahre alt";  // "Ich bin 25 Jahre alt"
```

## ⚠️ 8. Häufige Fehler

### 1. Verwechslung von = und ==
```java
// FALSCH:
if (alter = 18) { ... }  // Zuweisung statt Vergleich!

// RICHTIG:
if (alter == 18) { ... }  // Vergleich
```

### 2. Division durch Null
```java
int a = 10;
int b = 0;
int ergebnis = a / b;  // Fehler: ArithmeticException!
```

### 3. Ganzzahl-Division
```java
int ergebnis = 5 / 2;  // = 2 (nicht 2.5!)
double ergebnis = 5.0 / 2;  // = 2.5
```

### 4. Falsche Operator-Priorität
```java
// Gewollt: Prüfung ob x zwischen 1 und 10 liegt
// FALSCH:
if (1 <= x <= 10) { ... }  // Syntaxfehler!

// RICHTIG:
if (x >= 1 && x <= 10) { ... }
```

## 💡 9. Praktische Anwendungen

### Temperatur-Umrechnung
```java
double celsius = 25.0;
double fahrenheit = celsius * 9.0 / 5.0 + 32;  // 77.0°F
```

### Gerade/Ungerade prüfen
```java
int zahl = 42;
boolean istGerade = (zahl % 2 == 0);  // true
```

### Bereich prüfen
```java
int note = 85;
boolean istBestanden = (note >= 50 && note <= 100);  // true
```

## 🎮 10. Übungsaufgaben

### Aufgabe 1: Taschenrechner
Erstelle Variablen für zwei Zahlen und berechne:
- Summe
- Differenz  
- Produkt
- Quotient
- Rest bei Division

### Aufgabe 2: Notenbewertung
Eine Note zwischen 1-15 Punkten ist gegeben. Prüfe:
- Ist es eine gültige Note? (1-15)
- Ist es eine ausreichende Note? (≥5)
- Ist es eine sehr gute Note? (≥13)

### Aufgabe 3: Schaltjahr-Prüfung
Ein Jahr ist ein Schaltjahr, wenn:
- Es durch 4 teilbar ist UND
- Es nicht durch 100 teilbar ist ODER es durch 400 teilbar ist

### Aufgabe 4: Login-System
Simuliere eine Login-Prüfung mit:
- Benutzername muss "admin" sein
- Passwort muss "geheim123" sein
- Beide Bedingungen müssen erfüllt sein

## 🏆 Zusammenfassung

Operatoren sind das **Werkzeug**, um mit Daten zu arbeiten:
- **Arithmetische Operatoren** für Berechnungen
- **Vergleichsoperatoren** für Bedingungen
- **Logische Operatoren** für komplexe Bedingungen
- **Zuweisungsoperatoren** für effiziente Werteänderungen

Die **Operator-Priorität** ist wichtig - im Zweifel Klammern setzen!

---

## 🚀 Weiter geht's!

Im nächsten Kapitel lernst du **Ein- und Ausgabe** - wie dein Programm mit dem Benutzer kommuniziert!
