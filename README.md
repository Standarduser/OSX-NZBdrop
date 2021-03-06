# OSX-NZBdrop
**Allgemein**

NZBdrop ist ein Automator-Workflow (Ordneraktion) für den Mac, der heruntergeladene NZB-Dateien aus dem Download-Ordner des Mac 
(des aktuellen Benutzers) auf einen externen Server/NAS verschiebt.

**Hintergrund**

Usenet-Downloader wie NZBget oder SABnzbd verfügen über die Möglichkeit, NZB-Downloads in Kategorien einzusortieren, 
beispielsweise um sie je nach Art der gewünschten Datei unterschiedlich beim Post Processing behandeln zu können. Dies dient 
unter anderem dazu, eine Episode einer Serie anders behandeln zu können, als einen Film.

Auf Dateiebene lassen sich diese Kategorien ansprechen, indem im sogenannten Blackhole (dem Empfangsverzeichnis für NZB-Dateien) 
Unterordner angelegt werden, deren Namen den zugehörigen Kategorienamen entsprechen.

Jeder Download, der beispielsweise durch eine NZB-Datei aus dem Unterordner "Serie" erfolgt, wird automatisch der Kategorie 
Serie zugeordnet und entsprechend behandelt. Vorraussetzung dafür ist lediglich, dass die Kategorien entsprechend in den 
Einstellungen des jeweiligen Downloaders angelegt wurden.

**Funktionsweise**

Der ausgewählte Ordner (~/Downloads) wird auf neue Dateien überwacht. Bei einer Änderung des Ordnerinhaltes wird der Workflow
angetriggert, filtert aus den Dateien das .NZB-File heraus und übergibt das Ergebnis an den weiteren Verlauf.

Ist keine neue .NZB-Datei gefunden worden, wird der Workflow an dieser Stelle beendet.

Wurde eine .NZB-Datei gefunden, öffnet sich ein Dialog, in dem die Kategorie ausgewählt werden muss. Anschließend wird eine
Verbindung zum Server/NAS hergestellt und entsprechend der Auswahl die .NZB-Datei in den Unterordner, passend zur Kategorie, 
verschoben. Am Ende wird die Verbindung zum Server/NAS wieder getrennt.

**Einschränkungen**

Da der Teil für die Zuordnung der Kategorien auf AppleScript basiert und ein Dialogfeld maximal 3 Schaltflächen aufnehmen kann,
ist die Anzahl der Kategorien auf maximal 3 Stück beschränkt.

**Notwendige Anpassungen**

Im fünften Abschnitt (AppleScript ausführen) müssen zwischen den Zeilen 5 und 15 die Kategorien entsprechend dem Bedarf
angepasst werden.

**Bekannte Probleme**

Von Zeit zu Zeit dauert es etwas länger, bis der Workflow angetriggert wird. Sind in dieser Zeit mehrere neue .NZB-Dateien hinzu
gekommen, kann es passieren, dass entweder
- der Workflow mehrfach angetriggert wird und sich mehrere Dialoge überlagern, oder
- mehrere .NZB-Dateien mit nur einer Auswahl einer bestimmten Kategorie zugeordnet werden

Da diese Funktion über Automator/OS X ausgeführt wird, lässt sich das leider nicht beeinflussen.
