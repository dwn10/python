# SQL - LT4V2 - Projekt
Verwendete Technologien:

```javascript
const Projects = {
  	code: ["HTML", "CSS", "Javascript", "SQL"],
	technologies: {
	devTool: ["VS-Code", "PHP MyAdmin", "Xampp", "DB-Diagram"]
	}
}
```


## Quellen für dieses Projekt
<ul>
	<li><a href="https://www.iso.org/standard/76583.html">ISO-Org</a></li>
	<li><a href="https://dbdiagram.io/">DB-Diagram</a></li>
	<li><a href="https://dev.mysql.com/downloads/mysql/">MySQL</a></li>
	<li><a href="https://www.apachefriends.org/index.html">XAMPP</a></li>
</ul>

## Projektbeschreibung
- (Optional) Der Kundenwunsch, der noch nicht datenbank-gerecht formuliert ist. Anhand dessen können Sie die Normalisierung demonstrieren (ähnlich Folie 28 und folgende, aber wahrscheinlich komplizierter).
- Erstellen Sie ein ER-Diagramm.
- Erstellen Sie ein Relation-Modell.
- Erstellen Sie ein physikalisches Modell (das Relationenmodell, aber mit Datentypen).
- Erstellen Sie ein SQL-Skript, das die Datenbank erzeugt.
- Erstellen Sie ein SQL-Skript, das die Datenbank mit Beispieldaten füllt.
- Erstellen Sie verschiedene SQL-Statements mit Abfragen, die Fragen zum Datenbestand beantworten
- Dokumentation, welche die User-Story beschreibt und die Besonderheiten, und in der die Diagramme zu finden sind.
- Erstellen Sie ein Applikation mit html, css und javascript, um Daten einzugeben, zu ändern, löschen und Abfragen zu tätigen

## Erstellen Sie ein ER-Diagramm: 
`>> IMG + VIDEO <<`

<a href="#"><img src="https://media.discordapp.net/attachments/1185882189393575976/1214726352989855825/5.JPG?ex=65fa2913&is=65e7b413&hm=3c41444bcd4b4e3ffae1d0bf010d2dc404cb12c189915f8f10a625dd35b8736d&=&format=webp&width=1085&height=597" style="height: 50%; width:50%;"/></a>

<a href="https://media.discordapp.net/attachments/1185882189393575976/1215143276919787570/SQL.gif?ex=65fbad5d&is=65e9385d&hm=ebadd7e45bcb408cdbefd453efd1f7e536dfb658ca506f93cba0b1de3908a090&=&width=1062&height=597"><img src="https://media.discordapp.net/attachments/1214730549969813504/1215142862778269749/18.JPG?ex=65fbacfa&is=65e937fa&hm=c17600d3ed6e21abdd34ab82cb81fee527f8169e1eae01cfc8fcb481f68ab454&=&format=webp&width=1439&height=579" style="height: 50%; width:50%;"/></a>

## Dokumentation, welche die User-Story beschreibt und die Besonderheiten
```sql
-- Datenbank erstellen
CREATE DATABASE IF NOT EXISTS IT_System_GmbH;

-- Datenbank nutzen
USE IT_System_GmbH;

-- Tabelle Abteilung
CREATE TABLE Abteilung (
    id_Abteilung INT PRIMARY KEY AUTO_INCREMENT,
    Bezeichnung VARCHAR(255) NOT NULL,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

-- Tabelle Projekt
CREATE TABLE Projekt (
    id_Projekt INT PRIMARY KEY AUTO_INCREMENT,
    Bezeichnung VARCHAR(255) NOT NULL
);

-- Tabelle Vorgang
CREATE TABLE Vorgang (
    id_Vorgang INT PRIMARY KEY AUTO_INCREMENT,
    id_Projekt INT,
    id_Mitarbeiter INT,
    Bezeichnung VARCHAR(255) NOT NULL,
    Beginn DATE,
    Ende DATE,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (id_Projekt) REFERENCES Projekt(id_Projekt),
    FOREIGN KEY (id_Mitarbeiter) REFERENCES Mitarbeiter(id_Mitarbeiter)
);

-- Tabelle Freelancer
CREATE TABLE Freelancer (
    id_Freelancer INT PRIMARY KEY AUTO_INCREMENT,
    Adresse VARCHAR(255) NOT NULL,
    Email VARCHAR(255) NOT NULL,
    Stundensatz FLOAT NOT NULL,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

-- Tabelle Freelancerauftrag
CREATE TABLE Freelancerauftrag (
    id_Freelancerauftrag INT PRIMARY KEY AUTO_INCREMENT,
    id_Freelancer INT,
    id_Vorgang INT,
    Beschreibung VARCHAR(255) NOT NULL,
    Arbeitsstunden FLOAT NOT NULL,
    Dokument VARCHAR(255),
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (id_Freelancer) REFERENCES Freelancer(id_Freelancer),
    FOREIGN KEY (id_Vorgang) REFERENCES Vorgang(id_Vorgang)
);

-- Beziehungen
ALTER TABLE Mitarbeiter ADD FOREIGN KEY (id_Abteilung) REFERENCES Abteilung(id_Abteilung);
ALTER TABLE Vorgang ADD FOREIGN KEY (id_Projekt) REFERENCES Projekt(id_Projekt);
ALTER TABLE Vorgang ADD FOREIGN KEY (id_Mitarbeiter) REFERENCES Mitarbeiter(id_Mitarbeiter);
ALTER TABLE Freelancerauftrag ADD FOREIGN KEY (id_Freelancer) REFERENCES Freelancer(id_Freelancer);
ALTER TABLE Freelancerauftrag ADD FOREIGN KEY (id_Vorgang) REFERENCES Vorgang(id_Vorgang);

-- Geben Sie Daten in die Tabelle ein
INSERT INTO `abteilung` (`id_Abteilung`, `Bezeichnung`, `created_at`) VALUES (NULL, 'IT', CURRENT_TIMESTAMP);
INSERT INTO `abteilung` (`id_Abteilung`, `Bezeichnung`, `created_at`) VALUES (NULL, 'Marketing', CURRENT_TIMESTAMP);
INSERT INTO `abteilung` (`id_Abteilung`, `Bezeichnung`, `created_at`) VALUES (NULL, 'HR', CURRENT_TIMESTAMP);
INSERT INTO `abteilung` (`id_Abteilung`, `Bezeichnung`, `created_at`) VALUES (NULL, 'Entwicklung', CURRENT_TIMESTAMP);

-- Tabellen zeigen
SELECT * FROM `abteilung` WHERE 1;
SELECT * FROM `abteilung` WHERE `id_Abteilung`= 1;
```
## Credits:

**Author:**

```bash
  Darwin Paz
```
**Unter der Leitung von:**
```bash
  Norbert Maier
```

```http
  Abgabetermin:
```

| Stadt: | Datum:     | Bis:                       |
| :-------- | :------- | :-------------------------------- |
| `Darmstadt`      | `Fr - 15.03.2024` | **16:30 Uhr**  |
