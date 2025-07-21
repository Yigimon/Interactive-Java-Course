# Kapitel 8: Objektorientierte Programmierung (OOP) in Java - Theorie

## 🎯 Lernziele
Nach diesem Kapitel kannst du:
- Klassen und Objekte erstellen
- Attribute (Eigenschaften) und Methoden definieren
- Konstruktoren verwenden
- Kapselung mit private/public verstehen
- Getter und Setter implementieren
- Die Grundprinzipien der OOP anwenden

## 📚 Was ist Objektorientierte Programmierung?

**OOP** ist wie das **Bauen mit Bausteinen** - statt alles in eine große `main`-Methode zu schreiben, erstellst du **Klassen** (Baupläne) und **Objekte** (konkrete Bausteine).

```java
// Ohne OOP: Alles in main (unübersichtlich)
public static void main(String[] args) {
    String schülerName = "Max";
    int schülerAlter = 16;
    double schülerNote = 2.1;
    
    String lehrerName = "Frau Müller";
    int lehrerAlter = 35;
    String lehrerFach = "Mathematik";
    
    // Viel Code für verschiedene Personen...
}

// Mit OOP: Organisiert in Klassen
class Schüler {
    String name;
    int alter;
    double note;
}

class Lehrer {
    String name;
    int alter;
    String fach;
}
```

**Die 4 Grundprinzipien der OOP:**
1. 📦 **Kapselung** - Daten verstecken und schützen
2. 🧬 **Vererbung** - Eigenschaften weitergeben
3. 🎭 **Polymorphismus** - Verschiedene Formen
4. 🎯 **Abstraktion** - Komplexität verstecken

## 🏗️ 1. Klassen und Objekte

### 1.1 Was ist eine Klasse?
Eine **Klasse** ist ein **Bauplan** für Objekte. Sie definiert:
- **Attribute** (Eigenschaften) - was ein Objekt "hat"
- **Methoden** (Verhalten) - was ein Objekt "kann"

```java
// Klasse = Bauplan für einen Schüler
public class Schüler {
    // Attribute (Eigenschaften)
    String name;
    int alter;
    String klasse;
    double durchschnittsnote;
    
    // Methoden (Verhalten)
    public void stelleDichVor() {
        System.out.println("Hi, ich bin " + name + " und " + alter + " Jahre alt!");
    }
    
    public void geheInKlasse() {
        System.out.println(name + " geht in die Klasse " + klasse);
    }
}
```

### 1.2 Was ist ein Objekt?
Ein **Objekt** ist eine **konkrete Instanz** einer Klasse:

```java
// Objekte erstellen (Instanziierung)
Schüler max = new Schüler();
Schüler anna = new Schüler();
Schüler tom = new Schüler();

// Jedes Objekt hat eigene Werte
max.name = "Max Mustermann";
max.alter = 16;
max.klasse = "10a";

anna.name = "Anna Schmidt";
anna.alter = 15;
anna.klasse = "10b";

// Methoden aufrufen
max.stelleDichVor();   // Hi, ich bin Max Mustermann und 16 Jahre alt!
anna.stelleDichVor();  // Hi, ich bin Anna Schmidt und 15 Jahre alt!
```

## 🏠 2. Konstruktoren

**Konstruktoren** sind spezielle Methoden, die beim Erstellen von Objekten aufgerufen werden:

### 2.1 Standard-Konstruktor
```java
public class Auto {
    String marke;
    String farbe;
    int baujahr;
    
    // Standard-Konstruktor (ohne Parameter)
    public Auto() {
        marke = "Unbekannt";
        farbe = "Weiß";
        baujahr = 2023;
    }
}

// Verwendung:
Auto meinAuto = new Auto();  // Konstruktor wird automatisch aufgerufen
System.out.println(meinAuto.marke);  // "Unbekannt"
```

### 2.2 Parametrisierter Konstruktor
```java
public class Auto {
    String marke;
    String farbe;
    int baujahr;
    
    // Konstruktor mit Parametern
    public Auto(String marke, String farbe, int baujahr) {
        this.marke = marke;     // "this" unterscheidet Parameter von Attribut
        this.farbe = farbe;
        this.baujahr = baujahr;
    }
    
    public void zeigeInfos() {
        System.out.println(marke + " (" + farbe + ", " + baujahr + ")");
    }
}

// Verwendung:
Auto bmw = new Auto("BMW", "Blau", 2022);
Auto audi = new Auto("Audi", "Rot", 2023);

bmw.zeigeInfos();   // BMW (Blau, 2022)
audi.zeigeInfos();  // Audi (Rot, 2023)
```

### 2.3 Mehrere Konstruktoren (Überladung)
```java
public class Rechteck {
    double länge;
    double breite;
    
    // Konstruktor 1: Ohne Parameter (Einheitsquadrat)
    public Rechteck() {
        this.länge = 1.0;
        this.breite = 1.0;
    }
    
    // Konstruktor 2: Quadrat (eine Seitenlänge)
    public Rechteck(double seite) {
        this.länge = seite;
        this.breite = seite;
    }
    
    // Konstruktor 3: Rechteck (verschiedene Seiten)
    public Rechteck(double länge, double breite) {
        this.länge = länge;
        this.breite = breite;
    }
    
    public double berechneFlaeche() {
        return länge * breite;
    }
}

// Verschiedene Objekte erstellen:
Rechteck einheitsquadrat = new Rechteck();           // 1x1
Rechteck quadrat = new Rechteck(5.0);                // 5x5
Rechteck rechteck = new Rechteck(4.0, 6.0);          // 4x6
```

## 🔒 3. Kapselung (Encapsulation)

**Kapselung** bedeutet, dass du Daten **schützt** und nur kontrollierten Zugriff erlaubst:

### 3.1 Private Attribute
```java
public class BankKonto {
    private String kontoinhaber;  // private = nur innerhalb der Klasse zugreifbar
    private double kontostand;
    private String pin;
    
    public BankKonto(String kontoinhaber, String pin) {
        this.kontoinhaber = kontoinhaber;
        this.pin = pin;
        this.kontostand = 0.0;
    }
    
    // Kontrollierte Zugriffsmethoden
    public void einzahlen(double betrag) {
        if (betrag > 0) {
            kontostand += betrag;
            System.out.println("Eingezahlt: " + betrag + "€");
        } else {
            System.out.println("Betrag muss positiv sein!");
        }
    }
    
    public boolean abheben(double betrag, String eingabePin) {
        if (!pin.equals(eingabePin)) {
            System.out.println("Falsche PIN!");
            return false;
        }
        
        if (betrag > kontostand) {
            System.out.println("Nicht genug Geld!");
            return false;
        }
        
        kontostand -= betrag;
        System.out.println("Abgehoben: " + betrag + "€");
        return true;
    }
}

// Verwendung:
BankKonto konto = new BankKonto("Max Mustermann", "1234");
konto.einzahlen(100.0);
konto.abheben(50.0, "1234");  // Funktioniert
konto.abheben(30.0, "9999");  // Falsche PIN!

// konto.kontostand = 1000000;  // FEHLER! Private Attribute nicht direkt zugreifbar
```

### 3.2 Getter und Setter
```java
public class Person {
    private String name;
    private int alter;
    private String email;
    
    public Person(String name, int alter) {
        this.name = name;
        setAlter(alter);  // Setter für Validierung nutzen
    }
    
    // Getter: Werte lesen
    public String getName() {
        return name;
    }
    
    public int getAlter() {
        return alter;
    }
    
    public String getEmail() {
        return email;
    }
    
    // Setter: Werte schreiben (mit Validierung)
    public void setName(String name) {
        if (name != null && !name.trim().isEmpty()) {
            this.name = name;
        } else {
            System.out.println("Name darf nicht leer sein!");
        }
    }
    
    public void setAlter(int alter) {
        if (alter >= 0 && alter <= 150) {
            this.alter = alter;
        } else {
            System.out.println("Alter muss zwischen 0 und 150 liegen!");
        }
    }
    
    public void setEmail(String email) {
        if (email != null && email.contains("@")) {
            this.email = email;
        } else {
            System.out.println("Ungültige E-Mail-Adresse!");
        }
    }
}

// Verwendung:
Person person = new Person("Lisa", 16);
System.out.println(person.getName());  // Lisa
person.setEmail("lisa@example.com");
person.setAlter(200);  // Fehler: Alter muss zwischen 0 und 150 liegen!
```

## 🎯 4. Praktische Beispiele

### 4.1 Klasse: Spielcharakter
```java
public class Spielcharakter {
    private String name;
    private int leben;
    private int maxLeben;
    private int angriff;
    private int verteidigung;
    private int level;
    
    public Spielcharakter(String name) {
        this.name = name;
        this.level = 1;
        this.maxLeben = 100;
        this.leben = maxLeben;
        this.angriff = 10;
        this.verteidigung = 5;
    }
    
    public void angreifen(Spielcharakter gegner) {
        int schaden = this.angriff - gegner.verteidigung;
        if (schaden <= 0) schaden = 1;  // Mindestens 1 Schaden
        
        gegner.schadenErleiden(schaden);
        System.out.println(this.name + " greift " + gegner.name + " an! Schaden: " + schaden);
    }
    
    public void schadenErleiden(int schaden) {
        this.leben -= schaden;
        if (this.leben < 0) this.leben = 0;
        
        if (this.leben == 0) {
            System.out.println(this.name + " wurde besiegt!");
        }
    }
    
    public void heilen(int heilung) {
        this.leben += heilung;
        if (this.leben > maxLeben) this.leben = maxLeben;
        System.out.println(this.name + " wurde um " + heilung + " geheilt!");
    }
    
    public void levelUp() {
        this.level++;
        this.maxLeben += 20;
        this.leben = maxLeben;  // Vollständige Heilung
        this.angriff += 5;
        this.verteidigung += 2;
        System.out.println(this.name + " ist jetzt Level " + this.level + "!");
    }
    
    public void zeigeStatus() {
        System.out.println("=== " + name + " ===");
        System.out.println("Level: " + level);
        System.out.println("Leben: " + leben + "/" + maxLeben);
        System.out.println("Angriff: " + angriff);
        System.out.println("Verteidigung: " + verteidigung);
    }
    
    // Getter
    public boolean istAmbLeben() {
        return leben > 0;
    }
    
    public String getName() {
        return name;
    }
}

// Verwendung:
Spielcharakter held = new Spielcharakter("Krieger Max");
Spielcharakter gegner = new Spielcharakter("Ork Grunk");

held.zeigeStatus();
gegner.zeigeStatus();

held.angreifen(gegner);
gegner.angreifen(held);

held.levelUp();
held.heilen(10);
```

### 4.2 Klasse: Bibliotheksbuch
```java
public class Buch {
    private String titel;
    private String autor;
    private String isbn;
    private boolean istAusgeliehen;
    private String ausleiher;
    private java.time.LocalDate ausleihdatum;
    
    public Buch(String titel, String autor, String isbn) {
        this.titel = titel;
        this.autor = autor;
        this.isbn = isbn;
        this.istAusgeliehen = false;
    }
    
    public boolean ausleihen(String person) {
        if (istAusgeliehen) {
            System.out.println("Buch ist bereits ausgeliehen von: " + ausleiher);
            return false;
        }
        
        this.istAusgeliehen = true;
        this.ausleiher = person;
        this.ausleihdatum = java.time.LocalDate.now();
        System.out.println("'" + titel + "' wurde an " + person + " ausgeliehen.");
        return true;
    }
    
    public boolean zurückgeben() {
        if (!istAusgeliehen) {
            System.out.println("Buch war gar nicht ausgeliehen!");
            return false;
        }
        
        System.out.println("'" + titel + "' wurde von " + ausleiher + " zurückgegeben.");
        this.istAusgeliehen = false;
        this.ausleiher = null;
        this.ausleihdatum = null;
        return true;
    }
    
    public void zeigeInfo() {
        System.out.println("=== Buchinfo ===");
        System.out.println("Titel: " + titel);
        System.out.println("Autor: " + autor);
        System.out.println("ISBN: " + isbn);
        
        if (istAusgeliehen) {
            System.out.println("Status: Ausgeliehen an " + ausleiher);
            System.out.println("Seit: " + ausleihdatum);
        } else {
            System.out.println("Status: Verfügbar");
        }
    }
    
    // Getter
    public String getTitel() { return titel; }
    public String getAutor() { return autor; }
    public boolean istVerfügbar() { return !istAusgeliehen; }
}

// Verwendung:
Buch buch1 = new Buch("Java ist auch eine Insel", "Christian Ullenboom", "978-3836258951");
Buch buch2 = new Buch("Clean Code", "Robert C. Martin", "978-0132350884");

buch1.ausleihen("Max Mustermann");
buch1.zeigeInfo();

buch2.ausleihen("Anna Schmidt");
buch1.ausleihen("Tom Meyer");  // Bereits ausgeliehen!

buch1.zurückgeben();
buch1.ausleihen("Tom Meyer");  // Jetzt funktioniert es
```

## 🎲 5. Statische vs. Instanz-Elemente

### 5.1 Statische Elemente (gehören zur Klasse)
```java
public class Mathematik {
    // Statische Konstante
    public static final double PI = 3.14159;
    
    // Statische Variable (für alle Objekte gleich)
    private static int anzahlBerechnungen = 0;
    
    // Statische Methode
    public static double kreisFlaeche(double radius) {
        anzahlBerechnungen++;  // Zähler erhöhen
        return PI * radius * radius;
    }
    
    public static int getAnzahlBerechnungen() {
        return anzahlBerechnungen;
    }
    
    // Instanz-Methode (braucht Objekt)
    public void zeigeInfo() {
        System.out.println("Mathematik-Klasse mit " + anzahlBerechnungen + " Berechnungen");
    }
}

// Verwendung:
// Statische Methoden direkt über Klasse aufrufen
double flaeche = Mathematik.kreisFlaeche(5.0);
System.out.println("Anzahl Berechnungen: " + Mathematik.getAnzahlBerechnungen());

// Für Instanz-Methoden Objekt erstellen
Mathematik math = new Mathematik();
math.zeigeInfo();
```

### 5.2 Wann static verwenden?
```java
// GUT für static: Hilfsmethoden, die kein Objekt brauchen
public class StringHelfer {
    public static String umkehren(String text) {
        // Braucht kein Objekt-Zustand
        return new StringBuilder(text).reverse().toString();
    }
    
    public static int zähleZeichen(String text, char zeichen) {
        // Arbeitet nur mit Parametern
        int anzahl = 0;
        for (char c : text.toCharArray()) {
            if (c == zeichen) anzahl++;
        }
        return anzahl;
    }
}

// SCHLECHT für static: Methoden, die Objekt-Zustand brauchen
public class Auto {
    private String marke;
    private int geschwindigkeit;
    
    // RICHTIG: Instanz-Methode
    public void beschleunigen() {
        this.geschwindigkeit += 10;  // Braucht Objekt-Zustand
    }
    
    // FALSCH: Kann nicht static sein
    // public static void beschleunigen() {
    //     this.geschwindigkeit += 10;  // FEHLER! this in static-Methode
    // }
}
```

## 🏆 6. Best Practices für OOP

### 6.1 Klassen-Design
```java
// GUT: Klare Verantwortlichkeiten
public class EmailValidator {
    public boolean istGültig(String email) {
        return email != null && email.contains("@") && email.contains(".");
    }
}

public class Person {
    private String name;
    private String email;
    private EmailValidator validator = new EmailValidator();
    
    public void setEmail(String email) {
        if (validator.istGültig(email)) {
            this.email = email;
        } else {
            throw new IllegalArgumentException("Ungültige E-Mail!");
        }
    }
}

// SCHLECHT: Alles in einer Klasse
public class AllesInEinem {
    private String name;
    private String email;
    
    public void setEmail(String email) {
        // E-Mail-Validierung
        // Datenbank-Speicherung
        // E-Mail senden
        // Logging
        // ... zu viele Verantwortlichkeiten!
    }
}
```

### 6.2 Datenkapselung
```java
// GUT: Private Daten, öffentliche Schnittstelle
public class TemperaturSensor {
    private double temperatur;
    private boolean istAktiv;
    
    public double getTemperaturCelsius() {
        if (!istAktiv) {
            throw new IllegalStateException("Sensor ist nicht aktiv!");
        }
        return temperatur;
    }
    
    public double getTemperaturFahrenheit() {
        return getTemperaturCelsius() * 9.0 / 5.0 + 32.0;
    }
    
    public void aktivieren() {
        this.istAktiv = true;
        this.temperatur = messeTemperatur();  // Private Hilfsmethode
    }
    
    private double messeTemperatur() {
        // Simulation einer Messung
        return 20.0 + Math.random() * 10.0;
    }
}

// SCHLECHT: Alles öffentlich
public class SchlechterSensor {
    public double temperatur;    // Direkt änderbar!
    public boolean istAktiv;     // Keine Kontrolle!
    
    // Jeder kann alles direkt ändern - keine Kontrolle!
}
```

## 🎮 7. Übungsaufgaben

### Aufgabe 1: Grundlagen
- Erstelle eine `Fahrzeug`-Klasse mit Attributen und Methoden
- Implementiere eine `Taschenrechner`-Klasse mit den Grundrechenarten
- Erstelle eine `Datum`-Klasse für Tag, Monat, Jahr

### Aufgabe 2: Kapselung
- Entwickle eine `Passwort`-Klasse mit Validierung
- Implementiere eine `GeheimZahl`-Klasse für ein Ratespiel
- Erstelle eine `Notenverwaltung`-Klasse für einen Schüler

### Aufgabe 3: Praktische Anwendungen
- Programmiere eine `Bibliothek`-Klasse mit mehreren Büchern
- Erstelle ein `Bankkonto`-System mit verschiedenen Kontotypen
- Entwickle eine `Spielkarte`-Klasse und ein `Kartendeck`

### Aufgabe 4: Komplexe Systeme
- Baue ein `Schul`-System mit Schülern, Lehrern und Klassen
- Implementiere ein `Onlineshop`-System mit Produkten und Warenkorb
- Erstelle ein `Hotel`-Reservierungssystem

### Aufgabe 5: Design-Herausforderung
- Entwirf eine `Spiel`-Engine mit verschiedenen Charaktertypen
- Implementiere ein `Social Media`-System mit Posts und Benutzern
- Erstelle ein `Krankenhaus`-Verwaltungssystem

## 🏆 Zusammenfassung

**Klassen und Objekte:**
- Klasse = Bauplan, Objekt = konkrete Instanz
- `new` erstellt Objekte
- Jedes Objekt hat eigene Attributwerte

**Konstruktoren:**
- Spezielle Methoden für Objekt-Initialisierung
- Können überladen werden
- `this` unterscheidet Parameter von Attributen

**Kapselung:**
- `private` schützt Daten vor direktem Zugriff
- Getter/Setter für kontrollierten Zugriff
- Validierung in Setter-Methoden

**Static vs. Instanz:**
- `static` gehört zur Klasse, nicht zum Objekt
- Hilfsmethoden oft static
- Instanz-Methoden für Objekt-spezifisches Verhalten

**Best Practices:**
- Klare Verantwortlichkeiten
- Daten kapseln
- Aussagekräftige Namen
- Validation implementieren

**Die OOP hilft dir:**
- 📊 Code zu organisieren
- 🔒 Daten zu schützen
- 🔄 Code wiederzuverwenden
- 🛠️ Wartbaren Code zu schreiben

---

## 🚀 Glückwunsch!

Du hast alle Grundlagen der Java-Programmierung gelernt! Jetzt kannst du:
- Programme strukturieren
- Daten verwalten
- Benutzerinteraktion implementieren
- Objektorientiert programmieren

**Nächste Schritte:** Vertiefen, üben und eigene Projekte starten! 🎯
