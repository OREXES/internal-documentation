---
title: "5. Bonus"
description: "Zusatzinformationen"
summary: ""
weight: 817
---

## 5.1 Programmierstil (Simon)

-        Für die Erstellung von sauberem und wartbarem ABAP-Code gibt es verschiedene Richtlinien und Best Practices, die sich an den Prinzipien von "Clean Code" orientieren. Hier sind einige Schlüsselregeln mit Beispielen:

-        Klare und aussagekräftige Benennung: Variablen, Methoden und Klassen sollten so benannt werden, dass sie ihre Funktion oder ihren Zweck klar beschreiben. <br>   Beispiel: Verwende “kundenNummer” anstelle von knr für eine Variable, die eine Kundennummer darstellt.

-        Vermeidung von globalen Variablen: Globale Variablen sollten vermieden werden, da sie die Lesbarkeit und Wartbarkeit des Codes beeinträchtigen können.  
          Beispiel: Nutze lokale Variablen innerhalb von Funktionen oder Methoden anstatt globale Variablen.

-        Einhaltung der SOLID-Prinzipien: Diese Prinzipien fördern unter anderem die Modularität und Wiederverwendbarkeit des Codes.  
          Beispiel: Implementiere das Single-Responsibility-Prinzip, indem du sicherstellst, dass jede Klasse oder Methode nur eine Aufgabe erfüllt.

-        Konsistente Formatierung: Einheitliche Formatierung des Codes verbessert die Lesbarkeit.  
          Beispiel: Halte dich an eine konsistente Einrückung und verwende Leerzeilen, um logische Abschnitte im Code zu trennen.

-        Vermeidung von tief verschachtelten Strukturen: Tiefe Verschachtelungen erschweren das Verständnis des Codes.  
          Beispiel: Verwende frühzeitige Rückkehr (RETURN) in Methoden, um tief verschachtelte IF-Anweisungen zu vermeiden.

-        Kommentare und Dokumentation: Kommentare sollten genutzt werden, um komplexe Logik zu erläutern, aber nicht, um schlechten Code zu erklären.  
          Beispiel: Schreibe klare Kommentare für komplexe Algorithmen, vermeide aber Kommentare für Selbstverständlichkeiten.

-        Effiziente Nutzung von SAP-spezifischen Sprachkonstrukten: ABAP bietet viele spezifische Konstrukte, die effizient genutzt werden sollten.  
          Beispiel: Verwende READ TABLE mit einer binären Suche, wenn möglich, anstelle einer linearen Suche.

-        Vermeidung von Magic Numbers: Verwende Konstanten anstelle von direkten Zahlenwerten im Code.  
          Beispiel: Ersetze einen direkten Zahlenwert wie 3 durch eine Konstante mit einem beschreibenden Namen, z.B. MAX_RETRY_COUNT.

-        Fehlerbehandlung: Implementiere robuste Fehlerbehandlungsmechanismen.  
          Beispiel: Verwende Try-Catch-Blöcke, um Ausnahmen zu behandeln und sinnvolle Fehlermeldungen zurückzugeben.

## 5.2 Transportmanagement (Lukas)

### 5.2.1       Systemlandschaften

Die typische SAP-Landschaft besteht aus drei Systemebenen. Für die Systemsicherheit und die Qualitätssicherung wird die Verwendung der verschiedenen Systeme empfohlen. Die Systemlandschaft besteht aus dem Entwicklungssystem, dem Testsystem oder Qualitätssicherungssystem und dem Produktivsystem.

·        Entwicklungssystem (auch DEV abgekürzt): Auf dem Entwicklungssystem werden Entwicklungen und das Customizing vorgenommen  
·        Qualitätssicherungssystem (Abkürzung: QAS): Hier werden die Geschäftsprozesse anhand realer Testdaten getestet  
·        Produktivsystem (Abkürzung: PRD): Dieses System dient als Arbeitsmandant. Es wird vom Endanwender für das Tagesgeschäft genutzt

Transporte sind notwendig, um Entwicklungsprojekte vom Entwicklungssystem auf das Test- oder Produktivsystem zu transportieren. Die Architektur der drei Systemebenen folgt der einer Einbahnstraße. Diese Einbahnstraßen werden auch Transportwege genannt. Es ist möglich gezielt einzelne Objekte für einen Transport auszuwählen oder bestimmte Objekte zu einer vordefinierten Auswahl zu transportieren.

### 5.2.2       Transporte

Die Transaktionen SE01 oder SE09 werden als „Transport Organizer“ beschrieben. Mit ihnen können Customizing- und Workbench-Aufträge angelegt werden und liefern die Übersicht über die Aufträge und die Beschreibung der Aufgabe.
Customizing- und Workbench-Aufträge sind verschiedene Typen von Änderungsaufträgen. Mit einem Customizing-Auftrag werden mandantenabhängige Änderungen (z.B. bei Rollen) vorgenommen. Ein Workbench-Auftrag wird hingegen für mandantenunabhängiges Customizing verwendet. Workbench-Aufträge werden für alle Repository-Objekte der ABAP Workbench genutzt. SAP-Systeme können in Mandanten aufgeteilt werden. Kundendaten sind beispielsweise immer mandantenabhängig, da diese eine bestimmte Agilität vorweisen müssen, da z.B. bestimmte Einstellungen nur für gewisse Kunden gelten. Mandantenunabhängiges Customizing beschreibt Einstellungen, die für alle Mandanten im SAP-System gleichermaßen gelten.

<!-- ![Ein Bild, das Text, Screenshot, Diagramm, Schrift enthält. -->
<!-- Automatisch generierte Beschreibung](file:///C:/Users/SIMONF~1/AppData/Local/Temp/msohtmlclip1/01/clip_image069.png) -->

### 5.2.3       Anlegen eines Transports

Zu Beginn muss der „Transport Organizer“ geöffnet werden. Dann kann über den „Anlegen“-Button (F6) oben rechts das Anlagefenster des Transports geöffnete werden.

<!-- ![](file:///C:/Users/SIMONF~1/AppData/Local/Temp/msohtmlclip1/01/clip_image071.jpg) -->

Darauf wird die eine Auswahl an Aufträgen angezeigt, die angelegt werden können. Nach der Auswahl öffnet sich ein weiters Fenster wo ein Titel, ein Projekt (relevant für ein Charm Prozess) und ein Ziel (Systemspezifisch oder ein Transportweg). Im untern Fenster Aufgaben kann für weitere Benutzer eine Aufgabe im Auftrag angelegt werden.

<!-- ![Ein Bild, das Text, Screenshot, Zahl, Diagramm enthält. -->
<!-- Automatisch generierte Beschreibung](file:///C:/Users/SIMONF~1/AppData/Local/Temp/msohtmlclip1/01/clip_image073.png) -->

Der fertig angelegte Transport wird nach dem Speichern direkt angezeigt.

<!-- ![Ein Bild, das Text, Screenshot, Schrift, Zahl enthält. -->
<!-- Automatisch generierte Beschreibung](file:///C:/Users/SIMONF~1/AppData/Local/Temp/msohtmlclip1/01/clip_image075.png) -->

### 5.2.4       Versionierung

Die Versionshistorie zeigt den Verlauf von Anpassungen an einem Repository-Objekt an. Sie steht in den meisten Transaktionen, die mit APAP-Code arbeiten zur Verfügung, z.B. dem Object Navigator (SE80), dem ABAP Editor (SE38), dem Class Builder (SE24) oder dem Function Builder (SE37) zu Verfügung.
Sie lässt sich am oberen Bildschirmrand über den Reiter Hilfsmittel → Versionen → Versionsverwaltung öffnen, wie im nachfolgenden Bild zu sehen. Am besten öffnet man die Versionsverwaltung im Entwicklungssystem, da hier eine vollständige Liste angezeigt wird.

  
  
<!-- ![](file:///C:/Users/SIMONF~1/AppData/Local/Temp/msohtmlclip1/01/clip_image077.jpg) -->

Darauf öffnet sich das nachfolgende Fenster.

<!-- ![Ein Bild, das Text, Screenshot, Schrift, Zahl enthält. -->
<!-- Automatisch generierte Beschreibung](file:///C:/Users/SIMONF~1/AppData/Local/Temp/msohtmlclip1/01/clip_image079.jpg) -->

Nun kann durch das Markieren der jeweiligen Zeilen und das Verwenden der verschiedenen Funktionen in der Kopfzeile vergleichen werden.  
  
[[LS1]](#_msocom_1) 

-        Aufträge und Sperrung/Entsperrung

Beteiligung: Colin, Joemar

Review: Andreas, Johannes

---

 [[LS1]](#_msoanchor_1)Eventuell noch die verschiedenen Funktionen erklären
