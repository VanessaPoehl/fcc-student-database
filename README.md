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

### 1. Repository klonen
```bash
git clone https://github.com/VanessaPoehl/fcc-student-database
cd fcc-student-database
```

### 2. Datenbank wiederherstellen
Nutze die bereitgestellte `.sql`-Datei, um die Datenbankstruktur samt Testdaten zu laden.

**Linux / macOS / Git Bash:**
Im Idealfall hast du den Pfad zu PostgreSQL in deinen System-Umgebungsvariablen hinterlegt. Dann funktioniert dieser Standardbefehl:
```bash
psql -U postgres -f students.sql
```

**Windows (PowerShell):**
Falls `psql` nicht direkt gefunden wird, nutze den absoluten Pfad zur PostgreSQL-Installation (passe die Versionsnummer – z. B. 15, 16, 17 oder 18 – entsprechend an):
```powershell
& "C:\Program Files\PostgreSQL\<DEINE_VERSION>\bin\psql.exe" -U postgres -f students.sql
```

*(Hinweis: Das Skript `student_info.sh` nutzt den Usernamen, der in der Variable `PSQL` definiert ist. Bei Problemen stelle sicher, dass dieser mit deinem lokalen Datenbank-Nutzer – meistens `postgres` – übereinstimmt).*

### 3. Skript ausführbar machen und starten

**Unter Linux / macOS / Git Bash:**
```bash
chmod +x student_info.sh
./student_info.sh
```

**Unter Windows (PowerShell):**
```powershell
bash student_info.sh
```

---

## Troubleshooting für lokale Setups (Windows)

**1. "psql: command not found" im Skript**
Da das Bash-Skript den globalen `psql`-Befehl nutzt, muss dein Terminal wissen, wo PostgreSQL installiert ist.
*Lösung:* Füge den Pfad temporär zu deiner Terminal-Sitzung hinzu (passe die Versionsnummer an):
```bash
export PATH=$PATH:"/c/Program Files/PostgreSQL/18/bin"
```

**2. Das Skript fragt ununterbrochen nach dem Datenbank-Passwort**
Wenn deine lokale PostgreSQL-Installation passwortgeschützt ist, blockiert `psql` das Skript, da es bei jeder Abfrage nach dem Passwort verlangt.
*Lösung:* Speichere das Passwort temporär für deine aktuelle Terminal-Sitzung. Führe dazu (z. B. in der Git Bash) aus:
```bash
export PGPASSWORD="dein_passwort"
```

**3. Skript wirft Syntax-Fehler oder verhält sich merkwürdig (CRLF vs LF)**
Windows verwendet standardmäßig `CRLF` für Zeilenumbrüche, während Bash-Skripte `LF` erwarten. 
*Lösung:* Öffne die Datei `student_info.sh` in deinem Code-Editor (z. B. VS Code), klicke unten rechts in der Statusleiste auf `CRLF` und ändere es zu **`LF`**. Speichere die Datei ab und starte das Skript erneut.
