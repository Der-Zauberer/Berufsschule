# Ethernet
von André Sommer am 13.11.2023

## Netzformen
- Bus
- Stern
- Ring
- Baum
- Vermascht

## Ausdehnung von Netzen

|Name|Beschreibung|Ausdehnung|
|---|---|---|
|GAN (Global Area Network)|Wird als globales Netz mit erdumgreifender Dimension verwendet.|>10.000km|
|WAN (Wide Area Network)|Wird als Weitverkehrsnetz, welches ganze Länder umspannt verwendet.|>1.000km|
|MAN (Metropolitan Area Network)|Wird als regionales Netz zum verbinden von LANs verwendet.|100km (WMAN ~50km)|
|SAN (Storage Area Network)|Wird für große Massenspeichernetzwerke (Server für Speicherungen) verwendet.|~10km|
|LAN (Local Area Network)|Verbindet Geräte in Unternehmen, beschränkt sich auf das entsprechende Gelände.|~3km (WLAN ~250m)|
|PAN (Personal Area Network)|Wird für lokale private Netze verwendet (Heimnetz).|~100m|
|CAN (Controller Area Network)|Ursprünglich Car Area Network, wird generell zum vernetzen von Steuerungssystemen verwendet|~500m|
|BAN (Body Area Network)|Wird für medizinische Telemetrie mit Messung am menschlichem Körper verwendet.|~1m|

## Klassifikation nach Übertragungsmodus

### Simplex
Die Kommunikation kann nur unidirektional erfolgen, also nur in eine Richtung.

### Halbduplex
Die Kommunikation ist zwar bidirektional, allerdings nur seriell. Das heißt die Kommunikation kann in beide Richtungen erfolgen, kann Daten aber nur nacheinander und nicht gleichzeitig versenden beziehungsweise empfangen.

### (Full-)Duplex
Bei einem Fullduplex können die Daten sowohl bidirektional als auch parallel versendet werden. Das bedeutet, dass ein Empfänger selbst senden kann, ohne auf eine Antwort warten zu müssen.

|Art|Bidirektional|Parallel|
|---|---|---|
|Simplex|Nein||
|Halbduplex|Ja|Nein|
|(Full-)Duplex|Ja|Ja|

## Klassifikation nach Kommunikationsmuster

### Point to Point
Ein Punkt kann nur an dem nächsten Punkt senden, der kann die Informationen wiederum weiter geben.

### Broadcast
Ein Punkt kann an alle weiteren Punkte senden, muss aber an alle senden und kann nicht differenzieren.

### Multicast
Ein Punkt kann an bestimmte Punkte senden, kann also zwischen Empfängeren differenzieren.

## OSI-Modell 
**P**lease **D**o **N**ot **T**hrow **S**alami **P**izza **A**way

|Englische Bezeichnung|Deutsche Bezeichnung|Werkzeuge|Beispiel|
|---|---|---|---|
|Application Layer|Anwendungsschicht|FTP, HTTP, HTTPS, SNMP, SSH, TELNET|Firewall, Anwendung|
|Presentation Layer|Darstellungsschicht|||
|Session Layer|Sitzungsschicht|||
|Transport Layer|Transportschicht|TCP, UDP|Firewall|
|Network Layer|Vermittlungsschicht|IP|Router, Firewall|
|Data Link Layer|Sicherungsschicht|MAC-Adresse|Switch, Netzwerkkarte, Firewall|
|Physical Layer|Bitübertragungsschicht|Mediumsabhängige Kommunikation|Hub, Repeater|

In der TCP/IP Schichtenarchitektur werden die Schichten `Presentation Layer` und `Session Layer` ignoriert und die Schichten `Data Link Layer` und `Physikal Layer` zum `Host-to-Net Layer` zusammengefasst.

|Englische Bezeichnung|
|---|
|Application Layer|
|Transport Layer|
|Network Layer|
|Host-to-Net Layer|

## Kapselung

|Frame (Ramen)|Packets (Pakete)|Segments (Segmente)|Messages (Nachrichten)||
|---|---|---|---|---|
|Header Host-to-Net Layer|Header Network Layer|Header Transport Layer|Daten der Anwendungsschicht|Trailer|

## Netzwerkverbindung

### Konkurrenzverfahren CSMA/CD (Carrier Sense Multible Access with Collision Detection)
Teilnehmer in einem Netz hören mit um zu warten, bis die Leitung frei ist (Carrier Sense). Erst wenn die Leitung frei ist wird gesendet. Sollten zwei Teilnehmer gleichzeitig anfangen zu senden wird ein Jam-Signal gesendet um Teilnehmern mitzuteilen, dass es zu einer Kollision kam. Die Kollision wird erkannt, weil beim Senden weiterhin mitgehört wird um den Input mit den Datenströmen auf der Leitung zu validieren. Nach dem Jamsignal warten die Teilnehmer eine zufällige Zeit um eine erneute Kollision zu vermeiden bevor sie mit dem Senden fortfahren.

### Konkurrenzverfahren CSMA/CA  (Carrier Sense Multible Access with Collision Avoidance)
Teilnehmer in einem Netz hören mit um zu warten, bis die Leitung frei ist (Carrier Sense). Erst wenn die Leitung frei ist wird ein RTS (Request to Send gestellt). Der Empfänger bestätigt mit CLS (Clear to Send). Wenn die Sendung abgeschlossen ist wird ein ACK (Acknowlege) gesendet um den anderen Teilnehmern mitzuteilen das die Leitung wieder für RTS frei ist.

### Nicht konkurrierendes Verfahren Token Passing
Teilnehmer in einem Ring-Netz dürfen nur senden, wenn sie im Besitz eines Tokens sind. Es ist immer nur ein Token im Umlauf, so können Kollisionen vermieden werden. In Datenstromrichtung wird ein Frei-Token weitergeleitet. Dieses wird in ein Besetzt-Token umgewandelt und vorne an den Datenstrom angehängt. Nach dem Erhalten einer Empfangsbestätigung erhält der Absender ein neues Frei-Token, was weitergelesen wird. Jeder Teilnehmer in Datenstromrichung zwischen Sender und Empfänger kann mitlesen.

## Kollisionsdomäne
Verwenden mehrere Netzwerkteilnehmer das gleiche Medium spricht man von einem `shared medium`. Die Menge an Teilnehmern, die sich ein Medium teilen nennt man Kollisionsdomäne.

## Broadcastdomäne
Eine Broadcast-Meldung ist eine Rundumsendung an alle Netzwerkteilnehmer. Die Menge der potentiellen Broadcast-Empfänger bilden die Broadcastdomäne.