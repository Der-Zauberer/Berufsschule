# SQL
André Sommer am 01.02.2024

*Diese zusammenfassung bezieht sich auf den SQL Dialekt MySQL, bei anderen Dialekten kann die Syntax abweichen!*

## Befehlsgruppen
- **Data Definition Language (DDL):** Definiert und verändert die Datenbankstruktur
- **Data Data Manipulation Language (DML):** Verändert Daten in der Datenbank
- **Data Query Language (DQL):** Erfragt und liest Daten aus der Datenbank
- **Data Administration Language (DAL):** Verwaltet Benutzer und deren Rechte
- **Transaction Control Language (TCL):** Stellt Datenintegrität sicher in dem Anweisungen ganz oder gar nicht ausgeführt werden.

## Data Definition Language (DDL)

### Anlegen mit CREATE
```sql
-- Tabelle "Kunde" mit Spalten "id" und "name" erstellen
CREATE TABLE Kunde (
    id INT NOT NULL AUTO INCREMENT,
    name TEXT NOT NULL
);
```

### Bearbeiten mit ALTER
```sql
-- In Tabelle "Kunde" Spalte "firma" hinzufügen
ALTER TABLE Kunde ADD COLUMN firma TEXT;
-- In Tabelle "Kunde" Spalte "firma" löschen
ALTER TABLE Kunde DROP COLUMN firma;
-- In Tabelle "Kunde" Datentyp von Spalte "name" ändern
ALTER TABLE Kunde ALTER COLUMN name TYPE CHARACTER VARYING(45); 
-- In Tabelle "Kunde" Spalte "name" inf vorname umbenenne
ALTER TABLE Kunde RENAME COLUMN name to vorname; 
```

### Löschen mit DROP
```sql
-- Tabelle "Kunde" löschen
DROP TABLE Kunde;
```

## Data Manipulation Language (DML)

### Anlegen mit INSERT
```sql
-- Daten in Tabelle "Kunde" mit den Spalten "id" und "name" Datensätze anlegen
INSERT INTO Kunde (id, name) VALUES 
(0, "Hans"),
(1, "Heinz");
```

### Bearbeiten mit UPDATE
```sql
-- In Tabelle "Kunde" Spalte "name" auf "Max" setzen, bei allen Daten mit in dem der Wert der Spalte "id" 0 ist 
UPDATE Kunde SET name = "Max" WHERE id = 0;
```

### Löschen mit DELETE
```sql
-- Von Tabelle "Kunde" alle Datensätze löschen in dem der Wert der Spalte "id" 0 ist 
DELETE FROM Kunde WHERE id = 0;
```

## Data Query Language (DQL)
Die Reihenfolge bei SQL-Abfragen ist immer `SELECT` `FROM` `WHERE` `GROUP BY` `HAVING` `ORDER BY`. Hier ein Beispiel für eine SQL Abfrage:

```sql
-- Spalten für Ergebnistabellen auswählen
SELECT S.name, S.datum, L.name, avg(N.Note) AS notendurchschnitt
-- Tabellen auswählen, von dem die Spalten verwendet werden
FROM Schueler S, Noten N, Lehrer L
-- Verknüpfungen der Tabellen definieren
WHERE S.lehrer = L.id
-- Nach allen Spalten gruppieren, die keine Aggregatsfunktion sind
GROUP BY S.name, S.datum, L.name
-- Nach dem Ergebnis von Aggregatsfunktionen filtern
HAVING avg(N.note) > 3
-- Nach Spalten sortieren
ORDER BY avg(N.note) ASC
```

### SELECT

Select wählt die Spalten aus, bei Funktionen ist es oft Notwendig einen Namen zu hinterlegen. Dies geschieht mit dem Schlüsselwort `AS`, dahinter kommt der Name. Sollte dieser Leerzeichen und Sonderzeichen enthalten ist der Name mit eckigen Klammern einzuschließen: `avg(N.Note) AS [Der Notendurchschnitt]`. Es gibt verschiedene Aggregatsfunktionen:

|Schlüsselbefehle||
|---|---|
|`avg()`|Durchschnitt|
|`sum()`|Summe|
|`count()`|Menge|
|`min()`|Minimaler Wert|
|`max()`|Maximaler Wert|

### FROM

From gibt an welche Tabellen benötigt werden. Diese können für Spaltenaufrufe mit einem Buchstaben abgekürzt werden: `FROM Noten N`. Wenn nur eine Tabelle verwendet wird können alle Attribute ohne Tabellenname oder Tabellenalias verwendet werden.

### WHERE

Where kann eine Verbindung (Join) zwischen Tabellen herstellen und weitere Bedingungen festlegen, die nicht von Aggregatsfunktionen abhängig sind. Eine Verbindung erfolgt zwischen dem Primärschlüssel der einen Tabelle und dem Fremdschlüssel der anderen Tabelle: `WHERE A.Primärschlüssel = B.Fremdschlüssel`.

|Schlüsselbefehle||
|---|---|
|`=` `<` `>` `<=` `>=`|Vergleichsoperator|
|`LIKE`|Vergleich für Strings|
|`BETWEEN`|Daten innerhalb eines Wertebereiches|
|`AND`|Und|
|`OR`|Oder|
|`NOT`|Nicht|

### WHERE und Strings

Mit dem Schlüsselwort `LIKE` können Strings eingegrenzt werden. Dabei steht je nach SQL Dialekt `*` und `%` für beliebig viele Buchstaben und `?` für einzelne Buchstaben. Mit `WHERE text LIKE '%in%'` werden alle Texte ausgegeben, die das Wort "in" enthalten. Mit den Befehl `WHERE vorname LIKE 'Ni?o` werden alle Vornamen ausgegeben die einen einzelnen beliebigen Buchstaben zwischen "i" und "o" entgalten. Damit wäre sowohl das Ergebnis "Nico" als auch "Niko" möglich.

### WHERE und Daten

Daten können in der amerikanischen Schreibweise eingegrenzt werden mit der Formatierung `YYYY/MM/DD`. Möglich wäre ein Datenbereich zu definieren mit `WHERE Datum BETWEEN 20200101 AND 20201231`. Mit den Funktionen `YEAR()` `MONTH()` und `DAY()` kann dies auch umgesetzt werden. Ein Beispiel wäre `WHERE YEAR(Datum) = 2020`.

### GROUP BY

Sollte Having verwendet werden müssen alle Attribute die keine Aggregatsfunktionen sind gruppiert werden.

### HAVING

Sollte eine Aggregatsfunktionen verwendet werden und diese im Nachhinein gefiltert werden müssen, beispielsweise nur Ergebnisse die größer sind als eine Konstatne, kann diese Bedingung hinter Having definiert werden: `avg(N.Note) > 3`

### ORDER BY
Datensätze können nach einer oder mehreren Spalten sortiert werden. Wenn der Wert der ersten Spalte, die sortiert werden soll, gleich ist, dann wird zwischen diesen nach der nächsten angegebenen Spalten sortiert. Außerdem kann die Sortierungsrichtung angegeben werden.

|Schlüsselwort|Sortierungsrichtung|
|---|---|
|`ASC`, default|Aufsteigend|
|`DESC`|Absteigend|

### Joins

|Abfragetyp|Funktion|Funktion und Syntax|
|---|---|---|
|CROSS-JOIN|kartesisches Produkt|`FROM Kunde CROSS JOIN Auftrag`|
|EQUI-JOIN|Nullsafe* Join|`WHERE Kunde.auftrags_id = Auftrag.id`|
|INNER JOIN|Nullsafe* Join|`FROM Kunde INNER JOIN Auftrag ON Kunde.auftrags_id = Auftrag.id`|
|LEFT OUTER JOIN|Nullable* Join mit Nullables von der rechten Entität|`FROM Kunde LEFT OUTER JOIN Auftrag ON Kunde.auftrags_id = Auftrag.id`|
|RIGHT OUTER JOIN|Nullable* Join mit Nullables von der linken Entität|`FROM Kunde RIGHT OUTER JOIN Auftrag ON Kunde.auftrags_id = Auftrag.id`|
|FULL OUTER JOIN|Nullable* Join mit Nullables von beiden Entität|`FROM Kunde FULL OUTER JOIN Auftrag ON Kunde.auftrags_id = Auftrag.id`|

- **Nullsafe:** Wenn der Fremdschlüssel null ist und somit auf keine andere Entität referenziert wird der Join nicht gelistet
- **Nullable:** Der Join wird auch ohne gefüllten Fremdschlüssel aufgeführt, die leere Entität ist jeweils auf der anderen Seite des Basis-Outer-Joins

### Subselects

Subselects werden ein Mal gebündelt ausgeführt und die Antwort wird zwischengespeichert, so kann eine Abfrage mit Subselects je nach Anwendungsfall performater sein als ein einziger Select.

Äußere Tabellendeklarationen sind für die Subselects gültig. Subselects können für einen oder mehrere Ergebniszeilen verwendet werden.

```sql
-- Beispiel für ein Subselect im SELECT (Anzahl der Schüler pro Lehrer)
SELECT id, (SELECT count(id) AS schueler FROM Schueler WHERE lehrer = Lehrer.id) FROM Lehrer;

-- Beispiel für ein Subselect im WHERE (Nur Lehrer, die Schüler haben)
SELECT id FROM Lehrer WHERE id IN (SELECT lehrer FROM Schueler);

-- Beispiel für ein Subselect im WHERE (Nur Schüler, die die beste Note haben)
SELECT id FROM Schueler WHERE note = (SELECT max(note) FROM Schueler);
```


## Primary Keys

Ein Primary Key (Primärschlüssel) ist eine Spalte oder eine Kombination von Spalten in einer Tabelle, die jeden Datensatz eindeutig identifiziert. Die Primärschlüssel-Bedingungen umfassen:

- **Eindeutigkeit**: Jeder Wert in der Primärschlüssel-Spalte muss eindeutig sein.
- **Nicht-Null**: Kein Wert in der Primärschlüssel-Spalte darf NULL sein.
- **Automatische Indizierung**: MySQL erstellt automatisch einen Index für den Primärschlüssel, um die Abfrageleistung zu verbessern.

```sql
-- Beispiel für eine Tabellenerstellung mit direkter Angabe eines Primary Keys
CREATE TABLE Lehrer (id INT AUTO_INCREMENT, vorname VARCHAR(50) NOT NULL, nachname VARCHAR(100) NOT NULL, PRIMARY KEY (id);

-- Beispiel für ein ALTER TABLE Statement, welches den PK erst nach der Erstellung der Tabelle festlegt
ALTER TABLE Lehrer ADD PRIMARY KEY (id);
```

## Foreign Keys

Ein Foreign Key (Fremdschlüssel) ist eine Spalte oder eine Kombination von Spalten, die auf den Primärschlüssel einer anderen Tabelle verweist. Die Fremdschlüssel-Bedingungen umfassen:

- **Referenzielle Integrität**: Der Wert eines Fremdschlüssels muss entweder einem Wert des referenzierten Primärschlüssels entsprechen oder NULL sein.
- **Verknüpfung von Tabellen**: Fremdschlüssel ermöglichen die Verknüpfung und Konsistenz zwischen Tabellen.


```sql
-- Beispiel für eine Tabellenerstellung mit direkter Angabe von PK und FKs
CREATE TABLE Lehrer (lehrer_id INT AUTO_INCREMENT, klasse_id INT, PRIMARY KEY (lehrer_id), FOREIGN KEY (klasse_id) REFERENCES klasse(id));

-- Beispiel für ein ALTER TABLE Statement, welches den FK erst nach der Erstellung der Tabelle festlegt
ALTER TABLE Lehrer ADD CONSTRAINT fk_klasse FOREIGN KEY (klasse_id) REFERENCES klasse(id);
```
