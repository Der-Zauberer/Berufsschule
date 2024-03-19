# WLAN
von André Sommer am 19.03.2024

## Begriffe

- **Wi-Fi:** Beschreibung von WLAN-Netzen gemäß dem Standard 802.11b
- **SSID (Service Set Identifier):** Namen des WLANs als eindeutige ID
- **Kanal:** Frequenzbereich eines Funknetzes, auf dem Client kommunizieren

## Funksystem
Eine höhere Freqzenz bedeutet einen höheren Datendurchsatz jedoch auch eine stärkere Dämpfung, was die Reichweite verkleinert. Für das Senden wird oft die Stabantenne verwendet die horizontal oder Vertikal verwendet werden kann. Die Frequenz liegt zwischen 2,4GHz und 5GHz, wobei ein Kanal 5MHz lang ist.

Bei der Planung eines WLANS sollte folgendes beachtet werden:
- Kriterien zur Auswahl des WLAN-Standards im Bezug auf den Datendurchsatz
- Anzahl der Nutzer im WLAN
- Umgebungsbedingungen
- Störquellen
- Ausleuchtung

## Betriebsarten

### Ad-Hoc
Authentifizierungsfreie Verbindung zum sofortigen Zugriff. Alle Stationen sind gleichberechtigt.

### Infrastructure Mode
Der Accesspoint (AP) sendet zweimal pro Sekunde einen Beacon an alle Clients. Der Beacon enthält die Art der Verschlüsselung und die Geschwindigkeit sowie die SSID des Funknetzes. Client müssen sich beim Verbinden erst Authentifizieren. Hier ist auch eine Zugangsbeschränkung per MAC-Adresse und Maximalbeschränkung gleichzeitigen Verbindungen möglich.

### Wireless Distributen System (WDS) / Roaming
Ein Access Point ist mit dem Internet verbunden und die weiteren Access Points dienen als Repeater. Dadurch lässt sich eine größere Fläche mit WLAN Abdecken. Das ist eine sehr flexible Lösung, kann aber auch mit Störungen und Sicherheitsproblemen einhergehen.

- **WPAN** Wireless Personal Network
- **WLAN** Wireless Local Area Network
- **WWAN** Wireless Wide Area Network

## Verschlüsselung

### WEP (Wired Equivity Protocol)
- 64Bit oder 128Bit Verschlüsselung
- symetrische Verschlüsselung
- RC4 Algorithmus (XOR)

### WPA (Wifi Protected Access)
- modifizierte WEP-Verschlüsselung
- kurzfristige Behebung bekannter WEP-Schwachstellen
- verbesserte Verschlüsselung und Authentifizierung
- RC4 Algorithmus (XOR)

### WPA2
- nicht kompatibel zu WEP oder WPA, neue Hardware erforderlich
- AES Verschlüsselung (Advanced Encryption Standard)
- symetrische Verschlüsselung

## Authentifikation
- **offene Authentification:** Jeder kann sich Verbinden und das Netzwerk nutzen
- **PSK (Pre Shared Key):** Geheimer Schlüssel für den WLAN-Zugang
- **EAP (Extensible Authentication Protocol):**  Username und Password für RADIUS