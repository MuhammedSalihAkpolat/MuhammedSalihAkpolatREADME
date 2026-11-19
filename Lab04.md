# Aufgabe 1 · Agenten einrichten und seine Bremsen testen

## Übersicht: Tool & Berechtigungen

| Frage | Antwort |
| :--- | :--- |
| **Welches Tool, welche Version und welches Modell?** | GitHub Copilot in VS Code (VS Code v1.105+, Copilot Chat Extension); Modell: *Auto* (z. B. Claude Sonnet / GPT-4o, wird von Copilot automatisch gewählt) |
| **In welchem Berechtigungsmodus startete das Tool und wie wurde gewechselt?** | Startete im *Ask*- bzw. *Agent*-Modus mit Standardberechtigungen. Über das Modus-Dropdown in der Chat-Ansicht auf **Agent** und **Manual permissions** gewechselt (sowie `"chat.tools.edits.autoApprove": {"**/*": false}` in der `settings.json` gesetzt). |
| **Was tat der Agent ohne zu fragen?** | **Dateien lesen:** Ja (hat `README.md` ohne Nachfrage aufgelistet und gelesen).<br>**Dateien bearbeiten:** Standardmäßig erlaubt VS Code Dateiänderungen im Workspace automatisch, sofern `chat.tools.edits.autoApprove` nicht auf `false` steht; nach der Anpassung hat er vor dem Erstellen von `hello.txt` gefragt.<br>**Befehle ausführen:** Nein – vor der Ausführung von `git log` im Terminal hat er um Bestätigung gebeten. |
| **Wie sieht man Änderungen und wie macht man sie rückgängig?** | Änderungen lassen sich über die Inline-Diff-Ansicht im Editor oder `git diff` im Terminal einsehen. Rückgängig machen über den Button **Restore Checkpoint** im Chatverlauf oder über `git checkout -- .` bzw. Löschen ungetrackter Dateien. |
| **Neue Session starten, Kontextfenster & Quota einsehen** | Neue Session über das **New Chat (`+`)**-Symbol oder `/clear` starten. Die Auslastung des Kontextfensters sowie die verbleibenden monatlichen AI-Credits/Quota werden direkt im Eingabefeld des Chats (und im Copilot-Statusleisten-Menü) angezeigt. |
| **Welche Instruction-Dateien werden gelesen?** | `AGENTS.md` im Hauptverzeichnis des Repositories (sowie `.github/copilot-instructions.md`). |
| **Dürfen Prompts und Code zum Trainieren genutzt werden?** | Bei **Copilot Student** werden Prompts und Code standardmäßig **nicht** für das Modelltraining verwendet. (Bei Copilot Free wird dies in den GitHub-Einstellungen unter *Copilot → Allow GitHub to use my data for AI model training* gesteuert, was ich deaktiviert habe). |

## Warum dieses Tool?

Ich habe mich für **GitHub Copilot in VS Code** entschieden, da es über das GitHub Student Developer Pack kostenlos zugänglich ist und sich ohne zusätzliche CLI-Einrichtung direkt in meinen bestehenden Editor integriert. Der Datenschutz ist gut abgedeckt, weil GitHub bei Copilot Student standardmäßig keine Nutzerdaten zum Training verwendet. Obwohl das Tool selbst proprietär ist, unterstützt es den offenen `AGENTS.md`-Standard, was eine einheitliche Arbeitsweise im Team sicherstellt, selbst wenn andere Mitglieder andere Agenten nutzen. Zudem ermöglichen die visuelle Diff-Ansicht und *Restore Checkpoint* eine sehr sichere Kontrolle aller Änderungen innerhalb des monatlichen Credit-Kontingents.


## AI-Usage:
## Lab 4 · Aufgabe 1
- **Tool & Modell:** GitHub Copilot in VS Code (Agent-Modus, Auto)
- **Prompts:**
  1. `What files are in this folder? Do not change anything.`
  2. `Create a file hello.txt with the line Hello.`
  3. `Run git log.`
  4. `/plan Add a script that counts the files in this folder.`
- **Ergebnis:** Lese-, Schreib- und Terminal-Berechtigungen überprüft, die Testdatei `hello.txt` über *Restore Checkpoint* zurückgesetzt und den Vorschlag im Plan-Modus abgelehnt.
