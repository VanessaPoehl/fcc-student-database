# Student Database Analytics

Ein Kommandozeilen-basiertes SQL-Analyse-Tool, das eine relationale Universitätsdatenbank abfragt. Dieses Projekt demonstriert fortgeschrittene SQL-Fähigkeiten, indem es komplexe Datenzusammenhänge auswertet und sauber im Terminal ausgibt.

## Über das Projekt

In diesem Projekt wird eine Datenbank mit Informationen über Studenten, ihre Studiengänge (Majors) und belegte Kurse analysiert. Das Bash-Skript `student_info.sh` führt eine Reihe von komplexen SQL-Queries aus, um spezifische Geschäftsfragen zu beantworten (z. B. "Wie ist der Notendurchschnitt pro Studiengang?" oder "Welche Kurse werden von nur einem Studenten belegt?").

Der Fokus liegt hierbei nicht auf der Dateneingabe, sondern auf der **Datenextraktion und Datenanalyse** (Data Retrieval).

## Verwendete Technologien
* **PostgreSQL:** Als relationale Datenbank.
* **Advanced SQL:** Nutzung komplexer Abfragestrukturen zur Datenanalyse.
* **Bash Scripting:** Zur Automatisierung und formatierten Ausgabe der Query-Ergebnisse im Terminal.

## Highlights & SQL Features
Dieses Projekt demonstriert den sicheren Umgang mit fortgeschrittenen SQL-Konzepten:
* **Multi-Table JOINs:** Sicheres Verknüpfen mehrerer Tabellen über `INNER JOIN`, `FULL JOIN` und `RIGHT JOIN`.
* **Aggregatfunktionen:** Berechnung von Durchschnittswerten und Summen (z. B. `COUNT()`, `ROUND(AVG())`).
* **Gruppierungen:** Nutzung von `GROUP BY` und `HAVING` zur Kategorisierung von Datenmengen (z.B. Studenten pro Studiengang).
* **Pattern Matching:** Filtern von Textdaten mit `LIKE` und case-insensitivem `ILIKE`.
* **Logische Operatoren:** Komplexe `WHERE`-Klauseln mit kombinierten `AND` / `OR` Bedingungen.

## Lokale Installation & Nutzung

Um dieses Analyse-Skript auf deinem Rechner auszuführen, benötigst du ein Terminal (Bash) und eine lokal laufende **PostgreSQL**-Instanz.

**1. Repository klonen**
```bash
git clone [https://github.com/VanessaPoehl/fcc-student-database](https://github.com/VanessaPoehl/fcc-student-database)
cd fcc-student-database
```

**2. Datenbank-Nutzer anpassen**
Das Skript ist standardmäßig für den Benutzer `freecodecamp` konfiguriert. Wenn du lokal einen anderen PostgreSQL-Benutzer verwendest:
* Öffne die Datei `student_info.sh` und ändere in der Variablen `PSQL` (Zeile 6) den Eintrag `--username=freecodecamp` zu deinem Nutzer (z. B. `--username=DEIN_LOKALER_DB_NUTZER`).

**3. Datenbank importieren**
Erstelle die Datenbank `students` und fülle sie mit den Testdaten sowie dem Tabellenschema aus dem SQL-Dump:
```bash
psql -U DEIN_LOKALER_DB_NUTZER < students.sql
```

**4. Skript ausführen**
Mache das Bash-Skript ausführbar und starte die automatisierte Analyse:
```bash
chmod +x student_info.sh
./student_info.sh
```
Das Skript führt nun alle SQL-Abfragen durch und gibt die formatierten Ergebnisse direkt in deinem Terminal aus.
