# Netzwerkverkabelung
von André Sommer am 10.11.2023

## Koaxial-kabel
Zu Beginn der der LAN-Technologie wurde das Koaxialkabel verwendet. Die Maximale Übertragungsgeschwindigkeit betrug 10 Bbps. Aufgrund des geringen Biegeradius und der fehlenden Duplexübertragung wurden sie aber nach und nach durch Twisted-Pair Kabel ersetzt.

## Übersprechen (Crosstalk)
Werden Ethernet-Kabel nebeneinander gelegt können sie sich gegenseitig beeinflussen und es können Signale auf das andere Kabel überspringen. Die kann passieren durch
- galvische oder ohmsche Kopplung durch Isolationswiderstände
- kapazitive Kopplung durch die Kapazitäten, die sich zwischen den Leitungen bilden
- induktive Kopplung durch die Spulen, die jede Leitung bei Stromfluss bildet
- hochfrequente elektromagnetische Kopplung

## Schirmung (Auszug)
|Schirmung|Ausgeschrieben|Beschreibung|
|---|---|---|
|U/UTP|Unshielded Unshielded Twisted Pair|Kein gemeinsamer Schirm (U), einzelne Paare ungeschirmt (UTP)|
|SF/UTP|Screened Foiled Unshielded Twisted Pair|Gemeinsamer Schirm aus Geflecht un Folie (SF), einzelne Paare ungeschirmt (UTP)|
|F/UTP|Foiled Unshielded Twisted Pair|Gemeinsamer Folienschirm (F) einzelne Paare ungeschirmt (UTP)|
|S/FTP|Screened Foiled Twisted Pair|Gemeinsamer Geflechtschirm einzelner Paare (S), jeweils von einem Folienschirm umgeben (FTP)|

## Güteklassen (Auszug)
|Bezeichung|Geschwindigkeit|Freuenz|Schirmung|
|---|---|---|---|
|Cat1|1 Mbps|100 kHz|ohne Schirmung, ohne Verdrillung|
|Cat2|4 Mbps|1 MHz|ohne Schirmung, mit Verdrillt|
|Cat3|10 Mbps|16 MHz|UTP|
|Cat4|16 Mbps|20 MHz|UTP oder STP|
|Cat5|10 Mbps oder 100 Mbps|100 MHz|F/FTP|
|Cat5e|1 Gbps|100 MHz|F/FTP|
|Cat6|1 Gbps|250 MHz|F/FTP oder S/FTP oder SF/FTP|
|Cat6a|10 Gbps|500 MHz|SF/FTP|
|Cat7|10 Gbps|600 MHz|F/FTP oder S/FTP oder SF/FTP|
|Cat7a|10 Gbps|1000 MHz|SF/FTP|
|Cat8|25 Gbps oder 40 Gbps|1200 MHz|SF/FTP|

## Lichtwellenleiter
Lichtwellenleiter werden aufgrund ihrer geringen Dämpfung für lange Distanzen eingesetzt, man unterscheidet hier zwischen Multimode und Singlemode.

||Singlemode|Multimode|
|---|---|---|
|Beschreinung|Ein durchgehender Lichtstrahl ohne Reflektion|Mehrere Strahlen, die am Mantelglas reflektiert werden|
|Kerndurchmesser|c.a. 10µm|c.a. 50µm|
|Konstenvergleich|Teurer|Günstiger|
|Reichweitenvergleich|Größer|Kleiner|

## Struktorierte Verkabelung
|Stufe|Alias|Beschreibung|
|---|---|---|
|Primärverkabelung|Gebäudeverteiler|Verkabelung zwischen Häusern|
|Sekundärverkabelung|Gebäudeverkabelung, Stockwerkverteiler|Verkabelung der Stockwerke untereinander|
|Tertiärverkabelung|Stockwerkverkabelung, Etagenverkabelung|Verkabelung innrhalb eines Stockwerkes|

Durch die Strukturierte Verkabelung soll erreicht werden, dass alle Häuser das gleiche Verkabelungskonzept verwenden. Dies vereinfacht Dokumentationen und vergünstigt Wartungen. Häuser sind aufgrund der Ausfallsicherheit vermascht und damit redundant verbunden.