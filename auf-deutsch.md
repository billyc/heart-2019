---
title: Eine webbasierte Anwendung zur Datenvisualisierung für MATSim
author: \textbf{William Charlton}, Technische Universität Berlin
---

---

## Einleitung

MATSim (Horni, et al. 2016) wird häufig für die Transportforschung in akademischen Umgebungen eingesetzt und gewinnt als Hilfsmittel für Planungszusammenhänge in der Praxis an Bedeutung. Da sich MATSim von den Grenzen der akademischen Forschung hin zu einer eher öffentlichen Rolle bewegt, besteht eine bemerkenswerte Lücke: Es gibt keine webbasierten, interaktiven Tools zur Verbreitung von MATSim-Ergebnissen. Dies stellt eine Herausforderung für die Verwendung von MATSim in öffentlichen Richtlinieneinstellungen dar: Nur Personen mit umfassenden technischen Kenntnissen und Zugriff auf spezielle Software können die Ergebnisse sinnvoll untersuchen und untersuchen.

Diese Forschung versucht, diese Lücke zu schließen, indem eine offene webbasierte Visualisierungsanwendung geschaffen wird, die speziell zur Ergänzung von MATSim entwickelt wurde.

## Anforderung

Das Forschungsteam der TU Berlin hatte mehrere "leere Diskussionsrunden" abgehalten, bevor Code geschrieben wurde. Die folgenden Anforderungen ergaben sich aus diesen Diskussionen.

- ** Anforderung 1: Moderne Webbrowser-basierte. ** Verschiedene neuere Webtechnologien ermöglichen diese Untersuchung: HTML 5, CSS 3, WebGL, ECMA Script 6 und Web Workers. Leider aktualisieren Endbenutzer ihre Browser nicht häufig. Dies schafft eine Technologie-Annahmekurve mit einem sehr langen "Schwanz". Wir haben uns für die neuesten Web-Technologien entschieden, mit der Erwartung, dass diese in Zukunft weiter verbreitet werden.
- ** Anforderung 2: Open Source. ** Das gesamte Projekt ist vollständig Open Source und unter der GNU General Public License v3 lizenziert.
- ** Anforderung 3: Verwenden Sie gute Standardeinstellungen mit minimaler Konfiguration. ** Webbenutzer sind gewohnt, sich mit einer Site sofort vertraut zu machen - oft innerhalb von Sekunden nach ihrer ersten Interaktion. Es ist äußerst wichtig, dass diese Forschung den aktuellen Best Practices für Benutzeroberfläche und Benutzererfahrung folgt.
- ** Anforderung 4: Eine erweiterbare Plattform. ** Jeder Anwendungsfall der Datenvisualisierung ist anders. Es werden grundlegende Funktionen und Vorlagen bereitgestellt, ein Benutzer mit einem gewissen Grad an Codierkenntnissen sollte jedoch neue Visualisierungen erstellen können, die von den Forschern nicht erwartet werden.

## Erste Versuche

In ersten Experimenten wurden verschiedene Ansätze bewertet, bevor ein Front-End-Technologie-Stack eingesetzt wurde. Beachten Sie, dass das Backend in einem Begleitpapier von J. Laudan beschrieben wird.

** Visualisieren von Daten auf einer geografischen Karte. ** Zwei beliebte webbasierte Javascript-Bibliotheken wurden zur Anzeige geografischer Daten getestet. Prospekt und Mapbox GL. Mapbox GL handhabte große Datensätze viel besser als Leaflet. Die Verwendung von 3D-Vektorgrafiken für Mapbox GL anstelle von voreingestellten Kacheln sorgt für ein viel glatteres visuelles Erlebnis.

** Nicht geografische Daten. ** Experimente mit vielen verschiedenen Grafik- und Diagrammbibliotheken führten zum Paket Vega-Lite (Satyanarayan, 2016). Vega-lite folgt einer deklarativen Syntax "Grammatik der Grafiken", wie sie von Wilkinson (2005) popularisiert wird.

2769/5000
Character limit: 5000

## Ergebnisse: Der aktuelle Status des Werkzeugs

Eine Arbeitsinstanz der Plattform ist jetzt online und unter https://viz.vsp.tu-berlin.de verfügbar. Beispieldatensätze werden hochgeladen, und vorgefertigte Visualisierungen sind öffentlich zugänglich, um den aktuellen Status der Plattform zu demonstrieren.

Derzeit sind verschiedene Arten von Aggregatvisualisierungen in Betrieb:

- Ursprungs- / Zielflüsse zwischen aggregierten Gebieten
- Link fließt nach Tageszeit
- Ein Transitversorger
- Sankey-Diagramme, die Flüsse zwischen mehreren Auswahlmöglichkeiten darstellen, z. B. Moduswechsel zwischen zwei Szenarien
- Emissionsniveaus auf geografischer Netzbasis

Und eine disaggregierte Visualisierung ist verfügbar:

- Eine Fahrzeugflusssimulation, bei der Fahrzeuge in Echtzeit im Netzwerk fahren.

** Visualisierungs-Plug-Ins. ** Neue Visualisierungen können schnell erstellt und dem Framework hinzugefügt werden, um neue Funktionen zu generieren. Die Komponentenarchitektur von Vue "Einzelseitenanwendung" ermöglicht dies. Um eine neue Visualisierung zu erstellen, kopiert der Entwickler eine vorhandene leere Visualisierungsvorlage, gibt die erforderlichen Eingaben und Parameter an und ändert den Javascript-Code entsprechend den Anforderungen. Dies erfordert derzeit umfangreiche Kodierungskenntnisse in Javascript. Es ist kein System, das wie ein Online-Datenerkennungs-Tool "Zeigen und Klicken" ist.

In den folgenden Abbildungen in _Abbildung 1_ finden Sie Beispiele für den aktuellen Status der Benutzeroberfläche.

! [Beispielvisualisierungen, 1a - 1f](all-figures.png)

## Leistung

Selbst mit moderner Hardware und den neuesten Browsern ist es schwierig, mit disaggregierten MATSim-Daten performante, visuell ansprechende Ergebnisse zu erzielen. Beispielsweise hängt die Fahrzeugflusssimulation stark vom Back-End-Server ab, um Simulationsrahmen für den Browser zu erzeugen.

Aggregierte Daten lassen sich viel einfacher visualisieren. Es müssen weitere Anstrengungen unternommen werden, um die jetzt verfügbaren Back-End-Serverfunktionen zu nutzen.

## Schlussfolgerungen und Ausblick

Mit den verschiedenen Technologien zu experimentieren und alles zusammenzubringen war eine enorme Aufgabe, aber die Plattform ist jetzt ziemlich stabil.

Innerhalb weniger Tage können die Forscher eine neue Visualisierung erstellen. Es ist ermutigend zu sehen, wie Visualisierungen in so kurzer Zeit von der Idee zum groben Entwurf werden.

Die Welt der Datenvisualisierung steht nicht still. Vor kurzem wurden wichtige Datenvisualisierungsbemühungen von gut finanzierten Unternehmen wie Uber veröffentlicht. Es gibt berechtigte Fragen, wie diese Arbeit von großen, professionellen Coding-Teams abgelöst werden könnte.

Trotz dieser Bedenken ist das MATSim-Visualisierungs-Framework einsatzbereit und wird für Forscher von Nutzen. Dies ist ein gutes Zeichen für die weitere Entwicklung.

Der gesamte Code ist auf der Website von MATSim Github unter https://github.com/matsim-org/viz verfügbar.
