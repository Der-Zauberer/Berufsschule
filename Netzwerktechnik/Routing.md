### Zusammenfassung: Dynamisches Routing
von Felix Luckow am 24.06.2024

Dynamisches Routing automatisiert die Verwaltung und Verteilung von Routinginformationen, wodurch der administrative Aufwand reduziert und die Ausfallsicherheit in großen Netzwerken erhöht wird. Router tauschen dabei Informationen aus, um entfernte Netzwerke zu finden, Routinginformationen aktuell zu halten, Routen zu bewerten und den besten Pfad zu wählen.

### Ziel des dynamischen Routings:
1. Entfernte Netzwerke zu finden
2. Routinginformationen aktuell zu halten
3. Routen zu bewerten
4. Den besten Pfad auszuwählen

### Typen des dynamischen Routings:
1. **Distance Vector Routing (DV)**
   - Router senden periodisch den gesamten Inhalt ihrer Routingtabelle.
   - Informationen werden als Broadcast- oder Multicastnachrichten an Nachbarn gesendet.
   - Vorteile: Einfachheit und Eignung für kleine, lokale Netze.
   - Nachteile: Gefahr von Routingschleifen und eingeschränkte Skalierbarkeit.

2. **Link State Routing (LS)**
   - Router bilden Routing-Peers und tauschen Netz-Topologie-Informationen aus.
   - Vorteile: Detaillierte Netzwerkinformationen und bessere Skalierbarkeit.

### Metrik:
Die Metrik bestimmt die Erreichbarkeit entfernter Netzwerke und variiert je nach Routingprotokoll. Beispiele für Metriken sind:
- Anzahl der Hops
- Bandbreite
- Verbindungskosten
- Verbindungsauslastung
- Verzögerung
- Zuverlässigkeit der Verbindung

### Distance Vector Routing (DV):
- Router kennen nur die Entfernung und die Richtung zum Ziel.
- Der gesamte Routingtabelleninhalt wird periodisch an Nachbarn gesendet.
- Routingschleifen (Loops) und Count-to-Infinity-Probleme werden durch Techniken wie Split Horizon und Poison Reverse gemildert.

### RIP (Routing Information Protocol):
- Ein veraltetes Distance Vector-Protokoll mit Einschränkungen wie begrenztem Hop-Count (maximal 15).
- Verwendet Techniken wie Split Horizon, Route Poisoning, und Triggered Updates zur Verbesserung der Netzwerkkonvergenz und zur Vermeidung von Routingschleifen.

### Wichtige Timer im RIP:
- **Update Timer**: Bestimmt das Intervall, in dem Routinginformationen gesendet werden.
- **Route-Invalidation Timer**: Setzt eine Route als nicht erreichbar, wenn keine Updates empfangen werden.
- **Holddown Timer**: Verhindert Routing-Updates für eine Route, deren Metrik sich verschlechtert hat, um Netzwerkkonvergenzprobleme zu vermeiden.

### Konfiguration von RIP:
1. Aktivieren des RIP-Protokolls und der Version 2.
2. Angeben der Netzwerke, die propagiert werden sollen.
3. Deaktivieren von RIP auf bestimmten Schnittstellen.
4. Aktivieren des classless Routings.

### Überprüfung der RIP-Konfiguration:
- Anzeigen der IP-Routing-Tabelle.
- Anzeigen der RIP-spezifischen Routen.
- Anzeigen der Protokollinformationen.
- Aktivieren des Debugging für RIP.

Reines Distance Vector Routing wird heutzutage in großen Netzen kaum noch eingesetzt, außer in Kombination mit anderen Routingmethoden wie Path-Vector (BGP) oder als Hybrid mit Link State-Routing (EIGRP).
In mobilen Netzwerken findet es jedoch wieder vermehrt Anwendung.

Auffällig bei diesem Befehl ist, dass die Subnetzmaske in invertierter Schreibweise angegeben wird. Diese Schreibweise wird sonst üblicherweise beim Einrichten von Access-Control-Lists (ACLs) verwendet und wird auch als „Wildcard Mask“ bezeichnet.

## Designated Router in Multiaccess-Netzwerken

Grundsätzlich gilt zu unterscheiden, ob es sich bei der Verbindung der Router um eine Point-to-Point Verbindung oder um ein Multi-Access-Netzwerk handelt. 

Da es in einem Multi-Access-Netzwerken mehrere Nachbarschaften gibt, steigt der LSA-Traffic stark an.

## Verteilung der Rollen

Um den Datenverkehr in einem Link-State Multi-Access-Netzwerk zu senken, wird ein Router zum Designated Router (DR) ernannt. Dieser Router hält als Einziger die komplette Topologie und steuert die LSAs. Zur Ausfallsicherheit wird automatisch ein Backup Designated Router (BDR) angelegt. Alle anderen Router werden als DROTHER bezeichnet und senden ihre Nachrichten nur noch an den Designated Router (DR) und den Backup Designated Router (BDR).

- **Designated Router Multicast:** 224.0.0.5
- **Backup Designated Router Multicast:** 224.0.0.6

### Wahl des DR und BDR

Um die Wahl des DR und BDR bestimmen zu können, werden verschiedene Kriterien in vorgeschriebener Reihenfolge verwendet:

1. Ermittlung der Priorität
2. Ermittlung Router ID
3. Ermittlung der IP-Adresse des Loopback-Interface
4. Ermittlung der höchsten, eingestellten IP-Adresse an den Router-Interfaces

## OSPF Areas

Die Zahl möglicher Router in einem Netz ist limitiert (ca. 25). Bei größeren Netzen wird daher in Areas unterschieden, die über einen Area Border Router (ABR) miteinander verbunden sind. Alle anderen Router kennen nur ihren ABR und ihre eigene Topologie, aber nicht die anderen Router außerhalb ihrer Area. Somit besitzen alle Router in einer Area dieselbe Link-State Database. 

Von besonderer Hierarchie ist die Area 0 – Backbone Area. Alle anderen Areas müssen direkt oder über einen Virtual Link mit ihr verbunden sein. Änderungen der Topologie in einer Area werden grundsätzlich (nicht automatisch) nicht in eine benachbarte Area verteilt. Der Vorteil besteht darin, dass dadurch eine gute Skalierbarkeit des gesamten Netzwerks entsteht und die Areas, somit auch das gesamte Netzwerk, schneller konvergent wird.

## OSPF Überblick

### Vorteile:

- OSPF ist ein offener Quellsatz, also Lizenzfrei
- Ein LS-basiertes Routingprotokoll ist per Definition frei von Routingschleifen
- LS Routing ermöglicht sehr schnelle Netzkonvergenzzeiten (bis unterhalb 100ms)
- Das DR- und Area-Konzept ermöglicht eine gute Skalierung auch für größere Netze durch Hierarchisierung
- OSPF unterstützt VLSM und CIDR

### Nachteile:

- CPU und speicherintensives Routing
- LS-Routing erfordert eine gute Planung/ Design
- Die Konfiguration kann je nach Anforderung sehr komplex werden
- Grundsätzliches Problem bei unerwünschter Netzpartitionierung (z.B.: DR/BDR für einzelne Router nicht mehr erreichbar)

### Zusammenfassung:

Beim LS Routing werden nur Topologieinformationen zwischen den Routern ausgetauscht – nicht die Routingtabelle. Hierzu wird der Inhalt der LSDB regelmäßig auf Änderungen überprüft und bei Bedarf aktualisiert. Das beste Beispiel ist hier OSPF.

