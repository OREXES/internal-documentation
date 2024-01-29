---
title: "3. SAP Besonderheiten"
description: "Besonderheiten in SAP Systemen"
summary: ""
weight: 812
---

## 3.1 Funktionsbausteine 

### Was ist en Funktionsbaustein

Ein **Funktionsbaustein** ist eines der wichtigsten ABAP-Objekte in SAP ERP bzw. SAP S/4HANA. Das SAP-System benutzt an zahlreichen Stellen Funktionsbausteine für die ordnungsgemäße Funktion des SAP-Systems. Ein Funktionsbaustein kapselt den ABAP-Code und ermöglicht somit eine Wiederverwendung an verschiedenen Stellen.  
Ein Funktionsbaustein ist eine programmübergreifende wiederverwendbare Prozedur, die man in Funktionsgruppen strukturiert. Die wichtigste Transaktion für Funktionsbausteine ist die **Transaktion SE37 (ABAP-Funktionsbausteine)**. In dieser Transaktion kann man einen Funktionsbaustein anzeigen, ändern, anlegen, löschen, prüfen, aktivieren und ausführen. Die Transaktion SE37 ist sicherlich die Transaktion, wenn man Funktionsbausteine pflegen möchte.

<!-- ![Ein Bild, das Text, Screenshot, Schrift, Zahl enthält. -->
<!-- Automatisch generierte Beschreibung](file:///C:/Users/SIMONF~1/AppData/Local/Temp/msohtmlclip1/01/clip_image019.jpg) -->

Alternativ kann man die Transaktion SE80 (Object Navigator) verwenden, um einen Funktionsbaustein zu pflegen.  
Ein Funktionsbaustein kapselt einen ABAP-Code. Die Datenübergabe erfolgt über eine definierte Schnittstelle, die aus verschiedenen Parametern besteht. Folgende Parameterarten stehen dabei zur Verfügung:

- Import
- Export
- Changing
- Tabellen
- Ausnahmen

**Import-Parameter** dienen dazu, beim Aufruf des Funktionsbausteins Werte bzw. Variablen an den Funktionsbaustein zu übergeben. Import-Parameter werden beim Aufruf mit dem Schlüsselwort EXPORTING übergeben. Man „exportiert“ sozusagen Werte an den Funktionsbaustein. Der Funktionsbaustein „importiert“ diese. Sie können als optional gekennzeichnet werden, damit sie beim Aufruf nicht mehr zwingen versorgt werden müssen.

**Export-Parameter** sind immer optional. Dadurch werden Werte des Funktionsbausteins an das aufrufende Programm zurückgegeben. Export-Parameter nimmt man mit dem Schlüsselwort IMPORTING entgegen. Das aufrufende Programm „importiert“ somit den Wert.

**Changing-Parameter** sind Import- und Export-Parameter zugleich. Dabei handelt es sich um Variablen, die an den Funktionsbaustein übergeben werden, im Funktionsbaustein verändert werden und an das aufrufende Programm wieder zurückgegeben werden. Durch das Schlüsselwort CHANGING kann man Changing-Parameter beim Aufruf verwenden.

**Tabellen** sind veraltete Parameter und sollten nicht mehr verwendet werden.

**Ausnahmen** treten auf, wenn im Funktionsbaustein ein Fehler auftritt und dieser an das aufrufende Programm zurückgegeben wird. Somit kann man dort auf den Fehler entsprechend reagieren. Durch das Schlüsselwort EXCEPTIONS kann man im aufrufenden Programm die Ausnahmen entgegennehmen.

### Erstellung eines Funktionsbausteins

Ein Funktionsbaustein erstellt man über die Transaktion SE37 oder SE80. Ein Funktionsbaustein ist einer Funktionsgruppe zugeordnet. Deshalb muss man als Erstes eine Funktionsgruppe erstellen, wenn diese noch nicht existiert. Ansonsten kann man diesen Schritt überspringen und bei der Erstellung eines Funktionsbausteins die Funktionsgruppe angeben.

Entweder kann man in der Transaktion SE37 oder SE80 eine Funktionsgruppe erstellen. In der Transaktion SE37 wählt man hierfür die Menüfunktion „Springen > FGruppenverwaltung > Gruppe anlegen“.

<!-- ![Ein Bild, das Text, Schrift, Zahl, Software enthält. -->
<!-- Automatisch generierte Beschreibung](file:///C:/Users/SIMONF~1/AppData/Local/Temp/msohtmlclip1/01/clip_image021.jpg) -->

Daraufhin erscheint ein Fenster, in dem man den Namen der Funktionsgruppe, den Kurztext und den Verantwortlichen angibt. Nachdem man auf den Button „Sichern“ geklickt hat, wird die Funktionsgruppe angelegt und kann verwendet werden.

<!-- ![Ein Bild, das Text, Screenshot, Software, Zahl enthält. -->
<!-- Automatisch generierte Beschreibung](file:///C:/Users/SIMONF~1/AppData/Local/Temp/msohtmlclip1/01/clip_image023.jpg) -->

Nachdem man eine Funktionsgruppe erstellt hat oder eine existierende kennt, kann man einen Funktionsbaustein erstellen. Hierzu ruft man die Transaktion SE37 auf, gibt den Namen des Funktionsbausteins ein und klickt auf den Button „Anlegen“.

<!-- ![Ein Bild, das Text, Screenshot, Schrift, Zahl enthält. -->
<!-- Automatisch generierte Beschreibung](file:///C:/Users/SIMONF~1/AppData/Local/Temp/msohtmlclip1/01/clip_image024.jpg) -->

Daraufhin erscheint ein Fenster, in dem man den Namen, die zugeordnete Funktionsgruppe und den Kurztext angibt.

<!-- ![Ein Bild, das Text, Screenshot, Zahl, Schrift enthält. -->
<!-- Automatisch generierte Beschreibung](file:///C:/Users/SIMONF~1/AppData/Local/Temp/msohtmlclip1/01/clip_image026.jpg) -->

Nachdem man auf den Sichern-Button klickt, wird der Funktionsbaustein angelegt und man gelangt in den Function Builder und landet im Tab „Import“. Nun kann man in den einzelnen Tabs die Eigenschaften, Import-, Export-, Changing-Parameter, Tabellen und Ausnahmen angeben. Zudem hinaus schreibt man im Tab „Quelltext“ den gewünschten Programmcode.

  

## 3.2 Dynpro & Selection-Screens (GUI) (Joemar)

### Einführung in die Entwicklung von Dynpros und Selection-Screens

**Defintion von Dynpros**:
Dynamische Programme (Dynpros) sind ein zentrales Konzept in SAP ABAP und dienen der Erstellung von interaktiven Benutzeroberflächen für SAP-Anwendungen. 
Dynpros ermöglichen die Gestaltung von Bildschirmen, auf denen Benutzer mit dem SAP-System interagieren können. Diese Bildschirme enthalten verschiedene Elemente wie Eingabefelder, Auswahllisten, 
Knöpfe und andere Steuerelemente, die dem Benutzer die Eingabe von Daten und die Navigation innerhalb der Anwendung ermöglichen.

**Beispiel Dynpro aus den Benutzerantrag**:

<!-- ![](file:///C:/Users/SIMONF~1/AppData/Local/Temp/msohtmlclip1/01/clip_image028.png)          -->

**Strukturierte Oberfläche**:  
Dynpros ermöglichen eine logische und strukturierte Darstellung von Informationen, was es Benutzern erleichtert, sich in der Anwendung zurechtzufinden und die gewünschten Aufgaben auszuführen.

**Flexibilität und Anpassungsfähigkeit**:  
Die Flexibilität von Dynpros erlaubt es Entwicklern, Bildschirme nach den spezifischen Anforderungen einer Anwendung zu gestalten. Dies ermöglicht eine hohe Anpassungsfähigkeit und die Berücksichtigung der Bedürfnisse verschiedener Benutzergruppen.

**Interaktion und Rückmeldung**:  
Durch die Interaktion mit Dynpros erhalten Benutzer sofortige Rückmeldungen über ihre Eingaben oder Aktionen, was die Benutzererfahrung verbessert und Fehler minimiert.

**Nahtlose Integration mit ABAP-Logik**:  
Dynpros sind eng mit der ABAP-Logik verbunden, was es ermöglicht, die eingegebenen Daten direkt zu verarbeiten und in den SAP-Systemen zu nutzen.

**Was sind Selection-Screens?**  
Selection-Screens sind wichtige Werkzeuge in SAP ABAP, die es Benutzern ermöglichen, Eingabeparameter für Programme oder Funktionen festzulegen. Sie bieten eine interaktive Möglichkeit für Benutzer, die Ausführung von ABAP-Programmen zu steuern, indem sie spezifische Kriterien oder Filter festlegen, bevor das Programm ausgeführt wird.

**Beispiel Selection-Screen aus den Reader**:

<!-- ![](file:///C:/Users/SIMONF~1/AppData/Local/Temp/msohtmlclip1/01/clip_image030.png) -->

**Warum Selection-Screens**?  
Der Hauptzweck von Selection-Screens besteht darin, Benutzern die Auswahl von Daten für die Verarbeitung durch ABAP-Programme zu ermöglichen. Sie dienen als Filtermechanismus, um relevante Datensätze aus einer großen Datenmenge auszuwählen.

**Anpassungsfähigkeit und Flexibilität**:  
Selection-Screens bieten Flexibilität, da Benutzer verschiedene Parameter wie Benutzergruppe, Org-Einheiten Technische/Fachliche Rollen usw. festlegen können, um genau die Daten auszuwählen, die sie benötigen. Dies ermöglicht eine breite Anpassungsfähigkeit an verschiedene Anforderungen.

**Benutzerinteraktion und Kontrolle**:  
Sie bieten eine interaktive Benutzeroberfläche, über die Benutzer direkt mit dem Programm interagieren können, indem sie Werte eingeben oder auswählen, um das Ergebnis des Programms zu beeinflussen. Dadurch erhalten Benutzer mehr Kontrolle über die Verarbeitung der Daten.

**Optimierung der Programmausführung**:  
Durch die Nutzung von Selection-Screens können Programme effizienter ausgeführt werden, da sie nur die vom Benutzer ausgewählten Daten verarbeiten müssen. Dies trägt dazu bei, die Ausführungszeiten zu verkürzen und die Systemressourcen besser zu nutzen.

**Fehlerminimierung und Datenvalidierung**:  
Selection-Screens ermöglichen auch die Validierung von Benutzereingaben, bevor das Programm ausgeführt wird. Dadurch können Fehler vermieden werden, indem ungültige Eingaben abgefangen und Benutzer aufgefordert werden, korrekte Werte einzugeben.

**Wo können SELECTION-SCREENS verwendet werden?**
Selection-Screens können direkt in ABAP-Reporten erstellt werden. Bei der Erstellung oder Bearbeitung eines Reports in der ABAP Workbench kann der Entwickler Selection-Screen-Anweisungen hinzufügen, um den interaktiven Bildschirm zu definieren. Selection-Screens können auch in anderen Objekten wie Funktionsbausteinen, Methoden, Include-Programmen usw. definiert und verwendet werden, um Eingabeparameter oder -filter festzulegen.

**Wie erstelle ich einen SELECTION-SCREEN?**  
Innerhalb des Programms oder der Komponente können Anweisungen zur Definition des Selection-Screens verwendet werden. Einige wichtige Anweisungen sind:
```abap
"Definiert den Anfang und das Ende des Selection-Screens.
SELECTION-SCREEN BEGIN OF SCREEN ... END OF SCREEN

"Definiert Parameter für Benutzereingaben.
PARAMETERS

"Definiert Auswahlkriterien für Benutzer.
SELECT-OPTIONS

"Fügt Kommentare oder Erläuterungen zum Selection-Screen hinzu.
SELECTION-SCREEN COMMENT
```

**Beispiel SELECTION-SCREEN Block B1A aus dem Reader**:

<!-- ![](file:///C:/Users/SIMONF~1/AppData/Local/Temp/msohtmlclip1/01/clip_image032.png) -->

  

### Erstellung und Gestaltung von Benutzeroberflächen

**Auswahl des Entwicklungselements**:  
Um mit der Erstellung und Gestaltung von Dynpros zu beginnen muss zunächst ein neues Dynpro innerhalb eines Entwicklungselements erstellt werden. Typischerweise ist dies ein Paket oder eine Entwicklungsklasse.

**Neues Dynpro erstellen**:  
Auf das ausgewählte Entwicklungselement =>"Neu"=>"Dynpro" aus dem Dropdown-Menü, um einen neues Dynpro zu erstellen. Nachdem die grundlegenden Informationen für das neue Dynpro eingegeben wurden, wird der Screen Painter geöffnet, indem das neu erstellte Dynpro ausgewählt wird. Mit einem Doppelklick darauf oder über die Schaltfläche "Screen Painter" in der Werkzeugleiste.

**Arbeiten im Screen Painter**:  
Der Screen Painter ist nun geöffnet und es kann mit der Gestaltung des Dynpros begonnen werden. Hier ist es möglich Elemente wie Textfelder, Eingabefelder, Auswahllisten usw. auf dem Bildschirm platzieren und das Layout des Dynpros gestalten.

**Dynpro-Nummer**:  
Jedes Dynpro wird durch eine eindeutige Nummer identifiziert, die seine Position innerhalb eines SAP-Systems angibt. Diese Nummer wird zur Navigation und Steuerung zwischen verschiedenen Bildschirmen verwendet.

<!-- ![](file:///C:/Users/SIMONF~1/AppData/Local/Temp/msohtmlclip1/01/clip_image034.png) -->

**Subscreens**:  
Ein Subscreen ist ein separater Bildschirm (Dynpro), der in einen anderen Dynpro eingebettet wird, um spezifische Informationen anzuzeigen oder Funktionen bereitzustellen.  
Subscreens werden verwendet, um Teile der Benutzeroberfläche zu modularisieren, wodurch die Wiederverwendung von Bildschirminhalten und die Trennung von logischen Teilen der Benutzeroberfläche ermöglicht werden. Ein Subscreen wird in einem Containerbereich eines Hauptdynpros platziert und dort angezeigt. Die Anzeige eines Subscreens kann dynamisch während der Laufzeit eines Dynpros gesteuert werden. Daten können zwischen dem Hauptdynpro und dem Subscreen ausgetauscht werden, ähnlich wie bei der Datenbindung zwischen verschiedenen Teilen desselben Dynpros. Um einen Subscreen in einem Hauptdynpro zu definieren und einzubetten, wird die `DEFINITION SCREEN`-Anweisung verwendet. Subscreens können zur Laufzeit eines Dynpros über ABAP-Code hinzugefügt, geändert oder entfernt werden.

**Layout**:  
Das Layout eines Dynpros wird im Screen Painter erstellt. Es umfasst die visuelle Anordnung der Bildschirmelemente wie Textfelder, Eingabefelder, usw. Hier wird festgelegt, wie die Elemente auf dem Bildschirm angeordnet sind und wie sie miteinander interagieren.

<!-- ![](file:///C:/Users/SIMONF~1/AppData/Local/Temp/msohtmlclip1/01/clip_image036.png)  -->

**Bildschirm-Elemente eines Dynpros**:  
- **Textfelder**: Zur Anzeige von Texten oder Beschriftungen.  
- **Eingabefelder**: Zum Erfassen von Benutzereingaben wie Zahlen, Texten oder anderen Daten.  
- **Auswahlelemente**: Wie Checkboxen, Auswahllisten oder Radiobuttons, um Benutzern Auswahlmöglichkeiten zu bieten.  
- **Funktions- und Navigationsleisten**: Enthalten Schaltflächen für Aktionen wie Speichern, Zurück, etc.

<!-- ![](file:///C:/Users/SIMONF~1/AppData/Local/Temp/msohtmlclip1/01/clip_image038.png) -->

**Flow-Logic (Ablauflogik)**:  
Die Flow-Logic eines Dynpros definiert die Verarbeitungslogik, die auf Benutzeraktionen oder -eingaben reagiert. Diese Logik umfasst ABAP-Code, der festlegt, wie das System auf Ereignisse wie Klicken von Schaltflächen oder Eingabe in Felder reagiert.

<!-- ![](file:///C:/Users/SIMONF~1/AppData/Local/Temp/msohtmlclip1/01/clip_image040.png) -->

**PBO (Process Before Output)**:  
Die PBO-Logik definiert, was vor der Anzeige des Dynpros geschehen soll. Hier werden Initialisierungen von Variablen, Vorbelegungen von Feldern oder andere Vorbereitungen für die Anzeige durchgeführt.

**PAI (Process After Input)**:  
Die PAI-Logik wird ausgeführt, wenn der Benutzer mit dem Dynpro interagiert und eine Aktion ausführt. Hier wird festgelegt, wie das System auf Benutzeraktionen reagiert, z.B. wenn ein Button geklickt oder ein Eingabefeld ausgefüllt wird.

**Verbindung mit ABAP-Programmen**:  
Ein Dynpro ist eng mit einem ABAP-Programm verbunden, das die Logik für die Verarbeitung von Daten und Ereignissen auf dem Dynpro enthält. Die Kommunikation zwischen dem Dynpro und dem zugehörigen ABAP-Programm erfolgt über Module und Funktionen.


### Ansteuern von Dynpros (CALL SCREEN, SKIP TO SCREEN, LEAVE SCREEN etc.)

In der SAP ABAP-Programmierung dienen `CALL SCREEN`, `SKIP TO SCREEN` und `LEAVE SCREEN` dazu, die Steuerung und Navigation zwischen verschiedenen Dynpros innerhalb einer ABAP-Anwendung zu ermöglichen. Hier sind die Unterschiede und Verwendungszwecke dieser Befehle:

**CALL SCREEN**  
Der `CALL SCREEN` Befehl wird verwendet, um einen anderen Dynpro innerhalb desselben Programms aufzurufen und anzuzeigen. Es handelt sich um einen synchronen Aufruf, bei dem die Steuerung an den aufgerufenen Bildschirm übergeben wird. Nach der Verarbeitung des aufgerufenen Dynpros kehrt das Programm zur Verarbeitung an die Stelle zurück, von der aus der CALL SCREEN-Befehl aufgerufen wurde. Daten können zwischen dem aufrufenden Dynpro und dem aufgerufenen Dynpro über sogenannte „Export“- und „Import“-Parameter ausgetauscht werden.  
Beispiel:
```abap
CALL SCREEN <Dynpro-Nummer>.
```

**SKIP TO SCREEN**   
Der `SKIP TO SCREEN` Befehl dient dazu, die Steuerung an einen anderen Bildschirm zu übergeben, ohne die aktuellen Änderungen zu speichern oder zu verarbeiten. Es handelt sich um einen asynchronen Sprung, bei dem die aktuelle Verarbeitung abgebrochen wird und direkt zum aufgerufenen Bildschirm gesprungen wird, ohne Daten zu übergeben oder zu verarbeiten. Es wird häufig für Navigationen innerhalb von Reports verwendet, ohne eine spezifische Datenverarbeitung durchzuführen.  
Beispiel: 
```abap
SKIP TO SCREEN <Dynpro-Nummer>.
```

**LEAVE SCREEN**  
Der `LEAVE SCREEN` Befehl wird verwendet, um den aktuellen Bildschirm zu verlassen und zur Steuerung an den aufrufenden Bildschirm zurückzukehren. Es handelt sich um einen Befehl, der verwendet wird, um die aktuelle Verarbeitung zu unterbrechen und zum aufrufenden Bildschirm zurückzukehren. Er wird genutzt, wenn Änderungen im aktuellen Bildschirm nicht gespeichert oder verarbeitet werden sollen.  
Beispiel: 
```abap
LEAVE SCREEN.
```

**Zusammenfassung der Unterschiede**:  
- **CALL SCREEN**: Synchroner Aufruf eines anderen Dynpros innerhalb desselben Programms mit Datenübertragung und Rückkehr zur Verarbeitung.
- **SKIP TO SCREEN**: Asynchroner Sprung zu einem anderen Dynpro ohne Datenübertragung und sofortige Abbruch der aktuellen Verarbeitung.
- **LEAVE SCREEN**: Unterbrechung der aktuellen Verarbeitung und Rückkehr zum aufrufenden Bildschirm ohne Speicherung oder Verarbeitung der aktuellen Änderungen.

**Weitere Befehle**:  
Neben den bereits besprochenen Befehlen wie CALL SCREEN, SKIP TO SCREEN und LEAVE SCREEN gibt es noch weitere relevante Befehle, im Zusammenhang mit Dynpros verwendet werden können:

**SET SCREEN**  
Der `SET SCREEN` Befehl ermöglicht die Aktivierung oder Deaktivierung von Bildschirmelementen (z.B. Feldern, Buttons) während der Laufzeit eines Dynpros. Durch SET SCREEN können Sie dynamisch die Anzeige- oder Bearbeitungsattribute von Feldern steuern, je nachdem, wie der Programmablauf fortschreitet.  
Beispiel: 
```abap
SET SCREEN <Element-ID> PROPERTY <Eigenschaft> = <Wert>.
```

**LOOP AT SCREEN**  
Mit `LOOP AT SCREEN` können Sie über alle Bildschirmelemente eines Dynpros iterieren und bestimmte Operationen durchführen. Dieser Befehl ermöglicht die dynamische Bearbeitung von Bildschirmelementen während der Laufzeit, z.B. das Setzen von Eigenschaften oder das Ausblenden von Feldern basierend auf bestimmten Bedingungen.  
Beispiel: 
```abap
LOOP AT SCREEN. ... ENDLOOP.
```

**CLEAR SCREEN**  
Der Befehl `CLEAR SCREEN` löscht alle Daten und setzt die Bildschirmelemente eines Dynpros zurück. Er dient dazu, die angezeigten Informationen zu löschen und den Bildschirm in einen Ausgangszustand zurückzusetzen.  
Beispiel: 
```abap
CLEAR SCREEN.
```

## 3.3 Debugging

### Grundlagen des Debuggings in ABAP

Der Debugger ermöglicht zur Laufzeit eine Codeanalyse von ABAP-Programmen, Funktionsbausteinen und Web Dynpros u. a. Das Coding kann hier zeilen- und modulabschnittsweise durchlaufen werden. Der Codingablauf kann während der Laufzeit inklusive der Variablenwerte analysiert werden.

<!-- ![Ein Bild, das Text, Screenshot, Software, Computersymbol enthält. -->
<!-- Automatisch generierte Beschreibung](file:///C:/Users/SIMONF~1/AppData/Local/Temp/msohtmlclip1/01/clip_image042.jpg) -->

In der Standardsicht ist der Debugger in drei Teile aufgeteilt: Links (1) sieht man den Quelltext, der gerade durchlaufen wird. Rechts oben (2) ist der sogenannte Aufrufstack zu sehen. Dies ist eine hierarchische Auflistung der Programmteile, Methoden oder Funktionsbausteine, die bereits durchlaufen wurden. Unter dem Aufrufstack (3) können Variablen, Tabellen, etc. angezeigt werden. Diese können entweder eingetragen oder durch einen Doppelklick im Quelltext geladen werden.  
Mit den folgenden Buttons kann durch das Programm debuggen:

  
<!-- ![](file:///C:/Users/SIMONF~1/AppData/Local/Temp/msohtmlclip1/01/clip_image044.png) -->

<!-- ![](file:///C:/Users/SIMONF~1/AppData/Local/Temp/msohtmlclip1/01/clip_image045.png) -->

- **Einzelschritt (F5)**: _springt_ einen _Schritt_ weiter, also von Anweisung zu Anweisung
- **Ausführen (F6)**: _überspringt_ Funktionsbaustein, Methoden, Unterprogramme, etc.; diese Programmteile werden aber trotzdem durchlaufen; man bleibt auf derselben Ebene des Aufrufstacks
- **Return (F7)**: _verlässt_ den aktuellen Programmteil; auch werden nachfolgende Programmteile noch durchlaufen
- **Weiter (F8)**: _verlässt_ den Debugger; Programmteile werden aber noch durchlaufen

### Breakpoints

Es gibt verschiedene Möglichkeiten bei der Programmausführung in den Debugger zu wechseln:  
- `/h` im Kommandofenster eingeben. Der Debugger wird sofort am Anfang des Programms ausgeführt. Empfehlenswert, wenn das Programm vom Programmstart an debuggt werden soll.
- `/hs` im Kommandofenster eingeben. Der Debugger wird sofort am Anfang des Programms gestartet, inklusive der Programmteile, die den Status "Systemprogramm" haben. Das Systemdebugging ist normalerweise nicht notwendig. Wenn jedoch ein Programm debuggt werden soll, was den Status "Systemprogramm" hat, dann macht dieser Debuggingmodus Sinn.

Eine weitere Möglichkeit den Debugger aufzurufen ist via das Kommando `break`  
- `break <benutzername>` im Coding schreiben. Das Programm stoppt nur beim SAP-Benutzer <benutzername>. Empfehlenswert, wenn das Programm an einer bestimmten Stelle in den Debugger springen soll und man selbst das Programm debuggen will. Hier ist es auch meist unproblematisch, wenn man vergisst den Breakpoint bei einem Transport zu löschen, da bei anderen SAP-Usern der Sprung in den Debugger nicht erfolgt.   
- `break-point` Hier springt das Programm bei jedem SAP-Benutzer mit Debuggerberechtigung in den Debugger. Es ist dringend zu empfehlen diesen Befehl nur mit Vorsicht zu nutzen. Es ist unangenehm und wirkt unprofessionell, wenn im Qualitäts- oder Produktivsystem andere Benutzer oder gar der Fachwender mit Debuggerberechtigung ungewollt in den Debugger springen. Hier ist z.B. `break <benutzername>` vorzuziehen. Vor jedem Transport ins Qualitätssystem und besonders in Produktivsystem sollte das Code um diese Breakpoints „break-point“ bereinigt werden. Noch besser ist es sie gar nicht zu verwenden. Dann kann es auch nicht vergessen werden sie zu löschen.  
- `Break-point id <Checkpoint-Gruppe>` In der Transaktion SAAB kann man Checkpoint-Gruppen definieren. Im Coding kann man auf diese Checkpoint-Gruppe verweisen. In der Transaktion SAAB kann man dann für diese Checkpoint-Gruppe einstellen, ob dieser dynamische Break-Point an dem Tag aktiv sein soll. Das Programm spring dann für den eigenen User an dem heutigen Datum in dem aktuellen System in den Debugger, sofern die Debugging-Berechtigung vorhanden ist. Ganz praktisch ist es auch, dass SAP viele Checkpoint-Gruppen angelegt hat, die man selbst auch im Qualitäts- oder Produktiv-System aktivieren kann.

### dynamische Breakpoints

Eine andere Möglichkeit Breakpoints zu setzen sind dynamische Breakpoints. Diese Breakpoints bieten sich vor allem an, wenn das Problem nicht genau auf eine Programmstelle fixiert werden kann. Verschiedene dynamische Breakpoints finden Sie in der Statusleiste im ABAP-Debugger:

<!-- ![Ein Bild, das Text, Screenshot, Schrift, Zahl enthält. -->
<!-- Automatisch generierte Beschreibung](file:///C:/Users/SIMONF~1/AppData/Local/Temp/msohtmlclip1/01/clip_image047.png) -->

Darauf öffnet sich folgendes Fenster, wo man nach verschiedenen Kriterien Breakpoints setzen kann.

<!-- ![Ein Bild, das Text, Screenshot, Reihe, Zahl enthält. -->
<!-- Automatisch generierte Beschreibung](file:///C:/Users/SIMONF~1/AppData/Local/Temp/msohtmlclip1/01/clip_image049.png) -->

Hier möchte ich zwei Funktionen besonders hervorheben einmal, die Funktion „Breakpoint bei Message" verweisen. Dieser dynamische Breakpoint ist bei der Fehlerfindung besonders sinnvoll. Desweitern die Funktion „ABAP Befehl“, wo ein Breakpoint bei jedem Befehl gesetzt wird, um so z.B. ein Fehler bei der Selektion _„Select“_ zu finden.

### Externe Breakpoints

Beim externen Debugging kommt eine weitere Breakpointart, _Externe Breakpoints_, zum Einsatz. Durch das Setzen von einen oder mehrere externe Breakpoints für das ABAP-Programm, dessen spätere Ausführung unterbrochen und mit dem ABAP-Debugger kontrolliert werden soll.

<!-- ![Ein Bild, das Text, Schrift, Screenshot enthält. -->
<!-- Automatisch generierte Beschreibung](file:///C:/Users/SIMONF~1/AppData/Local/Temp/msohtmlclip1/01/clip_image051.png) -->

Dann kann man an die Stelle im Coding, die einen interessiert, einen externen Breakpoint setzen und noch bestimmen für welchen User der externe Breakpoint gelten soll -> beim nächsten Aufruf der entsprechenden Codingstelle durch den User, der in den Einstellungen hinterlegt ist, springt nun bei dir der Debugger auf.
Der User für das externe Debugging wird in den Einstellungen wie folgt definiert:  
In der Menüleiste des ABAP-Editors auf Hilfsmittel -> Einstellungen klicken; Reiter ABAP-Editor -> Debugging: Benutzer-Option aktivieren und den entsprechenden User setzen.

### Watchpoints

Ein ähnliches Tool, das zur Verfügung steht, ist der Watchpoint zur. Der Watchpoint überwacht Änderungen an der angegebenen Variable. Das heißt, hiermit kann man verfolgen, wo sich der Fehler eventuell in einem Feld einschleicht oder auch, wo bestimmte Tabellen befüllt werden. Watchpoints können aber nur auf Variablen des aktuellen Kontexts gesetzt werden.

<!-- ![](file:///C:/Users/SIMONF~1/AppData/Local/Temp/msohtmlclip1/01/clip_image053.jpg) -->

Mit der dem Klicken des oben markierten Buttons oder mit der Tastenkombination Umschalt + F4 öffnet sich das nachfolgende Fenster, hier kann eine Variable eingetragen werden. Zudem kann der Watchpoint in der letzten Zeile des Fensters mit einer Bedingung versehen werden.

<!-- ![Ein Bild, das Text, Screenshot, Software, Zahl enthält. -->
<!-- Automatisch generierte Beschreibung](file:///C:/Users/SIMONF~1/AppData/Local/Temp/msohtmlclip1/01/clip_image055.jpg) -->

Der Vorteil der Bedingung ist das z.B. bei einer langen Schleife nicht mühsam jeder Durchlauf einzeln nach dem Wert überprüft werden muss, sondern einfach über die Bedingung der fehlerhafte Wert direkt angelaufen wird. Nachfolgend ist eine Beispielbedingung zu sehen:

<!-- ![](file:///C:/Users/SIMONF~1/AppData/Local/Temp/msohtmlclip1/01/clip_image057.png) -->

-        Fehlerbehebung, Breakpoints, Wertaustausch, dynamische Breakpoints, Watchpoints, Nutzerbreakpoints, etc.

## 3.4 Lokale und globale Datentypen 

Im ABAP Dictionary besteht die Möglichkeit, globale Datentypen zu definieren, die für sämtliche Repository-Objekte des aktuellen AS ABAP sichtbar sind und entsprechend genutzt werden können, sofern es das Paketkonzept zulässt.

Die verfügbaren Datentypen im ABAP Dictionary umfassen:

- Datenelemente für elementare Datentypen und Referenztypen
- Strukturen, die sich aus beliebigen anderen Datentypen zusammensetzen
- Tabellentypen mit beliebigen Zeilentypen

In ABAP-Programmen kann über den TYPE-Zusatz in deklarativen Anweisungen auf die im ABAP Dictionary definierten Datentypen verwiesen werden. Dabei verhalten sich Datenelemente wie elementare ABAP-Typen, Strukturen wie strukturierte ABAP-Typen und Tabellentypen wie entsprechende ABAP-Typen. Die elementaren Komponenten jedes Datentyps im ABAP Dictionary basieren auf einem Satz eingebauter Typen des ABAP Dictionary, für die eine Zuordnung zu den eingebauten ABAP-Typen festgelegt ist. Bei einer Änderung eines Datentyps im ABAP Dictionary erfolgt automatisch eine Anpassung aller Verwender.

Anlegen von globalen Datentypen:

Zuerst geht man in die Transaktion `se11`.

{{< figure src="images/se11-1.png" alt="Einstiegsbild der Transaktion Se11" caption:"Einstiegsbild der Transaktion Se11" >}}

Nun muss der Radio-Button `Datentyp` ausgewählt werden. Darauf muss nun der Name des Datentyp in das zugehörige Feld eingetragen werden. Der nächste Schritt wäre den Button `Anlegen` zu betätigen.
Nun öffnet sich ein Pop-Up was abfragt was für ein Datentyp angelegt werden soll.

{{< figure src="images/se11-2.png" alt="Fenster der Datentypauswahl der Se11" caption:"Fenster der Datentypauswahl der Se11" >}}

Je nachdem was man nun auswählt unterscheidet sich das nachfolgende Fenster. 

- Datenelement

  {{< figure src="images/se11-2-dataelement.png" alt="Fenster der Datentypauswahl der Se11" caption:"Fenster der Datentypauswahl der Se11" >}}

   #### Domäne (Domain)
    Eine Domäne beschreibt wiederum den Datentyp und die zugehörigen Einschränkungen oder Regeln für die Verwendung dieses Datenelements festlegt.
    Die Domäne besitzt folgende Eigenschaften und muss auch als Dictonary-Objekt angelegt werden. Hierbei müssen folgende Eigenschaften festgelegt werden:

  ##### Datentyp (Data Type)
  Die grundlegende Art der Daten, die das Datenelement repräsentiert. Beispiele für Datentypen sind i für Integer, c für Character, d für Datum usw.

  ##### Länge (Length)
  Die maximale Anzahl von Zeichen oder Bytes, die das Datenelement speichern kann. Die Länge hängt vom Datentyp ab.

  ##### Dezimalstellen (Decimal Places)
  Falls das Datenelement einen numerischen Datentyp hat, wie zum Beispiel p für Decimal, gibt die Anzahl der Dezimalstellen die Genauigkeit an.

  ##### Währungsfeld (Currency Field)
  Falls erforderlich, kann ein Datenelement als Währungsfeld markiert werden, um sicherzustellen, dass nur gültige Währungscodes zugewiesen werden können.

  ##### Festwertliste (Fixed Value List)
  Eine Liste von festen Werten, die das Datenelement annehmen kann. Dies wird verwendet, um die Gültigkeit der eingegebenen Daten einzuschränken.

  ##### Referenz auf eine Domäne (Reference to a Domain)
  Eine Domäne kann auf eine andere Domäne verweisen, was die Wiederverwendung von Definitionen ermöglicht.

   #### Eingebauter Typ (Built-in Type)

    Eingebaute Typen sind vordefinierte ABAP-Datentypen, die standardmäßig in der Sprache vorhanden sind.
    Beispiele für eingebaute Typen sind i für Integer, c für Character, d für Datum usw.
    Diese Typen sind bereits in ABAP definiert und können direkt verwendet werden, ohne sie zuvor selbst zu definieren.

  #### Referenztyp (Reference Type):

    Ein Referenztyp ist ein Datentyp, der auf Objekte zeigt oder auf eine Speicheradresse verweist.
    In ABAP können Referenzen durch Verwendung von REF TO erstellt werden.
    Referenzen werden verwendet, um auf Objekte zuzugreifen, die dynamisch während der Laufzeit erstellt werden, anstatt statisch während der Entwicklungszeit.

- Struktur

  {{< figure src="images/se11-2-structure.png" alt="Fenster der Datentypauswahl der Se11" caption:"Fenster der Datentypauswahl der Se11" >}}

- Tabellentyp

  {{< figure src="images/se11-tabletyp.png" alt="Fenster der Datentypauswahl der Se11" caption:"Fenster der Datentypauswahl der Se11" >}}

  #### Zeilentyp (Line Type):

    Der Zeilentyp wird für interne Tabellen verwendet.
    Interne Tabellen sind spezielle Datenstrukturen in ABAP, die eine dynamische Tabelle von Datenzeilen darstellen.
    Der Zeilentyp definiert die Struktur einer Zeile in der internen Tabelle.

  #### Eingebauter Typ (Built-in Type):

    Eingebaute Typen sind vordefinierte ABAP-Datentypen, die standardmäßig in der Sprache vorhanden sind.
    Beispiele für eingebaute Typen sind i für Integer, c für Character, d für Datum usw.
    Diese Typen sind bereits in ABAP definiert und können direkt verwendet werden, ohne sie zuvor selbst zu definieren.

  #### Referenztyp (Reference Type):

    Ein Referenztyp ist ein Datentyp, der auf Objekte zeigt oder auf eine Speicheradresse verweist.
    In ABAP können Referenzen durch Verwendung von REF TO erstellt werden.
    Referenzen werden verwendet, um auf Objekte zuzugreifen, die dynamisch während der Laufzeit erstellt werden, anstatt statisch während der Entwicklungszeit.

Bei Datenelementen hat man drei Möglichkeiten einen Zeilentyp festzulegen: Der Zeilentyp, eingebauter Typ und Refernenztyp

Lokale Datentypen werden innerhalb von ABAP-Programmen definiert und dienen dazu, Variablen mit spezifischen Datentypen zu erstellen, ohne dabei den globalen Namensraum zu beeinflussen. Diese Datentypen können durch das Schlüsselwort `DATA` deklariert werden und ermöglichen die Definition von internen Tabellen, Strukturen, und anderen Datentypen, die ausschließlich innerhalb des jeweiligen Programms, Klasse oder Funktionsbausteins Gültigkeit haben. Die Verwendung von lokalen Datentypen trägt dazu bei, den Code übersichtlich zu gestalten, den Wartungsaufwand zu reduzieren und mögliche Konflikte mit globalen Variablen zu vermeiden. 


### Dynamische Datentypen

Dynamische Datentypen ermöglichen es, Variablen während der Laufzeit zu definieren und zu verarbeiten. Dies bietet mehr Flexibilität, da der Datentyp nicht statisch während der Entwicklungszeit festgelegt wird. Die ABAP-Sprache unterstützt dynamische Datentypen durch den Einsatz von Datenreferenzen und der Klasse `CL_ABAP_DATADESCR`.

Hier ist ein einfaches Beispiel für die Verwendung dynamischer Datentypen in ABAP:
```abap
DATA: dynamic_variable TYPE REF TO data.

FIELD-SYMBOLS: <fs_dynamic> TYPE ANY.

* Dynamischen Datentyp erstellen
CREATE DATA dynamic_variable TYPE 'STRING'.

* Datenreferenz initialisieren
ASSIGN dynamic_variable->* TO <fs_dynamic>.

* Wert zuweisen
<fs_dynamic> = 'Hello, Dynamic World!'.

* Ausgabe
WRITE: / 'Dynamic Value:', <fs_dynamic>.
```

In diesem Beispiel wird eine dynamische Variable `dynamic_variable` erstellt, die auf den Datentyp `STRING` zeigt. Dann wird eine Datenreferenz `<fs_dynamic>` erstellt, die auf den dynamischen Datentyp zeigt. Schließlich wird ein Wert zugewiesen und ausgegeben.

Es ist zu beachten, dass bei der Verwendung dynamischer Datentypen Vorsicht geboten ist, da dies zu Laufzeitfehlern führen kann, wenn die Datentypen nicht korrekt verarbeitet werden. Die Verwendung von dynamischen Datentypen sollte auf bestimmte Anwendungsfälle beschränkt werden, bei denen ein hohes Flexibilität erforderlich ist.

### Suchhilfen

Suchhilfen sind Objekte, die verwendet werden können, um Dynpro-Feldern eine Eingabehilfe (F4-Hilfe) zuzuordnen. Hierzu muss eine Suchhilfe im ABAP Dictionary anlegen und diese dann an das entsprechende Dynpro-Feld anbinden. Die Eingabehilfe (F4-Hilfe) ist eine Standardfunktion des SAP-Systems. 

Man geht in das ABAP Dictionary (SE11). Dann wählt man den Objekttyp "Suchhilfe" (Search Help) aus. Gib einen Namen für das Suchhilfenobjekt und ein Klicke auf "Anlegen". Danach wählt man den Radiobutten Elementare Suchilfe aus, am Ende des Punktes wird noch auf Sammelsuchhiflen eingegangen. Dann sollte das folgende Fenster zusehen sein:

{{< figure src="images/se11-3-searchhelp.png" alt="Fenster der Datentypauswahl der Se11" caption:"Fenster der Datentypauswahl der Se11" >}}

Die nächsten Schritte sehen wie folgt aus:

#### Festlegung der Struktur der Suchhilfe:

Füge Auswahlkriterien hinzu, indem du Felder für die Suche definierst.
Füge Anzeigefelder hinzu, die dem Benutzer die Informationen zur Verfügung stellen, die er sehen soll.
Du kannst auch Tabellen oder Views als Basis für die Suchhilfe verwenden.

#### Festlegung der Anzeigefelder (Display Fields):

Definiere die Felder, die in den Suchergebnissen angezeigt werden sollen.
Die Anzeigefelder sollten relevante Informationen enthalten, um dem Benutzer die Auswahl zu erleichtern.

#### Pflege der Suchhilfenattribute:

Gehe zur Registerkarte "Attribute" und definiere spezifische Attribute für die Suchhilfe, wie z.B. das Erscheinungsbild, Sortierreihenfolge und weitere Optionen.

#### Generierung und Aktivierung der Suchhilfe:

Klicke auf "Generieren" und dann auf "Aktivieren", um die Suchhilfe zu erstellen und zu aktivieren.

#### Integration der Suchhilfe in Programme:

Du kannst die Suchhilfe in deinem ABAP-Programm durch CALL FUNCTION oder AT SELECTION-SCREEN on VALUE-REQUEST-Ereignisse integrieren.
Verwende die Suchhilfe-Funktionen wie F4IF_INT_TABLE_VALUE_REQUEST, F4IF_FIELD_VALUE_REQUEST oder F4IF_VALUE_REQUEST, um die Suchhilfe aufzurufen.

Hier ist ein einfaches Beispiel für die Integration einer Suchhilfe in einem ABAP-Programm:

```abap
DATA: gv_field TYPE fieldname,
      gt_result TYPE TABLE OF your_data_structure.

PARAMETERS: p_search TYPE gv_field OBLIGATORY.

AT SELECTION-SCREEN ON VALUE-REQUEST FOR p_search.
  CALL FUNCTION 'F4IF_INT_TABLE_VALUE_REQUEST'
    EXPORTING
      retfield        = 'P_SEARCH'
      value_org       = 'S'
    TABLES
      value_tab       = gt_result
      return_tab      = gt_result.
```
Stelle sicher, dass du die spezifischen Namen und Strukturen deiner Suchhilfe und deiner Daten verwenden. Diese Anleitung bietet nur eine grundlegende Übersicht über den Prozess der Erstellung von Suchhilfen in ABAP.

#### Sammelsuchhilfen

In ABAP (Advanced Business Application Programming) ist eine "Sammelsuchhilfe" (Collective Search Help) eine erweiterte Form der Suchhilfe, die es ermöglicht, mehrere Werte aus verschiedenen Suchhilfen zu sammeln und in einer gemeinsamen Liste anzuzeigen. Im Gegensatz zu einer einzelnen Suchhilfe erlaubt die Sammelsuchhilfe die gleichzeitige Auswahl von Werten aus verschiedenen Quellen.

## 3.5 SQL Advanced Techniques 

-        Joins, LIKE %, IN

Bei ABAP SQL gibt es Besonderheiten bei oben geannten Operatoren.

#### ABAP Joins: 
ABAP bietet verschiedene Arten von Joins, um Daten aus verschiedenen Datenbanktabellen abzurufen und zu verarbeiten. Die gängigsten Joins sind ```abap INNER JOIN ```, ```abap LEFT OUTER JOIN ``` und ```abap RIGHT OUTER JOIN ```. Mit Joins können Daten aus mehreren Tabellen basierend auf gemeinsamen Schlüsselwerten zusammengeführt werden. Beispiel:

```abap
SELECT * FROM table1
INNER JOIN table2 ON table1.field = table2.field
INTO @DATA(result).
```
#### LIKE %: 
Der LIKE-Operator in ABAP wird verwendet, um nach Zeichenketten zu suchen, die bestimmte Muster erfüllen. Das % wird als Platzhalter verwendet, um eine beliebige Anzahl von Zeichen zu repräsentieren. Beispiel:
```abap
SELECT * FROM table
WHERE field LIKE '%pattern%'
INTO @DATA(result).
```
In diesem Beispiel würde die Abfrage nach Zeichenketten suchen, die das Muster "pattern" enthalten, unabhängig von deren Position in der Zeichenkette.

#### IN: 
Der IN-Operator wird verwendet, um zu überprüfen, ob ein Wert in einer Liste von Werten vorhanden ist. Beispiel:
```abap
SELECT * FROM table
WHERE field IN ('value1', 'value2', 'value3')
INTO @DATA(result).
```
Diese Abfrage würde Datensätze zurückgeben, deren Feldwert in der angegebenen Liste enthalten ist.

#### Dynamische Erstellung von Tabellen

Die Erstellung von dynamische Tabellen kann direkt über die ABAP-Data Dictionary-Typen realisiert werden. Hier ist ein Beispiel:

```abap
DATA: lt_dynamic_table TYPE TABLE OF (iv_structure_name).

* Dynamische Tabelle erstellen
DATA: lt_components TYPE TABLE OF dd03l,
      ls_component TYPE dd03l.

* Strukturkomponenten abrufen
CALL FUNCTION 'DDIF_FIELDINFO_GET'
  EXPORTING
    tabname              = iv_structure_name
  TABLES
    dfies_tab            = lt_components
  EXCEPTIONS
    not_found            = 1
    internal_error       = 2
    OTHERS               = 3.

IF sy-subrc = 0.
  LOOP AT lt_components INTO ls_component.
    APPEND VALUE #( ls_component-fieldname ) TO lt_dynamic_table.
  ENDLOOP.
ELSE.
  " Fehlerbehandlung
ENDIF.

* Daten in die dynamische Tabelle einfügen (als Beispiel)
LOOP AT lt_dynamic_table INTO DATA(ls_line).
  APPEND VALUE #( ls_line = 'Value' ) TO lt_dynamic_table.
ENDLOOP.
```
In diesem Beispiel

```abap lt_dynamic_table ``` ist die dynamische interne Tabelle, die zur Laufzeit erstellt wird. Der ```abab iv_structure_name ``` ist der Name der Struktur, die Sie verwenden möchten.
```abap lt_components ``` wird verwendet, um die Komponenten der Struktur aus dem Data Dictionary abzurufen.
Dann wird eine Schleife verwendet, um die Feldnamen in ```abab lt_dynamic_table ``` hinzuzufügen.
Optional können Sie Daten in die Tabelle einfügen, wie im Beispiel gezeigt.

Stellen Sie sicher, dass ```abap iv_structure_name ``` durch den tatsächlichen Namen Ihrer Struktur ersetzt wird. Dieser Ansatz ermöglicht es Ihnen, eine Tabelle mit unbekannter Struktur zur Laufzeit zu erstellen und mit Daten zu füllen.

### Dynamischer Aufruf von Funktionsbausteinen

In ABAP kann der dynamische Aufruf von Funktionsbausteinen mithilfe von Funktionen wie CALL FUNCTION und RFC_CALL_FUNCTION durchgeführt werden. Nachfolgend ist ein einfaches Beispiel für den dynamischen Aufruf eines Funktionsbausteins:

```abap
DATA: lv_function_name TYPE funcname,
      lt_parameters    TYPE TABLE OF RFCDBST,
      lt_export_parameters TYPE TABLE OF RFCDBST,
      lt_import_parameters TYPE TABLE OF RFCDBST,
      lt_exception      TYPE TABLE OF RFCDBST,
      lv_result         TYPE any.

* Funktionsbausteinname
lv_function_name = 'RFC_PING'.

* Parameter für den Funktionsbaustein
APPEND VALUE #( 'PARAMETER_NAME' = 'VALUE' ) TO lt_parameters.

* Aufruf des Funktionsbausteins
CALL FUNCTION lv_function_name
  EXPORTING
    PARAMETERS = lt_parameters
  IMPORTING
    RESULT     = lv_result
  EXCEPTIONS
    SYSTEM_FAILURE        = 1
    COMMUNICATION_FAILURE = 2
    OTHERS                = 3.

IF sy-subrc <> 0.
  WRITE: / 'Fehler beim Aufruf des Funktionsbausteins:', lv_function_name.
ELSE.
  WRITE: / 'Ergebnis:', lv_result.
ENDIF.
```

In diesem Beispiel wird der Funktionsbaustein RFC_PING aufgerufen, und es wird ein einzelner Parameter mit dem Namen PARAMETER_NAME und dem Wert VALUE übergeben.

Wenn Sie den dynamischen Aufruf von Remote Function Calls (RFC) benötigen, können Sie die Funktion RFC_CALL_FUNCTION verwenden, die für die Kommunikation mit einem Remote-System geeignet ist.

Es ist wichtig zu beachten, dass der dynamische Aufruf von Funktionsbausteinen mit Vorsicht verwendet werden sollte, da dies zu Laufzeitfehlern führen kann, wenn die erforderlichen Funktionsbausteine nicht existieren oder die Parameter nicht korrekt übergeben werden. Daher sollte eine gründliche Überprüfung und Handhabung von möglichen Fehlern im Code eingebaut werden.

### Dynamische WHERE-Aufrufe

In SAP wird die Erstellung einer dynamischen WHERE-Klausel in der Regel durch die Verwendung von dynamischem SQL oder Open SQL mit dynamischen Ausdrücken realisiert. Open SQL ist die natürliche SQL-Sprache, die in SAP ABAP verwendet wird. Hier ist ein einfaches Beispiel, wie eine dynamische WHERE-Klausel in einem ABAP-Programm erstellt werden kann:

```abap
DATA: lv_where_clause TYPE string,
      lv_condition     TYPE string.

* Setzen Sie Ihre dynamischen Bedingungen
lv_condition = 'FELD1 = ''WERT1'' AND FELD2 = ''WERT2'''.

* Konstruieren Sie die WHERE-Klausel
CONCATENATE 'WHERE' lv_condition INTO lv_where_clause SEPARATED BY space.

* Ihre SQL-Abfrage
SELECT * FROM ihre_tabelle INTO TABLE ihre_ergebnistabelle WHERE (lv_where_clause).

* Verarbeiten Sie das Ergebnis
LOOP AT ihre_ergebnistabelle INTO DATA(ergebniszeile).
  " Ihre Verarbeitungslogik hier
ENDLOOP.
```

In diesem Beispiel repräsentiert lv_condition die dynamischen Bedingungen, die auf die WHERE-Klausel anwendendet wird. Diese Bedingung kann basierend auf Laufzeitwerten oder Benutzereingaben konstruiert werden. Die lv_where_clause wird dann durch die Verkettung der Bedingung mit dem Schlüsselwort WHERE konstruiert. Schließlich kann diese dynamische WHERE-Klausel in dem SQL-SELECT-Anweisung verwendet werden.

Zu beachten ist, dass das Erstellen dynamischer SQL-Abfragen in Anwendung anfällig für SQL-Injektionsangriffe machen kann, wenn Benutzereingaben nicht ordnungsgemäß validiert und bereinigt werden. Validieren und bereinigen Sie immer Benutzereingaben, um Sicherheitslücken zu verhindern.

Außerdem handelt es sich bei dem obigen Beispiel um eine vereinfachte Darstellung, und in einem realen Szenario müssen möglicherweise verschiedene Datentypen, Escape-Zeichen und andere Überlegungen je nach spezifischen Anforderungen berücksichtigt werden.

### Wann welchen Tabellentyp verwenden(hashed, sorted, oder standard)

In ABAP werden unterschiedliche Tabellentypen verwendet, um den Anforderungen verschiedener Szenarien gerecht zu werden. Die Entscheidung für einen bestimmten Tabellentyp hängt von den Anforderungen der Anwendung ab. Hier sind die drei Haupttypen von internen Tabellen in ABAP und einige Richtlinien für ihre Verwendung:

- Standardtabelle (Standard Table):
  
  Verwendung: Verwendung, wenn die Datensätze in der Reihenfolge hinzugefügt wurden und die Reihenfolge beibehalten werden soll.
  Implementierung: DATA: lt_standard TYPE TABLE OF ....
  Beispiel: APPEND VALUE #(field1 = value1 field2 = value2) TO lt_standard.

- Sortierte Tabelle (Sorted Table):
  
   Verwendung: Verwendung, wenn die Datensätze nach einer bestimmten Reihenfolge sortiert sein müssen.
   Implementierung: DATA: lt_sorted TYPE SORTED TABLE OF ... WITH UNIQUE KEY ....
   Beispiel: INSERT VALUE #(field1 = value1 field2 = value2) INTO TABLE lt_sorted.

- Gehashte Tabelle (Hashed Table):
  
  Verwendung: Verwendung, wenn ein schneller Zugriff auf die Daten anhand eines eindeutigen Schlüssels erforderlich ist.
  Implementierung: DATA: lt_hashed TYPE HASHED TABLE OF ... WITH UNIQUE KEY ....
  Beispiel: lt_hashed[ key = value ] = value.

Die Wahl des Tabellentyps hängt von den spezifischen Anforderungen Ihrer Anwendung ab:

- Verwenden Sie eine Standardtabelle, wenn die Reihenfolge der Datensätze wichtig ist.
- Verwenden Sie eine Sortierte Tabelle, wenn Sie nach einem Schlüssel sortierte Daten benötigen.
- Verwenden Sie eine Gehashte Tabelle, wenn schnelle Zugriffe anhand eines eindeutigen Schlüssels erforderlich sind.

Es ist wichtig zu beachten, dass der Zugriff auf gehashte Tabellen in der Regel schneller ist als auf sortierte Tabellen, aber die Sortierung der Daten bei Bedarf erschwert wird. Daher sollte die Wahl des Tabellentyps sorgfältig basierend auf den spezifischen Anforderungen der Anwendung getroffen werden.

## 3.6 Code Inspector und Prüfung (Simon)

-        Verwendung des Code-Inspectors mit Regeln

-        SQL Trace (Performance Trace ST05)
