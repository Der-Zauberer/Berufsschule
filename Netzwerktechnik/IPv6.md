# Ethernet
von André Sommer am 05.12.2023

## Aufbau

Die IPv6 Adresse hat 8 Bläcke mit jeh 16 Bits und hat somit einen Adressbereich von 2^128 Adressen. Die Trennund von Hostbereich und Netzbereich erfolgt immer im vierten Block.

```
2004:7f3c:01fd:0001:0000:0000:0000:00c4
-------------- |||| -------------------
Netzbereich    |||| Hostbereich
               Subnetting
```

Somit können maximal 2^16 = 65536 Subnetze gebildet werden.

## Kürzung

Führende Nullen in einem Block können gekürzt werden. Außerdem dürfen beliebeig viele Blöcke, die nur eine Wertigkeit von 0 haben einmalig abgekürzt werden. Die Beislpieladresse von oben sähe demnach so aus:

```
2004:7f3c:01fd:0001:0000:0000:0000:00c4
          x    xxx  xxxxxxxxxxxxxx xx

2004:7f3c:1fd:1::c4
```

## Adressvergabe

### Stateful Address Configuration (DHCPv6)
Bei der Stateful Address Configuration wird die IPv6 Addresse einfach von einem IPv6 fähigem DHCP Server bezogen.

### Stateless Address Configuration (MAC-Adresse)
Bei der Stateless Address Configuration wird die Netzadresse übernommen und die Hostadresse aus der MAC-Adresse generiert. Dazu wird die Herstellerkennung und die Adapterkennung verwendet, zwischen diesen wird mit `ff:fe` aufgefüllt und das siebte Bit der Herstellerkennung wird geflipt.

```
MAC 00:0c:f1:8e:c1:d8
    -------- --------
    Herstlr. Adapter

                     |Bitflip
fe80:0000:0000:0000:020c:f1ff:fe8e:c1d8
------------------- -------|||||-------
Netzbereich         Herstlr.||||Adapter
                           Trenner
```

## Adressarten

|Adresse|Name|Beschreibung|
|---|---|---|
|::1|Loopback-Interface|Locale Adresse die nicht über das Netzwerk versendet wird, sondern auf dem lokalem Gerät bleibt.|
|ff02::|All-Nodes-Multicast-Group|Eine Multicast-Gruppe, die an alle IPv6 fähigen Geräte innerhalb eines Links sendet.|
|fe80::|Link-Local-Adress|Über die Adresse können geräte innerhalb eines Links miteinander Kommunizieren, Addresse kann nicht über den Link hinaus geroutet werde.|
|2000::|Global-Unicast-Address|Eine einzigartige globale Adresse, die im Internet geroutet werden kann.|