# Sicherheit
von André Sommer am 01.02.2024

Unter IT-Sicherheit versteht man im Allgemeinen den Schutz von Daten. Dabei geht es zum einem um den Schutz vor fremden Zugriff aber auch den Schutz vor Datenverlust.

## Bundesamt für Sicherheit und Informationstechnik (BSI)
Das BSI wurde von der Bundesregierung  1991 mit dem "Gesetzes über die Errichtung des Bundesamtes für Informationstechnik" geschaffen. Es hat drei Aufgaben:
- Gewährleistung der Sicherheit für das Regierungsnetz
- Gewährleistung der Sicherheit für kritische Infrastruktur
- Warnung der Bevölkerung vor Sicherheitslücken
- Setzen von Mindeststandards

## Schadsoftware
- **Virus:** Wie echte Viren benötigen Computerviren ein Wirtsprogramm, mit dem sie ausgeführt werden.
- **Wurm:** Würmer kommen ohne Wirtsprogramm aus und können sich möglicherweise von selbst über das Netzwerk oder Mailverkehr weiter verbreiten.
- **Trojaner:** Eine sinnvolle Anwendung, die aber im Hintergrund Schadsoftware enthält.
- **Botnet:** Ein zumeist Zusammenschluss von (zumeist infizierten) Clients, um "Denial of Service" Angriffe durchzuführen
- **Harvester:** Durchforstet Webseiten nach persönlichen Daten.

## Spamformen
- **Scam:** Unter falschem Namen oder falschem Vorwand wird Geld oder eine Ware verlangt oder erpresst.
- **Hoax:** Falschinformationen, die oft mit der Aufforderung verbunden sind diese weiter zu leiten.
- **Phishing:** Unter falschem Namen oder falschem Vorwand werden Informationen erfragt oder Wischen den Zeilen erlangt.

## Vertraulichkeit, Integrität, Verfügbarkeit, Authentizität (VIVA)
- **Vertraulichkeit:** Beschreibt den Schutz vor unerlaubtem Zugriff (Sicherstellung beispielsweise durch Verschlüsselung von Daten).
- **Integrität:** Beschreibt den Schutz der Daten vor unerlaubter Veränderung.
- **Verfügbarkeit:** Beschreibt die Ausfallsicherheit der Datenbereitstellung
- **Authentizität:** Beschreibt die Zuordbarkeit und Nachvollziehbarkeit von Handlungen

## Verschlüsselungsverfahren

### Symmetrische Verschlüsselung
Bei  Verschlüsselung wird mit dem **gleichen** Schlüssel **verschlüsselt** und **entschlüsselt**. Ein Beispiel hierfür ist die Cäsarverschlüsselung.

### Asymmetrische Verschlüsselung
Bei Verschlüsselung wird mit einem **Public-Key** verschlüsselt und mit dem **Private-Key** entschlüsselt. Hierbei kann der Public-Key verteilt werden, da sich die Nachricht mit ihm zwar ver- aber nicht wieder entschlüsseln lässt und er keine Rückschlüsse auf den Private-Key zulässt. Ein Beispiel hierfür ist das RSA-Verfahren, bei diesem werden die Keys durch zwei Primzahlen generiert.

### Hashing
Beim Hashing kann nur eine Hashsumme errechnet werden, es gibt keine Möglichkeit den ursprünglichen Inhalt aus diesem Hash wiederherzustellen. Dies ist zum Beispiel für Passwörter sinnvoll. Hier werden die Passwörter gehashed gespeichert und beim Login wird das Login-Passwort gehashed und nachfolgend mit dem gespeicherten Passworthash aus der Datenbank verglichen. Bei Passwörtern ist wichtig, dass es keine Hashkollisionen gibt. Ein Beispiel für einen aktuellen Hashingalgorithmus ist SHA-256.

### Sicherheitsvorkehrungen
- **Monitoring:** Infrastruktur wird über ein System überwacht, welches bei merkwürdigen Verhaltensmustern von Usern, Datenverarbeitungen, zu vielen Zugriffen oder Überlastung, Alarm schlägt.
- **Passwort-Manager:** Ein Verwaltungsprogramm für Passwörter um möglichst für jeden Dienst ein anderes Passwort zu verwenden ohne sich die Passwörter merken zu müssen.
- **Zwei-Faktor-Authentifikation (2FA):** Es müssen zur Authentifizierung zwei der drei Faktoren - Wissen (z.B. Passwort), Identität (z.B. Fingerabdruck), Besitz (z.B. Mobiltelefon) - zur Anmeldung benutzt werden. Dies geschieht meist über eine externe App, welche zeitgebundene Anmeldecodes ausgibt.

## Firewall
Eine Firewall ist ein System (Server oder Router), welches in der Lage ist Netzwerkverkehr zu analysieren und gegebenenfalls zu sperren. Für Sperrungen gibt es verschiedene Strategien:
- Alles erlauben und nur verdächtiges sperren (Blacklisting).
- Alles verbieten und nur bekanntes erlauben (Whitelisting).

### Firewallingtechniken
- Paketfilter
- Stateful Packet Inspection
- Deep Packet Inspection

### NGFW-Häufige Features
- URL-Filter
- VPN
- Content-Filter
- Network Address Translation (Nicht zwingend Firewall-Funktionalität. Eher Gateway/Router, welches häufig in NGFWs integriert.)
- Proxyfunktion (Proxy übernimmt als "Zwischenstation" Kommunikation mit dem Zielserver im "Auftrag" des Clients. Hierbei kann dann der Traffic überdies gescannt/blockiert werden).
- Autentifikation (Meist nach 802.1X)
- Virenscanner

### Filterung
- **Paketfilter:** Überprüft stateless TCP- und IP-Header.
- **Stateful Packet Inspection (SPI):** Überprüft ob es mit bisherigen Verbindungen zu Mustern bei den TCP- und IP-Headern kommt.
- **Circuit-Level Gateway:**  Überprüft bei aufrecht erhaltenen Verbindungen nur bei der Verbindungsherstellung
- **Deep Packet Inspection (DPI):** Überprüft auch den Inhalt von TCP-Segmenten
- **Application Gateway:** Arbeitet als Proxy und filtert so den Inhalt von Verbindungen
- **Next Generation Firewalls:** Überprüft auch nach Zertifikaten und Malwaremustern

## Schutzbedarf
Hierbei wird analysiert, wie schutzbedürftig eine IT-Komponente ist, beziehungsweise was passiert, wenn eine der VIVA-Schutzdefinitionen verletzt werden. Um dies zu verhindern gibt es Sicherheitsrichtlinien (Security Policy). Diese definitiert sowohl Verhaltensregeln der Mitarbeiter, diese müssen von allen Mitarbeitern des Unternehmens zur Kenntnis genommen werden. Eine Vernachlässigung der Sicherungspflicht wird sanktioniert und kann nach DSGVO je nach Schwere der Folgen zu empfindlichen Geldbußen und selbst zu Haftstrafen führen.

Die Schutzbedürftigkeit wird in drei Kategorien angegeben:
- **Normal: Die Schadensauswirkungen sind begrenzt und überschaubar**
  - Der mögliche finanzielle Schaden ist kleiner als 50.000 Euro
  - Ausfallzeiten von mehr als 24 Stunden werden hingenommen 
- **Hoch: Die Schadensauswirkungen können beträchtlich sein**
  - Der mögliche finanzielle Schaden liegt zwischen 50.000 Euro und 500.000 Euro
  - Ausfallzeiten dürfen maximal 24 Stunden betragen
- **Sehr hoch: Die Schadensauswirkungen können ein existenziell bedrohliches und katastrophales Ausmaß erreichen**
  - Der mögliche finanzielle Schaden ist größer als 500.000 Euro
  - Ausfallzeiten dürfen maximal zwei Stunden betragen

Der mögliche Schaden ergänzt sich außerdem nach:
- Verstößen gegen Gesetze und Verträge
- Beeinträchtigungen
  - informationellen Selbstbestimmungsrechts
  - persönliche Unversehrtheit
  - Aufgabenerfüllung
- negative Innen- und Außenwirkung
- finanzielle Auswirkungen

Vererbung von Schutzbedarf:
- **Maximalprinzip:** Der höchste Schutzbedarf aller Anwendungen wird auf das Gesamtsystem übernommen.
- **Betrachtung von Abhängigkeiten:** Schutzbedarf überträgt sich auf Abhängigkeiten.
- **Kumulationseffekt:** Der Schutzbedarf aller Anwendungen als Verbund kann höher sein als die Anwendungen einzeln beanspruchen.
- **Verteilungseffekt:** Verteilung einer Anwendung mit Schutzbedarf sorgt für ein verteilteres Risiko, und somit einen geringeren Bedarf der Einzelkomponenten.

## Backup

### Vollsicherung
Eine vollständige Sicherung aller zur sichernden Daten. Eine Vollsicherung ist entsprechend rechenintensiv und kann lange dauern. Außerdem ist die Vollsicherung entsprechend so groß wie die Größe der zu sichernden Daten (oder kleiner durch Kompression).

### Differenzielle Sicherung
Eine Sicherung, die alle Änderungen sichert, die seit der letzten Vollsicherung aufgetreten sind. Dieses Vorgehen ist deutlich weniger rechen- und speicherintensiv als die Vollsicherung aber intensiver als die inkrementelle Sicherung. Sie hat jedoch im Gegensatz zur inkrementelle Sicherung den Vorteil, dass nur die Vollsicherung und eine differenzielle Sicherung benötigt wird und Daten im Verlustfall wieder herzustellen. Daraus ergibt sich jedoch der Nachteil, dass sowohl das im Bezug stehende Vollbackup als auch das differenzielle Backup für eine erfolgreiche Wiederherstellung integer sein muss.

### Inkrementelle Sicherung
Eine Sicherung die alle Daten seit der letzten inkrementellen Sicherung oder Vollsicherung falls nicht vorhanden sichert. Diese Sicherung ist durch die Inkrementierungen am wenigsten Rechen- und Speicherintensiv. Eine Wiederherstellung der Daten benötigt aber die Vollsicherung und jede einzelne inkrementelle Sicherung, was die Wiederherstellung in diesem Fall rechenintensiver und aufwändiger macht. Gleichzeitig hat das stark verkette Konzept auch eine starke Erhöhung der "Points of Failure" zur Folge, da jede einzelne Datei auf den "Vorgänger" aufbaut, und somit keine der Dateien defekt sein darf.

### Großvater Vater Sohn Prinzip
Dieses Prinzip verbindet alle Backupstrategien miteinander, um eine optimale Balance aus Rechen- und Speicherintensität zu erreichen. Sie kann folgendermaßen ablaufen:
- Vollsicherung am Monatsanfang
- Differenzielle Sicherung am Wochenende (seit letzter Vollsicherung)
- Inkrementelle Sicherung am Tagesende (seit letzter inkrementelle Sicherung)

## RAID (Redundant Array of Independent Disks)
Ein RAID ist ein Verbund von Festplatten in denen ein Speicherbereich sich über mehrere Festplatten erstrecken kann oder gespiegelt wird. Die Spiegelung dient dem Schutz vor Datenverlust bei fehlerhaftem Schreiben oder dem Ableben der Festplatte. Aufgrund der Spiegelung ist ein RAID aber keine Backuplösung, da die Daten bei Beschädigung aller Spiegelinstanzen verloren gehen und versehentliche Änderungen automatisch gespiegelt werden. 

|Software-RAID|Hardware-RAID|
|---|---|
|Wird vom Betriebssystem verwaltet und benötigt daher zusätzliche Ressourcen|Wird von einem ressourcenunabhängigen RAID-Controller verwaltet zum Beispiel als DAS (Direct Attached Storage) oder als NAS (Network Attached Storage)|

Die Daten werden in Stripes (Blöcke) zerlegt, der Striping-Factor gibt die Blockgröße an.

|Bezeichnung|Beschreibung|Eigenschaften|
|---|---|---|
|RAID Level 0 (Data Striping)|Verbund mehrerer Festplatten|Min 2 Platten, niedrig|
|RAID Level 1 (Drive Monitoring)|Parität mehrerer Festplatten|Min 2 Platten, hoch|
|RAID Level 10|Kombination von RAID 0 und RAID 1 mit zwei Festplatten die jeweils auf zwei weiteren parätiert werden|Min 4 Festplatten, hoch|
|RAID Level 5|Matrixbetrieb durch Verteilung der Daten auf mehreren Festplatten und Parität auf jeweils nicht verwendeter Festplatte|Min 3 Festplatten, mittel|
|RAID Level 6|Matrixbetrieb durch Verteilung der Daten auf mehreren Festplatten und Parität auf jeweils zwei nicht verwendeter Festplatten|Min 4 Festplatten, hoch|
|Matrix RAID|Kombination von RAID 0 und RAID 1 mit zwei Festplatten mit jeweils zwei Partitionen die|Min 2 Festplatten|

Als Matrix RAID wird ein RAID bezeichnet, welcher auf einer Festplatte sowohl eine Datenpartition als auch eine Paritätspartition hat. Damit kann auf einer Festplatte eine Sicherung einer jeweils anderen Festplatte mit Datenpartition vorgenommen werden.

Hostspare sind Reservefestplatten zum schnellen Austausch im laufendem Betrieb.

## Unterbrechungsfreie Stromversorgung
Die USV kommt zum Einsatz, wenn durch mangelnde Spannungsqualität die Wiederherstellung des ausgefallenen sehr kostenintensiv ist oder Datenverlust oder Gefahr für Leib und Leben droht. Mangelnde Spannungsqualität kann durch Rauschen, Überspannung, Unterspannung und Spannungsspitzen sowie Totalausfall verursacht werden. Die USV dient also zur Verbesserung der Spannungsqualität und zur Weiterversorgung trotz Totalausfall.

### USV Arten
- **Standby- oder Offline USV:** Im Notfallbetrieb durch Akkumulator *(VFD - Voltage and Frequency Dependent)*
- **Netzinteraktive USV:** Im Notfallbetrieb durch Akkumulator sonst nur automatischer Spannungsregler *(VI - Voltage Independent)*
- **Online USV:** Dauerbetrieb durch Akkumulator (Keine Umschaltzeit) *(VFI - Voltage and Frequency Independent)*

||VFD|VI|VFI|
|---|---|---|---|
|Leistung|bis 1kVA|bis 5kVA|ab 500 VA|
|Wirkungsgrad|95%|95% - 98%|90%|
|Preis|niedrig|mittel|hoch|
|Anwendung|Kleine Verbraucher|Einzelne Verbraucher|Server und Datenkommunikation|
|Umschaltdauer|4ms - 10 ms|2ms - 4ms| / |

S (Scheinleistung in VA) = U * I = P / cosφ

P (Wirkleistung in W) = S * cosφ

cosφ (Leistungsfaktor)
