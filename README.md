# 🎉 Los geht's – Zeit, Spiele zu bauen! 🎮🚀

Willkommen bei KreaCoder! Jedes Team baut sein eigenes Browserspiel, und eine KI übernimmt das Programmieren. Ihr seid Game Designer, Artists, Autor*innen und Sounddesigner*innen, die KI setzt eure Ideen um.

## So startet ihr

1. Öffnet diesen Ordner in VS Code. Wenn VS Code fragt, ob es die empfohlenen Erweiterungen installieren soll: **Ja** (das ist „Live Server“, damit läuft euer Spiel im Browser).
2. Kopiert das Asset-Paket (Grafiken, Sounds, Musik) vom USB-Stick bzw. vom Workshop-Server in den Ordner `asset-library/` in diesem Repo.
3. Startet euren KI-Agenten (Claude Code, Copilot, Codex, ...) und sagt ihm, welches Team ihr seid und wie viele ihr seid, z. B. *„Wir sind Team 2, zu zweit, und wollen ein Spiel machen, in dem ...“*
4. Erzählt ihm von eurem Spiel, in jeder beliebigen Sprache. Um alles Technische kümmert er sich selbst, auch ums Speichern und darum, dass euer Team eure Änderungen bekommt.
5. Zum Spielen: Rechtsklick auf `games/<euer-spiel>/index.html` → **„Open with Live Server“**. Der Browser lädt nach jeder Änderung automatisch neu.

Alle Spiele online: siehe den GitHub-Pages-Link im „About“-Bereich des Repositorys.

## Ablauf

| Wann | Inhalt | Ergebnis |
|---|---|---|
| **Tag 1, Block 1** | Vision und Ablauf, Setup-Check, erstes „Hallo Spiel“ (ein Quadrat, das sich bewegt), Ideen pitchen, Teams bilden | Läuft bei allen, Idee steht |
| **Tag 1, Block 2** (bis mittags) | Kern-Mechanik: Steuerung, Ziel, Gewinnen/Verlieren, so hässlich wie nötig. Zum Schluss `PLAN.md` für die KI-Schicht schreiben | Prototyp, der 30 Sekunden Spaß macht |
| **KI-Schicht 1** (Nachmittag bis Nacht) | Agent arbeitet `PLAN.md` ab (z. B. mehr Level, Menü, Bugfixes) und testet selbst. Ihr könnt zwischendurch reinschauen, müsst aber nicht | Morgens ein Stand zum Begutachten |
| **Tag 2, Block 3** | Ergebnis der KI-Schicht ansehen, gegenseitiges Playtesting, Schwerpunkt wählen: Look, Sound, Story, Level oder Mechanik | Klare Liste, was das Spiel ausmacht |
| **Tag 2, Block 4** (bis mittags) | Kreativ-Block: Assets gestalten oder einbauen, Feintuning (Gefühl, Tempo, Schwierigkeit). Neuen `PLAN.md` schreiben | Spiel hat eine eigene Identität |
| **KI-Schicht 2** (Nachmittag bis Nacht) | Agent: Bugs aus dem Playtest, Titel- und Endbildschirm, Mobile-Steuerung, Feinschliff | Spielbare Version |
| **Tag 3, Block 5** | Letzte Änderungen (ca. 30 Min.), veröffentlichen, alle stellen ihr Spiel vor und spielen gegenseitig | Spielbare Links für alle |

**KI-Schicht:** Am Ende von Block 2 und 4 schreibt ihr mit eurem Agenten den `PLAN.md` in eurem Spielordner. Dann startet **eine Person pro Team** einen Cloud-Agenten (Claude Code im Web, Codex Cloud oder Copilot-Agent) mit der Aufgabe „Arbeite `PLAN.md` in `games/<euer-spiel>/` ab, halte dich an AGENTS.md“, und ihr könnt den Laptop zuklappen. Zu Beginn des nächsten Blocks übernimmt euer Agent das Ergebnis.

Viel Spaß! ✨

## Für KI-Agenten

Siehe [AGENTS.md](AGENTS.md).
