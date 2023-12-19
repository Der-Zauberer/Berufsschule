# Glossar
von André Sommer am 18.10.2023

### ARP (Address Resolution Protocol)
ARP wird verwendet um IP-Adressen den MAC-Adressen in einem Netzwerk zuordnen zu können und somit auf IP-Basis Geräte ansprechen zu können. Die Zuordnung wird in einer Tabelle eines Layer-2 fähigen Gerätes (z.B. Switch) hinterlegt. Das Gerät sendet ARP-Anfragen als Broadcast an Endgeräte im Netzwerk um eine bestimmte IP-Adresse zu suchen. Das betroffene Endgerät antwortet dann mit seiner IP-Adresse.

### CAT
Steht für Category (zu deutsch Güteklassen) und bezeichnet verschiedenen Qualitätsstandarts für Ethernetkabel.

### CSMA/CA  (Carrier Sense Multible Access with Collision Avoidance)
Teilnehmer in einem Netz hören mit um zu warten, bis die Leitung frei ist (Carrier Sense). Erst wenn die Leitung Frei ist wird ein RTS (Request to Send gestellt). Der Empfänger bestätigt mit CLS (Clear to Send). Wenn die Sendung abgeschlossen ist wird ein ACK (Acknowlege) gesendet um den anderen Teilnehmern mitzuteilen das die Leitung wieder für RTS frei ist.

### CSMA/CD (Carrier Sense Multible Access with Collision Detection)
Teilnehmer in einem Netz hören mit um zu warten, bis die Leitung frei ist (Carrier Sense). Erst wenn die Leitung Frei ist wird gesendet. Sollten zwei Teilnehmer gleichzeitig anfangen zu senden wird ein Jam-Signal gesendet um teilnehmern mitzuteilen, dass es zu einer Kollision kam. Die Kollision wird erkannt, weil beim Senden weiterhin mitgehört wird um den Input mit den Dtaneströmen auf der Leitung zu validieren. Nach dem Jamsignal warten die Teilnehmer eine zufällige Zeit um eine erneute Kollision zu vermeiden bevor sie mit dem Senden fortfahren.

### DHCP (Dynamic Host Configuration Protocol)
Durch DHCP können Geräte im Netzwerk automatisch IP-Adressen beziehen. Dazu sendet ein Endgerät eine Broadcastanfrage an den DHCP Server. Dieser antwortet dann im Broadcast mit der IP-Adresse und der dazugehörigen Subnetzmaske. Das Endgerät bestätigt per Boradcast diese Zuweisung. Die Nachrichten werden per Broadcast gesendet, um sicherzustellen, dass die Zuweisung nicht zu Problemen mit anderem Geräten im Netzwerk führt, da die anderen Endgeräte mitlesen und intervenieren können.

### DNS (Domain Name System)
DNS ist ein Protokoll zum Übersetzen von Domains in IP-Adressen. Eine Domain ist ein Name mit einen speziell definierten Schema, welche von einem Domainserver in eine IP-Adresse umgewandelt wird.

### FTP / SFTP (File Transfer Protocol)
FTP liegt auf der Anwendungsschiht und läuft standardmäßig auf Port 20 oder 21. Es dient zum Hochladen und Herunterladen von Dateien über das Netzwerk auf einem Dateiserver beziehungsweise Dateisystem. SFTP ist die verschlüsselte Variante.

### HTTP / HTTPS (Hypertext Transfer Protocol Secure)
HTTP wird auf der Anwendungsschicht verwendet um Hypertext (z.B. Webseiten) zu übertragen und läuft standartmäßig auf dem Port 80. HTTPS ist die verschlüsselte Variante und läuft standardmäßig auf dem Port 443. 

### ICMP (Internet Control Message Protocol)
Das ICMP basiert auf Layer-3 und wird hauptsächlich die Validierung von Datenpaketen im Bezug auf Ankunft und Zeit verwendet. Außerdem dient es zur Kommunikation über Fehlermeldungen.

### IP (Internet Protocol)
Die IP-Adresse ist eine eindeutige Adresse auf Layer-3, mit denen sich Geräte zuordnen lassen.

### NAT (Network Address Translation)
Ein Layer-3 fähiges Gerät (z.B. Router) vollzieht eine Network Address Translation um IPv4-Adressen zwischen privaten und öffentlichen Netzwerken zu übersetzen und Pakete weiterzuleiten.

### OSI (Open Systems Interconnection)
Das ISO-OSI Schichtenmodell vereinheitlicht die Übertragung von Daten in einem Netzwerk. Dazu wird eine Übertragung in Netzwerkschichten aufgeteilt.

### QoS (Quality of Service)
Quality of Service sorgt für eine Qualitätsgesicherte Kommunikation im Netzwerk. Es gibt Beispielsweise Parameter vor, mit der Datenpakete bevorzugt behandelt werden und gesendet werden um die Latenz zu veringern, zum Beispiel in der VoIP Telefinie.

### RTP (Real-Time Transport Protocol)
Das Protokoll dient zur übertragung von Multimedia-Datenströme wie Audio und Video und wird normalerweise mit UTP betrieben. Es wird auch zur VoIP übertragung eingesetzt. Und verwendet QoS um schnellere Datenkommunikation sicherzustellen.

### SIP (Session Initiation Protocol) 
Das SIP dient zum Kommunikationsaufbau für Multimedia-Datenströme wie Audio und Video.

### SSH (Secure Shell)
Die Secure Shell ist ein Protokoll auf Anwendungsschicht und läuft standardmäßig auf dem Port 22. Mit ihr können Konsolen über das Netzwerk ferngesteuert werden. Die Verbindung erfolgt außerdem verschlüsselt.

### TCP (Transmission Control Protocol)
TCP arbeitet auf Layer-4 und stellt sicher, dass gesendete Daten angekommen sind und dies in der richtigen Reihenfolge geschehen ist.

### Telnet
Telnet ist ein unverschlüsseltes Protokoll auf der Anwendungsschicht. Mit ihm können Konsolen über das Netzwerk ferngesteuert werden, der Standardport ist hierbei 23.

### UDP (User Datagram Protocol)
UTP arbeitet auf Layer-4 und wird für schnelle Datenkommunikation eingesetzt, bei der Verlusste oder die falsche Reihenfolge von Packeten in Kauf genommen wird, weil auf keine Bestätigung gewartet wird.

### VLAN (Virtual Local Area Network)
VLAN erlaubt das Aufteilen eines Netzwerkes in virtuelle kleinere Netzwerke bei physisch zusammengefassten Netzwerkteilnehmern.

### VPN (Virtual Private Network)
VPN stellt eine sichere Verbindung von einem Netzwerk in ein anderes Netzwerk als Teilnehmer her. Dies kann den Zugriff auf Netzwerkinterne Resourcen ermöglichen oder die sichere Datenkommunikation in einem unsicherem Netzwerk durch das umleiten der Daten in das Zielnetzwerk ermöglichen.
