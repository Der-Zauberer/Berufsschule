# Datenbanken
André Sommer am 14.09.2021

*Hier werden nur Relationale Datenbanken behandelt*

## Grundlegende Begriffe
Eine Datenbank ist eine Verknüpfung von Tabellen (Entitätstypen) welche wiederum Daten enthalten. Datenbanbanken werden verwendet um Daten zentral verwalten zu können. Eine Datenbank besteht aus der Speicherung und einem Datenbankmanagementsystenm (DBMS), welches die Speicherung verwaltet.

### Tabelle (Entitätstyp, Relation)
Eine Tabelle besteht aus mehreren Einträten (Entitäten) die alle nach dem geichen Muster aufgebaut sind, sie Definieren die Attributetypen und Attributnamen. Die Anzahl dieser Entitäten nennt man Entitätsmenge.

### Entität
Eine Entität hat einen eindeutigen Primärschlüssel und ein oder mehrere Attributwerte, welche im Entitätstyp definiert sind.

### Primärschlüssel (Primary Key)
Der Primärschlüssel ist eine Identifikationsnummer. Anhand dieser kann die Entität identifiziert werden.

### Fremdschlüssel (Foreign Key)
Der Fremdschlüssel ist ein Verweis auf einen anderen Primärschlüssel, mit ihm lassen sich Joins erstellen.

### Join
Ein Join ist eine Verknüpfung zweier Tabellen. Dabei verweist ein Fremdschlüssel auf einen Primärschlüssel einer anderen Tabelle.

### Datenbankmanagementsystem DBMS
Dieses System verarbeitet Datenbankbefehle und kümmert sich um die Daten Verwaltung. Dabei achtet diese auf die Optimierung von Abfragen und Indexing und kümmert sich um asynchronen Zugriff der Daten und Datenintegrität (Wiederspruchsfrei). Außerdem schützt das DBMS die Daten vor unerlaubten Zugriff.

### Transaktion
Sperrt die Daten vor Veränderungen um bei asynchronen Zugriff trotzdem Daten schreiben zu können.

### Redundanz
Datendopplung innerhalb einer Datenbank. Datendopplungen dürfen nach der dritten Normalenform in relationalen Datenbanken nicht vorkommen und sind somit ungewollt und überflüssig.

## Beziehungen
Es gibt verschiedene Arten von Beziehungen zwischen Tabellen. Die 1:1 Beziehung ist eine direkte Verknüpfung zweier Entitäten. Somit wäre es auch möglich die Entitäten zusammen zu fassen. Bei der 1:n Beziehung verweisen mehrere Entitäten auf eine Entität. Zum Beispiel könnten mehrere Söhne zu einem Vater gehören. Bei einer n:n Beziehung können verschiedene Tabellen auf verschiedene Tabellen verweisen. Da sich dies in Relationalen Datenbanken nicht umsetzen lässt ist über eine Zwischentabelle die n:n Beziehung in zwei 1:n Beziehungen aufzulösen. Zum Beispiel können verschiedene Fahrgäste verschieden Züge benutzen. Somit wird in einer Übergangstabelle jeweils ein Fahrgast einem Zug zugeordnet. Beziehungen werden auch Joins genannt.

## Normalisierung
Hierbei geht es darum Rendundanzen (Datendopplungen) zu vermeiden und einheitliche Attributwerte festzulegen.

1. Normalenform: Attribute müssen eindeutige Werte haben und dürfen jeweils nur aus einem Wert bestehen. 
2. Normalenform: Es werden Zwischentabellen angelegt um n:n Beziehungen in 1:n Beziehungen aufzulösen.
3. Normalenform: Es werden zusammengehörige Daten in eindeutigen Tabellen zusammengefasst. Nicht zusammengehörige Attribute werden in verschiedene Tabellen getrennt.