# Glossar
von André Sommer am 18.10.2023

### ARP (Adcress Resulution Protocol)
ARP wird verwendet um IP-Adressn den MAC-Adressen in einem Netzwerk zuordnen zu können und somit auf IP-Basis Geräte ansprechen zu können. Die Zuordnung wird in einer Tabelle eines Layer-2 fähigen Gerätes (z.B. Switch) hinterlegt. Das Gerät sendet ARP-Anfragen als Broadcast an Endgeräte im Netzwerk um eine bestimmte IP-Adresse zu suchen. Das betroffene Endgerät antwortet dann mit seiner IP-Adresse.

### CAT
Steht für Category (zu deutsch Güteklassen) und bezeichnet verschiedenen Qualitätsstandarts für Ethernetkabel.

### DHCP (Dynamic Host Configuration Protocol)
Durch DHCP können Geräte im Netwerk automatisch IP-Adressen beziehen. Dazu sendet ein Endgerät eine Broadcastanfrage an den DHCP Server. Dieser antwortet dann im Broadcast mit der IP-Adresse und der dazugehörigen Subnetzmaske. Das Endgerät bestätigt per Boradcast diese Zuweisung. Die Nachrichten werden per Broadcast gesendet, um sicherzustellen, dass die Zuweisung nicht zu Problemen mit anderem Geräten im Netwerk führt, da die anderen Endgeräte mitlesen und intervinieren können.

### DNS (Domain Name System)
DNS ist ein Protokol zum Übersetzen von Domains in IP-Adressen, damit diese dem entsprechendem Zielgerät zugeordnet werden können.

### FTP / SFTP (File Transfer Protocol)
FTP liegt auf der Anwendungsschiht und läuft standardmäßig auf Port 20 oder 21. Es dient zum Hochladen und Herunterladen von Dateien über das Netzwerk auf einem Dateiserver beziehungsweise Dateisystem. SFTP ist die verschlüsselte Variante.

### HTTP / HTTPS (Hypertext Transfer Protocol Secure)
HTTP wird auf der Anwendungsschicht verwendet um Hypertext (z.B. Webseiten) zu übertragen und läuft standartmäßig auf dem Port 80. HTTPS ist die verschlüsselte Variante und läuft standardmäßig auf dem Port 443. 

### ICMP (Internet Control Message Protocol)
Das ICMP basiert auf Layer-3 und wird hauptsächlich die validierung von Datenpaketen im Bezug auf Ankunft und Zeit verwendet. Außerdem dientz es zur kommunikation über Fehlermeldungen.

### IP (Internet Protocol)
Die IP-Adresse ist eine eindeutige Adresse auf Layer-3, mit denen sich Geräte zuordnen lassen.

### NAT (Network Address Translation)
Ein Layer-3 fähiges Gerät (z.B. Router) vollzieht eine Network Address Translation um IPv4-Adressen zwischen privaten und öffentlichen Netzwerken zu übersetzen und Pakete weiterzuleiten. NAT wird nur unter IPv4 verwendet.

### QoS (Quality of Service)
Quality of Service sorgt für eine Qualitätsgesicherte Kommunikation im Netzwerk. Es gibt Beispielsweise Parameter vor, mit der Datenpakete bevorzugt behandelt werden und gesendet werden um die Latenz zu veringern, zum Beispiel in der VoIP Telefinie.

### RTP (Real-Time Transport Protocol)
Das Protokoll dient zur übertragung von Multimedia-Datenströme wie Audio und Video und wird normalerweise mit UTP betrieben. Es wird auch zur VoIP übertragung eingesetzt. Und verwendet QoS um schnellere Datenkommunikation sicherzustellen.

### SIP (Session Initiation Protocol) 
Das SIP dient zum Kommunikationsaufbau für Multimedia-Datenströme wie Audio und Video.

### SSH (Secure Shell)
Die Secure Shell ist ein Protokoll auf Anwendungsschicht und läuft standardmäßig auf dem Port 22. Mit ihr können Konsolen über das Netzwerk ferngesteuert werden. Die Verbindung erfolgt außerdem verschlüsselt.

### TCP (Transmission Control Protocol)
TCP arbeitet auf Layer-4 und stellt sicher, dass gesendete Daten auch angekommen sind und dies in der richtigen reihenfolge geschehen ist.

### Telnet
Telnet ist ein unverschlüsseltes Protokoll auf der Anwendungsschicht. Mit ihm können Konsolen über das Netzwerk ferngesteuert werden, der Standardport ist hierbei 23.

### UDP (User Datagram Protocol)
UTP arbeitet auf Layer-4 und wird für schnelle Datenkommunikation eingesetzt, bei der Verlusste oder die falsche Reihenfolge von Packeten in kauf genommen wird, weil auf keine Bestätigung gewartet wird.