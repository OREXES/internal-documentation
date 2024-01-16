---
title: "1. Einstieg"
description: "Einführung in die SAP-Entwicklung"
summary: ""
date: 2023-09-07T16:04:48+02:00
lastmod: 2023-09-07T16:04:48+02:00
draft: false
menu:
  docs:
    parent: ""
    identifier: "example-6a1a6be4373e933280d78ea53de6158e"
weight: 810
toc: true
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
---

## 1.1 Was ist SAP?
### Definition
SAP ist ein **ERP** (**Enterprise Resource Planning**) -Softwaresystem. SAP unterstützt Unternehmen im zentralen Datenmanagement in diversen Unternehmensbereichen, wie Finanzen, Personalwesen, Fertigung, Lieferkette, Services, Beschaffung und mehr. Dabei werden die Unternehmensbereiche miteinander verbunden und zentral gesteuert. Somit bieten sich Möglichkeiten die betrieblichen Prozesse des Unternehmens intelligenter, schneller und effizienter zu gestalten. Neben den bereitgestellten SAP-Standardprogrammen können auch eigenen Programme zur Unterstützung von betrieblichen Prozessen in der SAP-eigenen Programmiersprache ABAP geschrieben werden.

### Geschichte und Enwicklung von SAP
Am 1. April 1972 wurde SAP unter der Abkürzung für „Systemanalyse und Programmentwicklung“ gegründet. Die erste Software SAP R/1 enthielt zunächst das Modul zur Finanzbuchhaltung. Nach und nach wurden mehr betriebliche Aufgaben von der Software unterstützt wie Auftragseingang, Materialbedarfsplanung und Rechnungsstellung. Schon damals wurde SAP als Standartsoftware verkauft, die von Partnern an die Bedürfnisse ihrer Kunden angepasst werden soll.

1982 folgte die Versionen SAP R/2 und SAP R/3 ab 1992, welche auf weitere neuere Hardware betrieben werden konnten und sich in ihrer Architektur unterscheiden.

SAP R/1 besteht aus einer 1-Tier Architektur, bei der die Präsentation, Logik und Anwendung auf einem einzigen Server laufen. SAP R/2 hingegen trennt die Präsentationsschicht von der Datenbank und Logik in einer 2-Tier Architektur. Bei SAP R/3 wurde das Client-Server-Modell durch 3 Schichten (Präsentationsschicht, Anwendungsschicht und Datenhaltungsschicht) umgesetzt, die jeweils auf eigenen Server laufen.

Die Darauffolgende Lösung SAP ERP/ ECC wurde durch SAP S/4HANA ab 2015 abgelöst. SAP S/4HANA basiert auf der performanten und leistungsstarken HANA-Datenbank. SAP Fiori und die Cloudedition der SAP S/4HANA werden folgend veröffentlicht und bieten mehr Flexibilität durch On-Premise- und Cloudlösungen.

### SAP Module und ihre Funktion
SAP ist in sogenannte Module untergliedert, die die verschiedenen Geschäftsbereiche eines Unternehmens abbilden. Einige Kernmodule sind:
·       **SAP Foundation Modul**
	Dieses Modul bietet einen allgemeinen Überblick
·       **CO**
	Beim _Controlling_ handgelt es sich um die Planung und Überwachung von Kosten.
·       **FI**
	Das _Financial Accounting_ beschäftigt sich mit Finanzberichterstattung und Buchhaltung.
·       **MM**
	Das _Materials Management_ beinhaltet die Planung, Steuerung und Optimierung der Materialflüsse eines Unternehmens.
·       **SD**
	In dem Modul _Sales and Distribution_ wird der Vertrieb von der Erstellung von Anfragen und Angeboten bis hin zum Versand und der Fakturierung abgebildet.
·       **PP**
	Das _Production Planning_ unterstützt die zeitliche und räumliche Planung der Produktion.
·       **HCM**
	Das _Human Capital Management_ umfasst die Personalwirtschaft.
·       **CRM**
	Mit dem _Customer-Relationship-Management_ können Kundendaten und kundenorientierten Aktivitäten automatisiert und integriert verarbeitet werden.

## 1.2 Hello World
### Einführung in das ABAP Entwicklungsumfeld
Das ABAP-Entwicklungsumgebung öffnet sich über den _Object Navigator_ mit der Transaktion SE80.
![Pasted image 20240109154156.png]]
w4ier können die Entwicklungsobjekte im _Repository Browser_ angelegt, geändert und angesehen werden.
![Pasted image 20240109154211.png]]
Das Objekt mit der höchsten Hierarchieebene ist das _Paket_. Ein _Paket_ dient der Sammlung zusammengehöriger Entwicklungen. Alle erstellen Objekte müssen mit dem Buchstaben Z beginnen, das ist der Namensraum, der außerhalb der SAP-Standardentwicklungen liegt. Als Beispiel, das Hauptpaket ZOM (kundeneigens erstellt) dient der Sammlung aller Entwicklungen des Organisationsmanagements.
![Pasted image 20240109154223.png]]

### Vorteile und Anwendungsbereiche von ABAP
ABAP ist die Primäre Anwendungs- und Erweiterungssprache die speziell für die Unterstützung der SAP-Prozesse entworfen wurde. Ein Großteil der Funktionen in SAP selbst sind in ABAP erstellt und können in eigenen ABAP-Programmen verwendet werden. ABAP bietet einfache, wiederverwendbare Datenstrukturen, eine interne Versionsverwaltung und gebündelte Transportaufträge zwischen den Systemen über den Application Server sowie die nützliche Vorwärtsnavigationsfunktion.

### Definition und Funktionen
Innerhalb eines Pakets können Entwicklungsobjekte wie Programme angelegt werden. Bei der Anlage eines einfachen Programmes muss der Programmtyp „Ausführbares Programm“ ausgewählt werden. Die Programme erhalten bei der Erstellung einen Befehl, welcher den Programmtyp angibt. Bei den Ausführbaren Programmen beginnt dieser mit REPORT und endet mit dem vergebenen Programmnamen.
```abap
REPORT z_vb_rep1.
```
Eine Ausgabe auf dem Bildschirm erfolgt über folgenden Befehl:
```abap
WRITE: 'Hello World'.
```
Der geschriebene Code kann mit der Tastenkombination `STRG + F2` auf Fehler überprüft, mit `STRG + F3` aktiviert und über `F8` oder jeweils die zugeordneten Buttons ausgeführt werden. Ein Programm kann nur im aktiviertem Zustand ausgeführt werden.

Mit einem `*` können Kommentare geschrieben werden, die keinen Einfluss auf die Programmlogik haben und der Beschreibung der Anweisungen dienen.
```abap
*dies ist ein Kommentar
```
Alternativ lassen sich Kommentare mit einem `"` beginnen und sind somit auch inline möglich.
```abap
"dies ist ein Kommentar
WRITE: 'Hello World'. "dies ist ein Inline-Kommentar
```

### Datentypen

Die SAP-Datentypen sind einem generischen Datentyp Data untergeordnet. Sie beschreiben die technische Eigenschaft eines Datenobjekts.
Die Datentypen werden unterschieden zwischen Elementare Typen, Referenztypen und Komplexe Datentypen.
1.     Elementare Typen
	Diese Datentypen sind nicht aus anderen Typen zusammengesetzt. Es gibt Elementare Typen mit fester und mit variabler Länge.
2.     Referenztypen
	Diese Datentypen beschreiben Datenobjekte, die Referenzen auf andere Datenobjekte oder Instanzen von Klassen enthalten.
3.     Komplexe Typen
	Diese Datentypen sind aus anderen Typen zusammengesetzt und werden zwischen folgende Arten unterschieden:
	·       Strukturierter Typ
		Folge beliebiger Datentypen zur Zusammenfassung logisch zusammenhängender Arbeitsbereiche.
	·       Tabellentypen
		Folge beliebiger Anzahl an Zeilen des gleichen Datentyps. Sie sind durch ihren Zeilentyp charakterisiert. Die Tabellenart bestimmt, wie der Zugriff auf die Tabelle erfolgt.
	·       Meshtypen
		Spezieller strukturierter Typ mit tabellarischen Inhalt, welche Assoziationen zueinander haben.
Hier eine Übersicht über SAP-[Datentypen](https://help.sap.com/doc/abapdocu_750_index_htm/7.50/de-de/abentypes_objects_oview.htm).

ABAP Datentypen

| **Datentyp** | **Beschreibung** |
| ---- | ---- |
| C | Text |
| N | Numerischer Text |
| T | Zeitangabe |
| D | Datum |
| F | Gleitpunktzahl |
| I | Ganze Zahl |
| P | Gepackte Zahl (Festkomma) |
| X | Hexadezimalzahl |


### Aufgaben
1.     Erstelle ein Paket mit dem Namen _Z_UEBUNG_VORNAME_NACHNAME_ und darin ein Ausführbares ABAP-Programm. Das Programm soll eine Bildschirmausgabe mit Hello World erzeugen.
2.     Welche Arten von Daten würden zu welchem Datentypen passen? Gibt es Welche die zu mehreren Datentypen zugeordnet werden könnten? Mache 3 Beispiele

## 1.3 Arithmetik und Logik
### Verständnis der arithmetischen und logischen Operatoren in ABAP
Zur Manipulation von Daten werden verschiedene Arten von Operatoren verwendet.
Es wird zwischen arithmetischen und logischen Operatoren unterschieden. Während die arithmetischen Operatoren für Berechnungen sind, nutzt man die logischen Operatoren zum Vergleichen von Werten.

**Sämtliche Operatoren tabellarisch** (bspw.: [hier](https://www.tutorialscampus.com/sap-abap/arithmetic-operators.htm))
Arithmetische Operatoren

| **Operator** | **Funktion** |
| ---- | ---- |
| + | Addition |
| - | Subtraktion |
| * | Multiplikation |
| / | Division |
| DIV | Division mit integer als Ergebnisse |
| MOD | Modulo Operation |
| ** | Potenz von der Basis (linker Operant) und dem Exponenten (rechter Operant) |
Logische Operatoren

| **Operator** | **Funktion** |
| ---- | ---- |
| = | Gleichheit |
| <> | Ungleichheit |
| < | Kleiner als |
| > | Größer als |
| <= | Kleiner oder gleich |
| >= | Größer oder gleich |
| BETWEEN | Prüfe ob Wert1 in Wert2 liegt |
| IS INITIAL | Prüfe, ob Variable nach Zuweisung geändert wurde |
| IS NOT INITIAL | Prüfe, ob Variable nach Zuweisung nicht geändert wurde |

### Aufgaben
1.     Erstelle für jeden Operator eine Ausgabe, in der dieser Operator zur Berechnung des Ergebnisses verwendet wurde.

## 1.4 Charakteroperationen in ABAP
Die Charakteroperationen liefern einen booleschen wert.
Charakteroperatoren

| **Operator** | **Funktion** |
| ---- | ---- |
| A CO B | A enthält nur B |
| A CN B | A enthält nicht nur B |
| A CA B | A enthält mindestens ein B |
| A NA B | A enthält kein B |
| A CS B | A enthält den gesamten B String |
| A NS B | A enthält nicht den gesamten B String |
| A CP B | A enthält das B Muster |
| A NP B | A enthält nicht das Muster von B |
-        **String Konkatenation** (bspw.: [hier](https://otremba.net/wiki/Stringoperationen_(ABAP)))
String teilen

String an bestimmter Position teilen
Der Wert von `lv_stringout` ist `lv_stringin` ab der Startposition `startpos`, die Anzahl der Zeichen ist `charlen`. Bei `stringpos` wird das 1. Zeichen als `Null` betrachtet.
```abap
lv_strout = lv_strin+lv_startpos(lv_charlen).
```
String an bestimmten Trennzeichen teilen
```abap
SPLIT lv_strin AT lv_trennzeichen INTO lv_teilstring1 lv_teilstring2.
```
String Konkatenieren
Folgende Anweisungen kombiniert einen String aus zwei Teilen.
```abap
CONCATENATE lv_str1 lv_str2 INTO lv_strout.
"oder
lv_strout = lv_str1 lv_str2.
```
Auch das Zusammensetzen mit Trennzeichen ist möglich:
```abap
CONCATENATE lv_str1 lv_str2

  INTO lv_strout

  SEPARATED BY SPACE.
```

-        **String Templates**

Der Text eines String Templates befindet sich innerhalb von Pipes.
```abap
lv_strtem = | Das ist ein Text |.
```
Mit & können Templates zusammengesetzt werden
```abap
lv_strtem = |Hello| & |World|.
```
Eine Variable wird in Klammern gesetzt.
```abap
lv_strtem = |{ lv_data }|.
```
Es können Funktionen innerhalb der Templates verwendet werden.
```abap
lv_strtem = |{ strlen( lv_variable )}|.
```
Das Ergebnis einer Methode ausgeben:
```abap
lv_strtem = |Ergebnis: { methode( ) }|.
```
### **Aufgaben**
1. Erzeuge eine Ausgabe, in der die ersten 3 Buchstaben des angemeldeten Benutzers mit dem aktuellen Monat und am Ende den Mandaten ermittelt und konkateniert werden. Im September würde bei dem Benutzer „MaxM“ im Mandaten 001 die Ausgabe also Max09001 lauten.
2. Informiere dich über weitere String Operationen (bspw. [hier](https://otremba.net/wiki/Stringoperationen_(ABAP)))
## 1.5 Strukturen und interne Tabellen (Simon)

### Strukturen und Strukturtypen
Strukturen und Strukturtypen setzen sich aus beliebigen Datentypen zusammen. Sie können statisch oder dynamisch sein.
Es gibt verschiedene Arten von Strukturen:

1.     Flache Strukturen
Flache Strukturen enthalten keine tiefen Komponenten. Sie enthalten nur Komponenten mit flachem Datentyp, also Elementartypen c, n, d, t, decfloat16, decfloat34, f, i, int8, p, x sowie b, s oder wiederum Strukturen mit diesen Typen.

2.     Flache Zeichenartige Strukturen
Es enthält nur Zeichenartige Komponenten. Zeichenartige Datenobjekte enthalten Zeichenketten (oder Zeichenfolgen). Ein zeichenartiges Datenobjekt hat entweder einen zeichenartigen Datentyp c, n, string, einen Datums-/Zeittyp d, t oder ist eine flache Struktur mit rein zeichenartigen Komponenten.

3.     Geschachtelte Strukturen
Sie enthalten mindestens eine Unterstruktur. Ob eine geschachtelte Struktur flach bzw. zeichenartig ist, richtet sich nach allen Komponenten.

4.     Tiefe Strukturen
sie enthalten mindestens eine tiefe Komponente (Strings, interne Tabellen, Daten- oder Objektreferenzen, Boxed Components).

Der Begriff "geschachtelte Struktur" darf nicht mit dem Begriff "tiefe Struktur" verwechselt werden. Eine geschachtelte Struktur ist flach, wenn sie nur flache Komponenten und Unterkomponenten enthält. Eine geschachtelte Struktur ist tief, wenn sie mindestens eine tiefe Komponente oder Unterkomponente enthält.
Ein Strukturtyp beschreibt die Eigenschaften einer Struktur. Der Strukturtyp wird bei der Erzeugung der Struktur angegeben.
### Interne Tabellen
Interne Tabellen sind temporär und existieren maximal so lange, das Programm läuft. Eine Interne Tabelle kann beliebig viele Spalten eines beliebigen Datentyps enthalten. Sie werden für die lokale Verwaltung von Datensätzen verwendet.

Es gibt drei Tabellenarten:

1. **Standardtabelle (Standard Table)**
	Zugriffsart: Linear

	Verwendung: Wenn der Zugriff auf die Tabelle normalerweise in der Reihenfolge der Einfügung erfolgt.

	Zugriff: Der Zugriff erfolgt über den Index, und die Suche wird linear durchgeführt.

	Beispiel: `DATA: lt_table TYPE STANDARD TABLE OF ty_structure.`

2. **Sortierte Tabelle (Sorted Table)**
	Zugriffsart: Binärer Suchalgorithmus

	Verwendung: Wenn die Tabelle nach einem oder mehreren Feldern sortiert sein muss.

	Zugriff: Der Zugriff ist schneller als bei einer Standardtabelle, insbesondere wenn die Tabelle groß ist, da die Suche binär erfolgt.

	Einschränkung: Einträge müssen in der sortierten Reihenfolge eingefügt werden.

	Beispiel: `DATA: lt_table TYPE SORTED TABLE OF ty_structure WITH UNIQUE KEY field1 field2.`

3. **Hashed Tabelle (Hashed Table)**

	Zugriffsart: Hash-Algorithmus

	Verwendung: Wenn es viele Einträge gibt und der Zugriff auf die Einträge über den Schlüssel erfolgt.

	Zugriff: Der Zugriff ist sehr schnell und erfolgt über einen Hash-Algorithmus, unabhängig von der Anzahl der Einträge in der Tabelle.

	Einschränkung: Die Reihenfolge der Einträge ist nicht garantiert.

	Beispiel: `DATA: lt_table TYPE HASHED TABLE OF ty_structure WITH UNIQUE KEY field1 field2.`

**Einsatzbereiche:**
Standardtabellen sind gut geeignet, wenn die Tabelle klein ist und der Zugriff auf die Tabelle sequenziell erfolgt.

Sortierte Tabellen eignen sich am besten für Tabellen, die sortiert sein müssen und deren Zugriff oft mithilfe von Teilschlüsseln erfolgt.

Hashed Tabellen sind ideal, wenn der direkte Zugriff auf die Tabelle über den Schlüssel erfolgt und die Tabelle viele Einträge hat.

Diese internen Tabellenarten ermöglichen es den Entwicklern, je nach Anforderung und Nutzungsszenario, die am besten geeignete Tabelle auszuwählen.

### **Erstellung und Verwendung von Strukturen und internen Tabellen**

Erzeugung eines Strukturtypen:

```abap
TYPES: BEGIN OF ls_fahrzeug,
	hersteller(20) TYPE c,
	farbe TYPE String,
	motorleistung TYPE i,
END OF ls_fahrzeug.
```


Erstellung einer Struktur:
```abap
DATA gs_Wagen TYPE ls_fahrzeug.
gs_Wagen_hersteller = 'VW'.
gs_Wagen_farbe = 'rot'.
gs_Wagen_motorleistung = 150.
```

### Prozessierungsbefehle für interne Tabellen (bspw. Sort)

Tabellenoperationen für interne Tabellen

| **Befehl** | **Funktion** |
| ---- | ---- |
| SELECT | Daten lesen |
| INSERT | Einfügen |
| APPEND | Anhängen |
| READ | Zeilen lesen |
| MODIFY | Zeilen überschreiben |
| DELETE | Zeilen löschen |
| SORT | Tabelle sortieren |
| COLLECT | Verdichtete Zeile einfügen |
| CLEAR | Löscht alle Zeilen und gibt den Speicher bis auf initialen Speicherbedarf frei |
| REFRESH | Löscht Zeilen  <br>obsolet |
| FREE | Gesamte von Zeilen belegter Speicher wird freigegeben |
| DESCRIBE | Gibt die Anzahl der Einträge zurück |
| LOOP | Durchlaufe Zeilen einer interne Tabelle |

### Table Expressions

Table Expressions in ABAP bieten eine kompakte und leserliche Möglichkeit, auf Elemente von internen Tabellen zuzugreifen. Hier sind einige Beispiele für die Verwendung von Table Expressions in ABAP:
1. Direkter Zugriff auf ein Tabellenelement:
   `DATA(lv_value) = it_table[ 3 ].`
   Hier wird auf das dritte Element der internen Tabelle `it_table` zugegriffen und der Wert       in der Variablen `lv_value` gespeichert.

2. Zugriff mit einem Schlüssel (Key Access):
   Wenn die Tabelle eine sortierte Tabelle oder ein Hash-Tabelle ist, können Sie einen Schlüssel verwenden, um auf ein Element zuzugreifen:
   `DATA(lv_value) = it_sorted_table[ key name = 'Wert' ].`
   Hier wird auf das Element mit dem Schlüssel `name = 'Wert'` in der sortierten Tabelle `it_sorted_table` zugegriffen.

3. Bedingter Zugriff:
   `DATA(lv_value) = it_table[ tabix ] ? ##NO_TEXT.`
   Dieser Ausdruck greift auf das `tabix`-te Element der Tabelle `it_table` zu, falls `tabix` ein gültiger Index ist. Andernfalls wird ein Laufzeitfehler vermieden, indem `##NO_TEXT` verwendet wird.

4. Lesen und Ändern eines Tabellenelements:
   `it_table[ 1 ]-field = 'Neuer Wert'.`
   Hier wird das Feld `field` des ersten Elements der Tabelle `it_table` geändert.

5. Verwendung in Schleifen:
```abap
LOOP AT it_table INTO @DATA(ls_row) WHERE field = 'Kriterium'.
WRITE: / ls_row-another_field.
ENDLOOP.
```
 Hier wird eine Schleife über die interne Tabelle `it_table` ausgeführt,             aber     nur die Zeilen betrachtet, in denen das Feld `field` den Wert `'Kriterium'` hat.
