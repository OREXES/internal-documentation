---
title: "2. Programmstruktur"
description: "Struktur von ABAP-Programmen"
summary: ""
weight: 810
---

## 2.1 Relationale Operatoren (Lukas)

Relationale Operatoren, die zum Vergleich von zwei oder mehr Operanden eines beliebigen Datentyps verwendet werden.

Relationale Operatoren und verbinden zwei oder mehr Operanden eines beliebigen Datentyps, um einen relationalen Ausdruck oder einen Vergleichsausdruck zu bilden. Das Ergebnis des relationalen Ausdrucks ist wahr oder falsch.

Für bestimmte Datentypen gibt es zusätzliche relationale Operatoren. Der Prädikatsoperator "IS" qualifiziert einen Operanden.

Wenn Operanden von unterschiedlicher Länge und unterschiedlichem Typ sind, wird eine automatische Konvertierung durchgeführt.

Die automatische Typkonvertierung wird für einen der beiden Operanden durchgeführt. Die automatische Konvertierung kann durch den Datentyp bestimmt werden, und die folgende Liste zeigt den Vorrang der Datentypen.

Wenn ein Operand vom Datentyp I ist, dann wird der andere Operand in I konvertiert.

Wenn ein Operand vom Datentyp P ist, dann wird der andere Operand nach P konvertiert.

Wenn ein Operand vom Datentyp D ist, dann wird der andere Operand nach D konvertiert.

Die Typen C und N werden nicht konvertiert und direkt verglichen.

Ist ein Operand vom Datentyp N und der andere Operand vom Typ C oder X, werden beide Operanden nach P konvertiert.

Ist ein Operand vom Datentyp C und der andere Operand vom Typ X, so wird der Typ X nach C konvertiert.

Nachfolgend die Tabelle der Binäre Vergleichsoperatoren:

|**Operator**|**Beschreibung**|**Bedeutung**|
|---|---|---|
|**=, EQ**|Gleich|Wahr, wenn der Wert von Operand1 mit dem Wert von Operand2 übereinstimmt, sonst falsch.|
|**<>, NE**|Nicht gleich|Wahr, wenn der Wert von Operand1 nicht mit dem Wert von Operand2 übereinstimmt, sonst falsch.|
|**Is initial**|Ist initialisiert|Die Bedingung wird wahr, wenn sich der Inhalt der Variablen gegenüber dem ursprünglich zugewiesenen Wert nicht ändert.|
|**Is not initial**|Ist nicht initialisiert|Die Bedingung wird wahr, wenn sich der Inhalt der Variablen gegenüber dem ursprünglich zugewiesenen Wert geändert hat.|
|**<, LT**|Weniger als|Wahr, wenn der Wert von Operand1 kleiner ist als der Wert von Operand2, sonst falsch.|
|**>, GT**|Größer als|Wahr, wenn der Wert von Operand1 größer ist als der Wert von Operand2, sonst falsch.|
|**<=, LE**|Weniger gleich|Wahr, wenn der Wert von Operand1 kleiner oder gleich ist als der Wert von Operand2, sonst falsch.|
|>= GE|Größer gleich|Wahr, wenn der Wert von Operand1 größer oder gleich ist als der Wert von Operand2, sonst falsch.|

  Nachfolgend die Tabelle der Vergleichsoperatoren für zeichenartige Datentypen:

|**Operator**|**Beschreibung**|**Bedeutung**|
|---|---|---|
|**CO**|Enthält nur|Wahr, wenn operand1 nur Zeichen aus operand2 enthält. Groß-/Kleinschreibung und schließende Leerzeichen beider Operanden werden berücksichtigt.|
|**CN**|Enthält nicht nur|Wahr, wenn ein relationaler Ausdruck mit CO falsch ist, wenn operand1 also nicht nur Zeichen aus operand2 enthält.|
|**CA**|Enthält beliebig|Wahr, wenn operand1 mindestens ein Zeichen aus operand2 enthält. Groß-/Kleinschreibung und schließende Leerzeichen beider Operanden werden berücksichtigt.|
|**NA**|Enthält nicht irgendwelche|Wahr, wenn ein relationaler Ausdruck mit CA falsch ist, wenn operand1 also kein Zeichen aus operand2 enthält.|
|**CS**|Enthält String|Wahr, wenn der Inhalt von operand2 in operand1 enthalten ist. Groß-/Kleinschreibung wird nicht, schließende Leerzeichen des linken Operanden werden berücksichtigt.|
|**NS**|Enthält kein String|Wahr, wenn ein relationaler Ausdruck mit CS falsch ist, wenn operand1 also den Inhalt operand2 nicht enthält.|
|**CP**|Enthält Muster|Wahr, wenn der Inhalt von operand1 zu dem Muster in operand2 passt. Für die Bildung des Musters operand2 können Maskenzeichen verwendet werden, wobei "*" eine beliebige Zeichenkette inklusive der leeren Zeichenkette und "+" ein beliebiges Zeichen darstellt. Groß-/Kleinschreibung wird nicht berücksichtigt. Schließende Leerzeichen des linken Operanden werden berücksichtigt.|
|NP|Enthält kein Muster|Wahr, wenn ein relationaler Ausdruck mit CP falsch ist, wenn operand1 also nicht zum Muster in operand2 passt.|

## 2.2 Open-SQL
### Syntax
Variablen müssen mit einem Fluchtsymbol @ gekennzeichnet werden.

```abap
SELECT carrid, connid
       FROM sflight
       INTO ls_result
       WHERE carrid = @carrid
	   INTO ls_result.
```

### Bedingungen in Open SQL
|**Befehl**|**Funktion**|
|---|---|
|GROUP BY|Gruppiere das Ergebnis nach Feld|
|COUNT|Zähle zusammen|
|HAVING|Schränkt eine gruppierte Datenmenge ein|
|ORDER BY|Sortiert die Ergebnisse auf- oder absteigend|

### Aggregatfunktionen
| **Befehl** | **Funktion** |
| ---- | ---- |
| AVG | Ermittelt den Durchschnitt |
| COUNT | Zählt die Anzahl der Einträge |
| MAX | Ermittelt das Maximum |
| MIN | Ermittelt das Minimum |
| SUM | Berechnet die Summe |

### Performance

Die Optimierung von OpenSQL-Anweisungen in ABAP für bessere Performance ist besonders wichtig in großen und komplexen SAP-Systemen. Im Folgenden sind einige Richtlinien, um OpenSQL-Anweisungen effizienter zu gestalten beschrieben:

### Selektive Datenabfrage

Beschränke die abgefragten Daten auf das Notwendige. Verwende die `WHERE`-Klausel, um die Datenmenge zu reduzieren.

Beispiel:
Schlecht: `SELECT * FROM mara INTO TABLE @data(mara_tab).`

Besser: `SELECT matnr, mtart FROM mara INTO TABLE @data(mara_tab) WHERE mtart = 'FERT'.`

### Indizes nutzen

Orientiere die `WHERE`-Klausel an den Indizes der Datenbanktabelle, um die Abfrage zu beschleunigen.

Beispiel:
`SELECT * FROM vbak INTO TABLE @data(vbak_tab) WHERE vkorg = @vkorg AND vtweg = @vtweg.`

### Vermeidung von SELECT
Wähle nur die benötigten Spalten statt SELECT *, um die Datenmenge zu minimieren.

Beispiel:
Schlecht: `SELECT * FROM kna1 INTO TABLE @data(kna1_tab).`
Besser: `SELECT kunnr, name1 FROM kna1 INTO TABLE @data(kna1_tab).`

### Joins effizient nutzen

Verwende Joins statt mehrerer einzelner SELECT-Statements, um verwandte Daten aus mehreren Tabellen zu kombinieren.

Beispiel:
```abap
SELECT a~matnr, b~maktx FROM mara AS a INNER JOIN makt AS b ON a~matnr = b~matnr INTO TABLE @data(joined_data) WHERE b~spras = 'DE'.`
```
### FOR ALL ENTRIES vermeiden

Wenn möglich, vermeide `FOR ALL ENTRIES`, da es ineffizient sein kann, insbesondere bei großen Datenmengen.

Beispiel:

Statt `FOR ALL ENTRIES`, besser `JOIN` oder `WHERE ... IN (SELECT ...)`

### Aggregatfunktionen nutzen

Nutze Aggregatfunktionen (wie `SUM`, `MAX`, `MIN`) in deinen Abfragen, um Berechnungen auf der Datenbankebene durchzuführen, statt große Datenmengen in ABAP zu laden und dort zu verarbeiten.

Beispiel:
```abap
SELECT MAX(netwr) INTO @data(max_netwr) FROM vbrk.
```
### Vermeidung von SELECT DISTINCT

`SELECT DISTINCT` kann Performance-Probleme verursachen, wenn es nicht notwendig ist. Prüfe, ob es wirklich benötigt wird.

Beispiel:

Statt `SELECT DISTINCT`, besser die Datenmodellierung prüfen und optimieren.

### Verwendung von Cursor

Bei Verarbeitung großer Datenmengen können Cursor verwendet werden, um den Speicherverbrauch zu minimieren.

Beispiel:
```abap
OPEN CURSOR WITH HOLD FOR SELECT ...

FETCH NEXT CURSOR ... INTO ...
```
### Limitierung der Ergebnismenge

Beschränke die Anzahl der zurückgegebenen Zeilen, insbesondere bei Abfragen zu Analysezwecken oder in Benutzeroberflächen.

Beispiel:
```abap
SELECT ... INTO TABLE @data(...) UP TO 10 ROWS.
```
## 2.3  Kontrollfluss (Simon)

### If-Else Abfragen
```abap
IF Bedingung_1 AND Bedingung_2.

    * Anweisungsblock_1

ELSEIF Bedingung.

    * Anweisungsblock_2

ELSE.

    * Anweisungsblock_2

ENDIF.
```
### Check Abfragen

`CHECK` ist eine Kombination aus `IF` und `CONTINUE`. Die Nachfolgenden Befehle werden nur ausgeführt, wenn die Bedingung erfüllt ist. Andernfalls wird der Anweisungsblock verlassen.
```abap
CHECK Bedingung.
```
### Switches
```abap
CASE sy-subrc.

WHEN 0.

*   Okay-Fall

WRITE: / tz_netzwerktechnik,

'Teilnehmer für den Kurs Netzwerktechnik

gefunden'.

WHEN 4.

*   Fehlerfall

WRITE: / 'keine Teilnehmer für den Kurs

Netzwerktechnik gefunden'.

WHEN OTHERS.

*   Kann nicht sein, anderer sy-subrc wird von der

*   Anweisung nicht geliefert.

ENDCASE.
```
### Iteration
```abap
_While-Schleife_

WHILE sek > 0.

    WRITE: / sek.

    sek = sek - 1.

ENDWHILE.

_Do Schleife_

DO 24 TIMES.

* Anweisungsblock_1

ENDDO.

_Loop-Schleife_

LOOP AT itab ASSIGNING <field-symbol>.

* Anweisungsblock_1

ENDLOOP.
```
### Return, continue, exit, leave program,

`RETURN` beendet den aktuellen Verarbeitungsblock an jeder beliebigen Stelle im Programm.
`EXIT` beendet die komplette Schleife.
```abap
DO 24 TIMES.

    IF sy-index = 3.

      EXIT.

    ENDIF.

    ...

ENDDO.
```
Mit der `CONTINUE` Anweisung kann ein Anweisungsblock einer Schleife vorzeitig verlassen werden.
```abap
IF Bedingung_1.

    CONTINUE.

ENDIF.
```
Der `LEAVE PROGRAM` Befehl beendet das Programm.

## 2.2 BADI (Lukas evtl. Colin)

Einführung in Business Add-Ins (BADI)

BADIs sind eine Möglichkeit, die Funktion des SAP-Standardcodes an die eigenen bzw. Die Bedürfnisse des Kundens anzupassen. Ein BadI ist ein Quelltext-Plugin und nutzt Objektorientierung und Interfaces zur Implementierung. Hierdurch wird der bereits vorhandene Standardcode nicht verändert.  
Ziel der BAdIs ist es eine Geschäftsprozesse und Vorgänge im System an Projekt- und Kundenbedürfnisse anzupassen. Sie ergänzen somit die Enhancements, User-Exits und BAPIs. Unterschiede sind teilweise in Performance und hauptsächlich in der Art und Weise, wie sie angelegt werden. 

Verwendung und Anpassung von BADI in ABAP

<!-- ![](file:///C:/Users/SIMONF~1/AppData/Local/Temp/msohtmlclip1/01/clip_image002.png) -->

Startpunkt ist die Transaktion SE18 (BaDI Builder).

<!-- ![](file:///C:/Users/SIMONF~1/AppData/Local/Temp/msohtmlclip1/01/clip_image004.png) -->

Auswahl eines BaDI und oder Anlage eines Erweiterungsspots.

<!-- ![](file:///C:/Users/SIMONF~1/AppData/Local/Temp/msohtmlclip1/01/clip_image006.png) -->

Über das Menü an der linken Seite, kann zu den Implementierungen gesprungen werden. Durch ein Doppelklick darauf, kann zur implementierenden Klasse gewechselt werden. In dieser wird der Code dann entsprechend angepasst.

<!-- ![](file:///C:/Users/SIMONF~1/AppData/Local/Temp/msohtmlclip1/01/clip_image008.png) -->

<!-- ![](file:///C:/Users/SIMONF~1/AppData/Local/Temp/msohtmlclip1/01/clip_image010.png) -->

## 2.3 Objektorientierte Programmierung (Colin)

In ABAP gibt es die Möglichkeit Anwendung objektorientiert zu entwickeln. Grundlage bieten die Klassen und ihre Methoden. Eine Klasse ist wie die Blaupause der Anwendung zu sehen. Innerhalb der Methoden wird die Funktionalität der Klasse festgelegt. Hierzu kommen noch die Attribute. Diese können als Merkmale der Klasse bzw. Eigenschaften gesehen werden. Sie werden durch Variablen ausgeprägt.  
Alle bekannten Paradigmen der Objektorientierung treten auch hier in Kraft, so ist möglich, durch die Verwendung der Kapselung, die Klassen zu schützen und Zugriff zu regeln.  
Die Definition einer Klasse kann entweder lokal in der Workbench oder global erfolgen. Eine globale Definition hat die Folge, dass die Klasse in beliebig vielen Reports, Funktionsbausteinen, Anwendungen, etc. verwendet werden kann. Während die lokale Definition nur am Ort der Erzeugung vorhanden ist.

**Paradigmen der objektorientierten Programmierung**

- **Vererbung**:  
  Mit der Vererbung werden, wie bereits im Begriff enthalten, die Funktionen, Attribute etc. einer bestehenden Klasse an eine neue Klasse weiterzugeben. Diese neue Klasse dient dann als Erweiterungsklasse der ursprünglichen. Manchmal wird der Begriff Superklasse für die vererbende und Subklasse für die erhaltende 
  Klasse verwendet. Zweck dieses Konzeptes ist es, dass keine Redundanz entsteht und die Bestandteile effizient wiederverwendet werden. Ist es notwendig, dass eine Methode anzupassen, kann dies durch eine Redefintion durchgeführt werden.

Erstellung einer lokalen Klasse  
Die lokale Implementierung findet in der Workbench statt. Um in ABAP eine Klasse zu definieren, muss ein Definitions- und ein Implementierungsteil erstellt werden.  
In der Definition werden die Attribute, Methoden, ihre Eigenschaften und Schnittstellen festgelegt. Jedoch keine Ablauflogik, diese wird erst im Implementierungsabschnitt durchgeführt.

Definition
```abap
CLASS lcl_beispiel DEFINITION.  
   
  
  PUBLIC SECTION.  
   
    _"Insanzattrbut_  
     DATA: lv_summe TYPE i.  
   
    _"Statisches Attribut_  
     CLASS-DATA: lv_classdata TYPE string.  
   
    _"Konstante_  
     CONSTANTS: lc_const TYPE i VALUE 10.  
   
    METHODS:  
   
      add IMPORTING iv_num1 TYPE i  
                     iv_num2 TYPE i.  
   
  
  PROTECTED SECTION.  
   PRIVATE SECTION.  
   
ENDCLASS.
```
In der Definition werden die Kapselung, die Attribute, sowie die Methoden festgelegt. Wichtiger Punkt ist, dass hier noch keine Logik eingebaut wird.

Implementierung
```abap
CLASS lcl_beispiel IMPLEMENTATION.  
  METHOD add.  
   
    lv_summe = iv_num1 + iv_num2.  
   ENDMETHOD.  
   
ENDCLASS.
```
Vererbung Defintion
```abap
CLASS lcl_sub DEFINITION INHERITING FROM lcl_beispiel.  
   
  
  PUBLIC SECTION.  
   
    METHODS:  
   
      add IMPORTING iv_num1 TYPE i  
                     iv_num2 TYPE i REDEFINITION.  
   
  
  PROTECTED SECTION.  
   PRIVATE SECTION.  
   
ENDCLASS.
```
Vererbung Implementation
```abap
CLASS lcl_sub IMPLEMENTATION.

    METHOD add.

      DATA: sum TYPE i.

      sum = iv_num1 + iv_num2.

    ENDMETHOD.

ENDCLASS.
```
In der Implementierung der Klasse wird nun die Logik festgelegt. Besonders zu beachten ist es, dass der restliche ABAP-Code zwischen Definition und Implementierung geschrieben wird.

Erstellung einer globalen Klasse  
Die globale Erstellung findet der Transaktion SE24 (Class Builder) statt. Hier kann die Klasse wie eine Tabelle oder Struktur analog der SE11 zum Beispiel definiert werden. Über einen Button kann dann die Workbench geöffnet werden, um die Funktionen mit ABAP zu implementieren.

Definition

<!-- ![](file:///C:/Users/SIMONF~1/AppData/Local/Temp/msohtmlclip1/01/clip_image012.png) -->

Einstieg in den Class Builder.

<!-- ![](file:///C:/Users/SIMONF~1/AppData/Local/Temp/msohtmlclip1/01/clip_image014.png) -->

Hier kann nun über den Eingabebildschirm angegeben werden, was die Klasse alles beinhalten soll. Ähnlich der Anlage einer Struktur oder Datenbank in der SE11.  
Static und Instance Methoden unterscheiden sich darin, dass eine Static Methode kein Objekt von der Klasse benötigt, um aufgerufen zu werden. So muss für eine Instance Methode zuerst ein Objekt der Klasse erzeugt werden.

<!-- ![](file:///C:/Users/SIMONF~1/AppData/Local/Temp/msohtmlclip1/01/clip_image016.png) -->

Auch die Parameter der Methode werden hier festgelegt. Dies findet alles über die Buttons im Menüband statt.  
Durch Klick auf Quelltext, kann dann die ABAP-Logik eingebaut werden.

<!-- ![](file:///C:/Users/SIMONF~1/AppData/Local/Temp/msohtmlclip1/01/clip_image018.png) -->

Implementierung des Codes nach dem Sprung durch den Button “Quelltext”.

Zugriff auf eine Static Methode
```abap
zcl_beispiel=>add(  
   EXPORTING  
     iv_num1 = 4  
     iv_num2 = 4  
 ).
```
Zugriff auf eine Instance Methode
```abap
DATA: lcl_class TYPE REF TO zcl_beispiel.  
 CREATE OBJECT lcl_class.  
   
lcl_class->sub(  
   EXPORTING  
     iv_num1 = 12  
     iv_num2 = 3  
 ).
```
Vererbung einer Klasse

## 2.4 Prozedurale Programmierung (Simon)

-        **Einführung in die prozedurale Programmierung in ABAP**

-        **Unterschiede zur objektorientierten Programmierung**

-        **Form-Perform, etc.**

Formroutinen sind eine Art Funktionen zur lokalen Datenverarbeitung. Ihre Logik wird innerhalb der Anweisungen FORM und ENDFORM geschrieben und sie werden mit der PERFORM Anweisung aufgerufen. Sie können die Zusätze USING oder CHANGING für eine Werteübergabe enthalten.

-        **Includes**

Mit Includes lassen ABAP Programme sich in mehreren Unterprogramme aufteilen. Damit sind sie besser lesbar. Ein Unterprogramm wird mit der Anweisung INCLUDE unterprogrammname in das Hauptprogramm eingebunden. Der TOP INCLUDE eines Programmes bildet den globalen Deklarationsteil eines Programmes.
