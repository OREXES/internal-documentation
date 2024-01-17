---
title: "3. SAP Besonderheiten"
description: "Besonderheiten in SAP Systemen"
summary: ""
weight: 812
---

# 3.    SAP-Besonderheiten

## 3.1 Funktionsbausteine (Lukas)

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

Defintion von Dynpros:

Dynamische Programme (Dynpros) sind ein zentrales Konzept in SAP ABAP

und dienen der Erstellung von interaktiven Benutzeroberflächen für SAP-                        Anwendungen. Dynpros ermöglichen die Gestaltung von Bildschirmen, auf denen Benutzer mit dem SAP-System interagieren können. Diese Bildschirme enthalten verschiedene Elemente wie Eingabefelder, Auswahllisten, Knöpfe und andere Steuerelemente, die dem Benutzer die Eingabe von Daten und die Navigation innerhalb der Anwendung ermöglichen.

Beispiel Dynpro aus den Benutzerantrag:

<!-- ![](file:///C:/Users/SIMONF~1/AppData/Local/Temp/msohtmlclip1/01/clip_image028.png)          -->

Strukturierte Oberfläche:

Dynpros ermöglichen eine logische und strukturierte Darstellung von Informationen, was es Benutzern erleichtert, sich in der Anwendung zurechtzufinden und die gewünschten Aufgaben auszuführen.

Flexibilität und Anpassungsfähigkeit:

Die Flexibilität von Dynpros erlaubt es Entwicklern, Bildschirme nach den spezifischen Anforderungen einer Anwendung zu gestalten. Dies ermöglicht eine hohe Anpassungsfähigkeit und die Berücksichtigung der Bedürfnisse verschiedener Benutzergruppen.

Interaktion und Rückmeldung:

Durch die Interaktion mit Dynpros erhalten Benutzer sofortige Rückmeldungen über ihre Eingaben oder Aktionen, was die Benutzererfahrung verbessert und Fehler minimiert.

Nahtlose Integration mit ABAP-Logik:

Dynpros sind eng mit der ABAP-Logik verbunden, was es ermöglicht, die eingegebenen Daten direkt zu verarbeiten und in den SAP-Systemen zu nutzen.

  

Was sind Selection-Screens?

Selection-Screens sind wichtige Werkzeuge in SAP ABAP, die es Benutzern ermöglichen, Eingabeparameter für Programme oder Funktionen festzulegen. Sie bieten eine interaktive Möglichkeit für Benutzer, die Ausführung von ABAP-Programmen zu steuern, indem sie spezifische Kriterien oder Filter festlegen, bevor das Programm ausgeführt wird.

Beispiel Selection-Screen aus den Reader:

<!-- ![](file:///C:/Users/SIMONF~1/AppData/Local/Temp/msohtmlclip1/01/clip_image030.png) -->

Warum Selection-Screens?

Der Hauptzweck von Selection-Screens besteht darin, Benutzern die Auswahl von Daten für die Verarbeitung durch ABAP-Programme zu ermöglichen. Sie dienen als Filtermechanismus, um relevante Datensätze aus einer großen Datenmenge auszuwählen.

Anpassungsfähigkeit und Flexibilität:

Selection-Screens bieten Flexibilität, da Benutzer verschiedene Parameter wie Benutzergruppe, Org-Einheiten Technische/Fachliche Rollen usw. festlegen können, um genau die Daten auszuwählen, die sie benötigen. Dies ermöglicht eine breite Anpassungsfähigkeit an verschiedene Anforderungen.

Benutzerinteraktion und Kontrolle:

Sie bieten eine interaktive Benutzeroberfläche, über die Benutzer direkt mit dem Programm interagieren können, indem sie Werte eingeben oder auswählen, um das Ergebnis des Programms zu beeinflussen. Dadurch erhalten Benutzer mehr Kontrolle über die Verarbeitung der Daten.

Optimierung der Programmausführung:

Durch die Nutzung von Selection-Screens können Programme effizienter ausgeführt werden, da sie nur die vom Benutzer ausgewählten Daten verarbeiten müssen. Dies trägt dazu bei, die Ausführungszeiten zu verkürzen und die Systemressourcen besser zu nutzen.

Fehlerminimierung und Datenvalidierung:

Selection-Screens ermöglichen auch die Validierung von Benutzereingaben, bevor das Programm ausgeführt wird. Dadurch können Fehler vermieden werden, indem ungültige Eingaben abgefangen und Benutzer aufgefordert werden, korrekte Werte einzugeben.

  

Wo können SELECTION-SCREENS verwendet werden?

Selection-Screens können direkt in ABAP-Reporten erstellt werden. Bei der Erstellung oder Bearbeitung eines Reports in der ABAP Workbench kann der Entwickler Selection-Screen-Anweisungen hinzufügen, um den interaktiven Bildschirm zu definieren. Selection-Screens können auch in anderen Objekten wie Funktionsbausteinen, Methoden, Include-Programmen usw. definiert und verwendet werden, um Eingabeparameter oder -filter festzulegen.

Wie erstelle ich einen SELECTION-SCREEN?

Innerhalb des Programms oder der Komponente können Anweisungen zur Definition des Selection-Screens verwendet werden. Einige wichtige Anweisungen sind:

SELECTION-SCREEN BEGIN OF SCREEN ... END OF SCREEN: Definiert den Anfang und das Ende des Selection-Screens.

PARAMETERS: Definiert Parameter für Benutzereingaben.

SELECT-OPTIONS: Definiert Auswahlkriterien für Benutzer.

SELECTION-SCREEN COMMENT: Fügt Kommentare oder Erläuterungen zum Selection-Screen hinzu.

Beispiel SELECTION-SCREEN Block B1A aus dem Reader:

<!-- ![](file:///C:/Users/SIMONF~1/AppData/Local/Temp/msohtmlclip1/01/clip_image032.png) -->

  

### Erstellung und Gestaltung von Benutzeroberflächen

Auswahl des Entwicklungselements:

Um mit der Erstellung und Gestaltung von Dynpros zu beginnen muss zunächst ein neues Dynpro innerhalb eines Entwicklungselements erstellt werden. Typischerweise ist dies ein Paket oder eine Entwicklungsklasse.

Neues Dynpro erstellen:

Auf das ausgewählte Entwicklungselement =>"Neu"=>"Dynpro" aus dem Dropdown-Menü, um einen neues Dynpro zu erstellen. Nachdem die grundlegenden Informationen für das neue Dynpro eingegeben wurden, wird der Screen Painter geöffnet, indem das neu erstellte Dynpro ausgewählt wird. Mit einem Doppelklick darauf oder über die Schaltfläche "Screen Painter" in der Werkzeugleiste.

Arbeiten im Screen Painter:

Der Screen Painter ist nun geöffnet und es kann mit der Gestaltung des Dynpros begonnen werden. Hier ist es möglich Elemente wie Textfelder, Eingabefelder, Auswahllisten usw. auf dem Bildschirm platzieren und das Layout des Dynpros gestalten.

Dynpro-Nummer:

Jedes Dynpro wird durch eine eindeutige Nummer identifiziert, die seine Position innerhalb eines SAP-Systems angibt. Diese Nummer wird zur Navigation und Steuerung zwischen verschiedenen Bildschirmen verwendet.

<!-- ![](file:///C:/Users/SIMONF~1/AppData/Local/Temp/msohtmlclip1/01/clip_image034.png) -->

Subscreens:

Ein Subscreen ist ein separater Bildschirm (Dynpro), der in einen anderen Dynpro eingebettet wird, um spezifische Informationen anzuzeigen oder Funktionen bereitzustellen.

Subscreens werden verwendet, um Teile der Benutzeroberfläche zu modularisieren, wodurch die Wiederverwendung von Bildschirminhalten und die Trennung von logischen Teilen der Benutzeroberfläche ermöglicht werden. Ein Subscreen wird in einem Containerbereich eines Hauptdynpros platziert und dort angezeigt. Die Anzeige eines Subscreens kann dynamisch während der Laufzeit eines Dynpros gesteuert werden. Daten können zwischen dem Hauptdynpro und dem Subscreen ausgetauscht werden, ähnlich wie bei der Datenbindung zwischen verschiedenen Teilen desselben Dynpros. Um einen Subscreen in einem Hauptdynpro zu definieren und einzubetten, wird die DEFINITION SCREEN-Anweisung verwendet. Subscreens können zur Laufzeit eines Dynpros über ABAP-Code hinzugefügt, geändert oder entfernt werden.

  

Layout:

Das Layout eines Dynpros wird im Screen Painter erstellt. Es umfasst die visuelle Anordnung der Bildschirmelemente wie Textfelder, Eingabefelder, usw. Hier wird festgelegt, wie die Elemente auf dem Bildschirm angeordnet sind und wie sie miteinander interagieren.

<!-- ![](file:///C:/Users/SIMONF~1/AppData/Local/Temp/msohtmlclip1/01/clip_image036.png)  -->

Bildschirm-Elemente eines Dynpros:

Textfelder: Zur Anzeige von Texten oder Beschriftungen.

Eingabefelder: Zum Erfassen von Benutzereingaben wie Zahlen, Texten oder anderen Daten.

Auswahlelemente: Wie Checkboxen, Auswahllisten oder Radiobuttons, um Benutzern Auswahlmöglichkeiten zu bieten.

Funktions- und Navigationsleisten: Enthalten Schaltflächen für Aktionen wie Speichern, Zurück, etc.

<!-- ![](file:///C:/Users/SIMONF~1/AppData/Local/Temp/msohtmlclip1/01/clip_image038.png) -->

  

Flow-Logic (Ablauflogik):

Die Flow-Logic eines Dynpros definiert die Verarbeitungslogik, die auf Benutzeraktionen oder -eingaben reagiert. Diese Logik umfasst ABAP-Code, der festlegt, wie das System auf Ereignisse wie Klicken von Schaltflächen oder Eingabe in Felder reagiert.

<!-- ![](file:///C:/Users/SIMONF~1/AppData/Local/Temp/msohtmlclip1/01/clip_image040.png) -->

PBO (Process Before Output):

Die PBO-Logik definiert, was vor der Anzeige des Dynpros geschehen soll. Hier werden Initialisierungen von Variablen, Vorbelegungen von Feldern oder andere Vorbereitungen für die Anzeige durchgeführt.

PAI (Process After Input):

Die PAI-Logik wird ausgeführt, wenn der Benutzer mit dem Dynpro interagiert und eine Aktion ausführt. Hier wird festgelegt, wie das System auf Benutzeraktionen reagiert, z.B. wenn ein Button geklickt oder ein Eingabefeld ausgefüllt wird.

Verbindung mit ABAP-Programmen:

Ein Dynpro ist eng mit einem ABAP-Programm verbunden, das die Logik für die Verarbeitung von Daten und Ereignissen auf dem Dynpro enthält. Die Kommunikation zwischen dem Dynpro und dem zugehörigen ABAP-Programm erfolgt über Module und Funktionen.

  

### Ansteuern von Dynpros (CALL SCREEN, SKIP TO SCREEN, LEAVE SCREEN etc.)

In der SAP ABAP-Programmierung dienen CALL SCREEN, SKIP TO SCREEN und LEAVE SCREEN dazu, die Steuerung und Navigation zwischen verschiedenen Dynpros innerhalb einer ABAP-Anwendung zu ermöglichen. Hier sind die Unterschiede und Verwendungszwecke dieser Befehle:

CALL SCREEN

Der CALL SCREEN Befehl wird verwendet, um einen anderen Dynpro innerhalb desselben Programms aufzurufen und anzuzeigen. Es handelt sich um einen synchronen Aufruf, bei dem die Steuerung an den aufgerufenen Bildschirm übergeben wird. Nach der Verarbeitung des aufgerufenen Dynpros kehrt das Programm zur Verarbeitung an die Stelle zurück, von der aus der CALL SCREEN-Befehl aufgerufen wurde. Daten können zwischen dem aufrufenden Dynpro und dem aufgerufenen Dynpro über sogenannte „Export“- und „Import“-Parameter ausgetauscht werden.

Beispiel: CALL SCREEN <Dynpro-Nummer>.

SKIP TO SCREEN

Der SKIP TO SCREEN Befehl dient dazu, die Steuerung an einen anderen Bildschirm zu übergeben, ohne die aktuellen Änderungen zu speichern oder zu verarbeiten. Es handelt sich um einen asynchronen Sprung, bei dem die aktuelle Verarbeitung abgebrochen wird und direkt zum aufgerufenen Bildschirm gesprungen wird, ohne Daten zu übergeben oder zu verarbeiten. Es wird häufig für Navigationen innerhalb von Reports verwendet, ohne eine spezifische Datenverarbeitung durchzuführen.

Beispiel: SKIP TO SCREEN <Dynpro-Nummer>.

LEAVE SCREEN

Der LEAVE SCREEN Befehl wird verwendet, um den aktuellen Bildschirm zu verlassen und zur Steuerung an den aufrufenden Bildschirm zurückzukehren. Es handelt sich um einen Befehl, der verwendet wird, um die aktuelle Verarbeitung zu unterbrechen und zum aufrufenden Bildschirm zurückzukehren. Er wird genutzt, wenn Änderungen im aktuellen Bildschirm nicht gespeichert oder verarbeitet werden sollen.

Beispiel: LEAVE SCREEN.

Zusammenfassung der Unterschiede:

CALL SCREEN: Synchroner Aufruf eines anderen Dynpros innerhalb desselben Programms mit Datenübertragung und Rückkehr zur Verarbeitung.

SKIP TO SCREEN: Asynchroner Sprung zu einem anderen Dynpro ohne Datenübertragung und sofortige Abbruch der aktuellen Verarbeitung.

LEAVE SCREEN: Unterbrechung der aktuellen Verarbeitung und Rückkehr zum aufrufenden Bildschirm ohne Speicherung oder Verarbeitung der aktuellen Änderungen.

  

Weitere Befehle:

Neben den bereits besprochenen Befehlen wie CALL SCREEN, SKIP TO SCREEN und LEAVE SCREEN gibt es noch weitere relevante Befehle, im Zusammenhang mit Dynpros verwendet werden können:

SET SCREEN

Der SET SCREEN Befehl ermöglicht die Aktivierung oder Deaktivierung von Bildschirmelementen (z.B. Feldern, Buttons) während der Laufzeit eines Dynpros. Durch SET SCREEN können Sie dynamisch die Anzeige- oder Bearbeitungsattribute von Feldern steuern, je nachdem, wie der Programmablauf fortschreitet.

Beispiel: SET SCREEN <Element-ID> PROPERTY <Eigenschaft> = <Wert>.

LOOP AT SCREEN

Mit LOOP AT SCREEN können Sie über alle Bildschirmelemente eines Dynpros iterieren und bestimmte Operationen durchführen. Dieser Befehl ermöglicht die dynamische Bearbeitung von Bildschirmelementen während der Laufzeit, z.B. das Setzen von Eigenschaften oder das Ausblenden von Feldern basierend auf bestimmten Bedingungen.

Beispiel: LOOP AT SCREEN. ... ENDLOOP.

CLEAR SCREEN

Der Befehl CLEAR SCREEN löscht alle Daten und setzt die Bildschirmelemente eines Dynpros zurück. Er dient dazu, die angezeigten Informationen zu löschen und den Bildschirm in einen Ausgangszustand zurückzusetzen.

Beispiel: CLEAR SCREEN.

## 3.3 Debugging (Lukas)

### Grundlagen des Debuggings in ABAP

Der Debugger ermöglicht zur Laufzeit eine Codeanalyse von ABAP-Programmen, Funktionsbausteinen und Web Dynpros u. a. Das Coding kann hier zeilen- und modulabschnittsweise durchlaufen werden. Der Codingablauf kann während der Laufzeit inklusive der Variablenwerte analysiert werden.

<!-- ![Ein Bild, das Text, Screenshot, Software, Computersymbol enthält. -->
<!-- Automatisch generierte Beschreibung](file:///C:/Users/SIMONF~1/AppData/Local/Temp/msohtmlclip1/01/clip_image042.jpg) -->

In der Standardsicht ist der Debugger in drei Teile aufgeteilt: Links (1) sieht man den Quelltext, der gerade durchlaufen wird. Rechts oben (2) ist der sogenannte Aufrufstack zu sehen. Dies ist eine hierarchische Auflistung der Programmteile, Methoden oder Funktionsbausteine, die bereits durchlaufen wurden. Unter dem Aufrufstack (3) können Variablen, Tabellen, etc. angezeigt werden. Diese können entweder eingetragen oder durch einen Doppelklick im Quelltext geladen werden.

Mit den folgenden Buttons kann durch das Programm debuggen:

  
<!-- ![](file:///C:/Users/SIMONF~1/AppData/Local/Temp/msohtmlclip1/01/clip_image044.png) -->

<!-- ![](file:///C:/Users/SIMONF~1/AppData/Local/Temp/msohtmlclip1/01/clip_image045.png) -->

·        **Einzelschritt (F5)**: _springt_ einen _Schritt_ weiter, also von Anweisung zu Anweisung

·        **Ausführen (F6)**: _überspringt_ Funktionsbaustein, Methoden, Unterprogramme, etc.; diese Programmteile werden aber trotzdem durchlaufen; man bleibt auf derselben Ebene des Aufrufstacks

·        **Return (F7)**: _verlässt_ den aktuellen Programmteil; auch werden nachfolgende Programmteile noch durchlaufen

·        **Weiter (F8)**: _verlässt_ den Debugger; Programmteile werden aber noch durchlaufen

### Breakpoints

Es gibt verschiedene Möglichkeiten bei der Programmausführung in den Debugger zu wechseln

·       "/h" im Kommandofenster eingeben. Der Debugger wird sofort am Anfang des Programms ausgeführt. Empfehlenswert, wenn das Programm vom Programmstart an debuggt werden soll.  
  

·       "/hs" im Kommandofenster eingeben. Der Debugger wird sofort am Anfang des Programms gestartet, inklusive der Programmteile, die den Status "Systemprogramm" haben. Das Systemdebugging ist normalerweise nicht notwendig. Wenn jedoch ein Programm debuggt werden soll, was den Status "Systemprogramm" hat, dann macht dieser Debuggingmodus Sinn.

Eine weitere Möglichkeit den Debugger aufzurufen ist via das Kommando _„break“_

·       _„break <benutzername>“_ im Coding schreiben. Das Programm stoppt nur beim SAP-Benutzer <benutzername>. Empfehlenswert, wenn das Programm an einer bestimmten Stelle in den Debugger springen soll und man selbst das Programm debuggen will. Hier ist es auch meist unproblematisch, wenn man vergisst den Breakpoint bei einem Transport zu löschen, da bei anderen SAP-Usern der Sprung in den Debugger nicht erfolgt.  
  

·       _„break-point“_. Hier springt das Programm bei jedem SAP-Benutzer mit Debuggerberechtigung in den Debugger. Es ist dringend zu empfehlen diesen Befehl nur mit Vorsicht zu nutzen. Es ist unangenehm und wirkt unprofessionell, wenn im Qualitäts- oder Produktivsystem andere Benutzer oder gar der Fachwender mit Debuggerberechtigung ungewollt in den Debugger springen. Hier ist z. B. "break <benutzername> vorzuziehen. Vor jedem Transport ins Qualitätssystem und besonders in Produktivsystem sollte das Code um diese Breakpoints „break-point“ bereinigt werden. Noch besser ist es sie gar nicht zu verwenden. Dann kann es auch nicht vergessen werden sie zu löschen.  
  

·       _“Break-point id <Checkpoint-Gruppe>”_ In der Transaktion SAAB kann man Checkpoint-Gruppen definieren. Im Coding kann man auf diese Checkpoint-Gruppe verweisen. In der Transaktion SAAB kann man dann für diese Checkpoint-Gruppe einstellen, ob dieser dynamische Break-Point an dem Tag aktiv sein soll. Das Programm spring dann für den eigenen User an dem heutigen Datum in dem aktuellen System in den Debugger, sofern die Debugging-Berechtigung vorhanden ist. Ganz praktisch ist es auch, dass SAP viele Checkpoint-Gruppen angelegt hat, die man selbst auch im Qualitäts- oder Produktiv-System aktivieren kann.

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

## 3.4 Lokale und globale Datentypen (Lukas)

-        Unterschied zwischen lokalen und globalen Datentypen in ABAP

-        Verwendung und Anwendung von Datentypen, dynamische Typen

-        Suchhilfen

-        Anlegen von lokalen und globalen Datentypen, Domänen, Tabellentypen, Strukturen

## 3.5 SQL Advanced Techniques (Lukas)

-        Joins, LIKE %, IN, Verwendung von dynamischen Typen

-        Dynamische Erstellung von Tabellen

-        Dynamischer Aufruf von Funktionsbausteinen

-        Dynamische WHERE-Aufrufe

-        Wann welcher Tabellentyp (hashed, sorted, oder standard)

## 3.6 Code Inspector und Prüfung (Simon)

-        Verwendung des Code-Inspectors mit Regeln

-        SQL Trace (Performance Trace ST05)
