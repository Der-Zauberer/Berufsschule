# Sicherheit
von André Sommer am 01.02.2024

Unter IT-Sicherheit versteht man im Allgemeinen den Schutz von Daten. Dabei geht es zum einem um den Schutz vor fremden Zugriff aber auch den Schutz vor Datenverlust.

## Bundesamt für Sicherheit und Informationstechnik (BSI)
Das BSI wurde von der Bundesregierung  1991 mit dem "Gesetzes über die Errichtung des Bundesamtes für Informationstechnik" geschaffen. Es hat drei Aufgben:
- Gewährleistung der Sicherheit für das Regierungsnetz
- Gewährleistung der Sicherheit für kritische Infrastruktur
- Warnung der Bevölkerung vor Sicherheitslücken
- Setzen von Mindeststandards

## Schadsoftware
- **Virus:** Wie echte Viren benötigen Computerviren ein Wirtsprogramm, mit dem sie ausgeführt werden.
- **Wurm:** Würmer kommen ohne Wirtsprogramm aus und können sich möglicherweise von selbst über das Netzwerk oder Mailverkehr weiter verbreiten.
- **Trojaner:** Eine sinnvolle Anwendung, die aber im Hintergrund Schadsoftware enthält.
- **Botnet:** Ein zumeist Zusammenschluss von (zumeist Infizierten) Clients, um "Denial of Service" Angriffe durchzuführen
- **Harvester:** Durchforstet Webseiten nach persönlichen Daten.

## Spamformen
- **Scam:** Unter falschem Namen oder falschem Vorwand wird Geld oder eine Wahre verlangt oder Erpresst.
- **Hoax:** Falschinformationen, die oft mit der Aufforderung verbunden sind diese weiter zu leiten.
- **Phishing:** Unter falschem Namen oder falschemm Vorwand werden Informationen erfragt oder wischen den Zeilen erlangt.

## Vertraulichkeit, Integrität, Verfügbarkeit, Authentizität (VIVA)
- **Vertraulichkeit:** Beschreibt die Zugriffsbeschränkung vor unerlaubter Einsicht und Verschlüsselung bei der Übertagung von Daten.
- **Integrität:** Beschreibt den Schutz der Daten vor unerlaubter Veränderung.
- **Verfügbarkeit:** Beschreibt die Ausfallsicherheit der Datenbereitstellung
- **Authentizität:** beschreibt die Zuordbarkeit und Nachvollziehbarkeit von Handlungen

## Verschlüsselungsverfahren

### Symmetrische Verschlüsselung
Bei  Verschlüsselung wird mit dem gleichen Schlüssel Verschlüsselt und Entschlüsselt. Ein Beispiel hierfür ist die Cäsarverschlüsselung oder Base64.

### Asymmetrische Verschlüsselung
Bei Verschlüsselung wird mit einem Public-Key verschlüsselt und mit dem Private-Key entschlüsselt. Hierbei kann der Private-Key verteilt werden, da sich die Nachricht mit ihm nicht verschlüsseln lässt und er keine Rückschlüsse auf den Private-Key zulässt. Ein Beispiel hierfür ist das RSA verfahren, bei diesem werden die Keys durch zwei Primzahlen generiert.

### Hashing
Beim Hashing kann nur Verschlüsselt werden, es gibt keine Möglichkeit die Nachricht wieder zu entschlüsseln. Dies ist zum Beispiel für Passwörter sinvoll. Hier werden die Passwörter gehasht gespeichert und beim Login wird das Loginpasswort gehashed mit dem gespeicherten gehashtem Password aus der Datenbank verglichen. Bei Passwörtern ist wichtig, dass es keine Hashkollisionen gibt. Ein Beispiel hierfür ist SHA-256.

### Sicherheitsvorkehrungen
- **Monitoring:** Infrastruktur Wird über ein System überwacht, welches bei merkwürdigen Verhaltensmustern von Usern, Datenverarbeitungen oder zu vielen Zugriffen, oder Überlastung Alarm schlägt.
- **Passwort-Manager:** Ein Verwaltungsprogramm für Passwörter um möglichst für jeden Dienst ein anderes Passwort zu verwenden ohne sich die Passwörter merken zu müssen.
- **Zwei-Faktor-Authentifikation (2FA):** Es müssen zur Authentisierung zwei der drei Faktoren Wissen (zB. Passwort), Identität (zb. Fingerabdruck), Besitz(z.B Mobiltelefon) zum anmelden benutzt werden. Dies geschieht meist über eine extra App, welche Zeitgebundene Anmeldecodes ausgibt.

## Schutzbedarf
Hierbei wird analysiert, wie schutzbedürftig ein Unternehmen ist beziehungsweise was passiert, wenn die VIVA Zielobjekte verletzt werden. Um dies zu verhindern gibt es Sicherheitsrichtlinien (Security Policy). Sie muss von allen Mitarbeitern des Unternehmens zur Kenntniss genommen werden, eine Verletzung wird sanktioniert und kann durch die DSGVO je nach schwere zu empfindlichen Geldbusen und selbst zu Haftaststrafen frühen.

Die Schutzbedürftigkeit wird in drei Kategorien angegeben:
- **Normal: die Schadensauswirkungen sind begrenzt und überschaubar**
  - Der mögliche finanzielle Schaden ist kleiner als 50.000 Euro
  - Ausfallzeiten von mehr als 24 Stunden werden hingenommen 
- **Hoch: Die Schadensauswirkungen können beträchtlich sein**
  - Der mögliche finanzielle Schaden liegt zwischen 50.000 Euro und 500.000 Euro
  - Ausfallzeiten dürfen maximal 24 Stunden betragen
- **Sehr Hoch: Die Schadensauswirkungen können ein existenziell bedrohliches und katastrophales Ausmaß erreichen**
  - Der mögliche finanzielle Schaden ist größer als 500.000 Euro
  - Ausfallzeiten dürfen maximal zwei Stunden betragen

Der mögliche Schaden sich außerdem nach:
- Verstöße gegen Gesetze und Verträge
- Beeinträchtigung
  - Informationellen Selstbestimmngsrechtes
  - Persönliche Unversehrtheit
  - Aufgabenerfüllung
- Negative Innen- und Außenwirkung
- Finanzielle Auswirkungen

## Backup

### Vollsicherung
Eine vollständige Sicherung aller zur sichernden Daten. Eine Vollsicherung ist entsprechend rechenintensiv und kann lange Dauern. Außerdem ist die Vollsicherung entsprechend so groß wie die Größe der zu sichernden Daten.

### Differenzielle Sicherung
Eine Sicherung, die alle Änderungen sichert, die seit der letzten Vollsicherung aufgetreten sind. Dieses vorgehen ist deutlich weniger Rechen- und Speicherintensiv als die Vollsicherung aber intensiver als die inkrementelle Sicherung. Sie hat jedoch im Gegensatz zur inkrementelle Sicherung den Vorteil, dass nur die Vollsicherung und eine differenzielle Sicherung benötigt wird und Daten im Verlustfall wieder herzustellen.

### Inkrementelle Sicherung
Eine Sicherung die alle Daten seit der letzten inkrementellen Sicherung oder Vollsicherung falls nicht vorhanden sichert. Diese Sicherung ist durch die Inkrementierungen am wenigsten Rechen- und Speicherintensiv. Eine Wiederherstellung der Daten benötigt aber die Vollsicherung und jede einzelne inkrementelle Sicherung, was die Wiederherstellung in diesem Fall rechenintensiver und aufwändiger macht.

### Großfater Vater Sohn Prinzip
Dieses Prinzip verbindet alle Backupstrategien miteinander um eine optimale Balance aus Rechen- und Speicherintensität zu erreichen. Sie kann folgendermaßen ablaufen:
- Vollsicherung am Monatsanfang
- Differenzielle Sicherung am Wochenende (seit letzter Vollsicherung)
- Inkrementelle Sicherung am Tagesende (seit letzter inkrementelle Sicherung)

## RAID
TODO

## USV
TODO

## Netzwerksicherheit
TODO
