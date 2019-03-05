---
title: Eine webbasierte Plattform zur Datenvisualisierung für MATSim
author: \textbf{William Charlton}, Technische Universität Berlin, Germany
---

---

# 1. Einleitung

MATSim ist ein Open-Source-Framework für die Implementierung großer, agentenbasierter Transportsimulationen. MATSim wird häufig in der Transportforschung in akademischen Umgebungen eingesetzt und gewinnt als praktisches Werkzeug in der Praxis in der Praxis an Bedeutung.

Da sich MATSim von den Grenzen der akademischen Forschung hin zu einer eher öffentlichen Rolle bewegt, besteht eine bemerkenswerte Lücke: Es gibt keine webbasierten, interaktiven Tools zur Verbreitung von MATSim-Ergebnissen. Dies stellt eine Herausforderung für die Verwendung von MATSim in öffentlichen Richtlinieneinstellungen dar. Die einzigen Personen, die die Ergebnisse sinnvoll untersuchen und untersuchen können, sind diejenigen, die über umfassende technische Kenntnisse und Zugriff auf die betreffende spezialisierte Software und umfangreiche Datensätze verfügen.

Diese Forschung untersucht einen Weg, um diese Lücke zu schließen: den Aufbau einer offenen webbasierten Visualisierungsplattform, die speziell zur Ergänzung von MATSim entwickelt wurde.

# 2. Motivation

Die rasante Weiterentwicklung der Internet-Browsing-Technologien in den letzten fünf Jahren hat es dem Webbrowser ermöglicht, mehr als je zuvor "Anwendungen" zu erledigen: Hintergrundverarbeitung, dreidimensionales Rendering mit GPU-Beschleunigung, Offline-Unterstützung und vieles mehr. Die Kombination dieser Technologien und ihrer Standardimplementierungen auf jedem gängigen Hardwaretyp und Betriebssystem macht das Web jetzt zu einer sehr überzeugenden Plattform.

Für die MATSim-Forschung lautet die Frage: Kann ein Webbrowser wirklich nützlich sein, um Ergebnisse zu ermitteln und Ergebnisse zu liefern, wenn die Datensätze so groß sind? Die Beantwortung dieser Frage ist die Hauptmotivation für diese Forschung. Wesentlich

Derzeit führt die Analyse der MATSim-Ergebnisse zu Forschungsberichten, PDFs, Bildschirmaufzeichnungen und Präsentationen. Ein Online-Dashboard mit Ergebnissen, das ein Benutzer untersuchen und manipulieren könnte, wäre nicht nur interaktiver, sondern könnte auch Ergebnisse enthüllen, die die ursprünglichen Analysten nicht erwartet hatten.

# 3. Anforderungen

Das Forschungsteam der TU Berlin hat mehrere Diskussionen geführt, bevor überhaupt Code geschrieben wurde: Das heißt, wenn wir ganz am Anfang beginnen und etwas komplett Web-basiertes und offenes Design entwerfen könnten, was wären die Mindestvoraussetzungen dafür wirklich nützlich? Die folgenden Anforderungen ergaben sich aus diesen Diskussionen.

## Anforderung 1: Webbrowser-basiert

Angesichts der oben genannten Motivation und der Hypothese, dass die moderne Webplattform für umfangreiche Visualisierungsaufgaben bereit ist, besteht die naheliegendste Anforderung darin, dass das Produkt dieser Untersuchung mit jedem modernen Webbrowser zusammenarbeiten muss.

Verschiedene spezifische Web-Technologien, die in den letzten Jahren entwickelt und verfügbar gemacht wurden, ermöglichen uns die Durchführung dieser Forschung: HTML 5, CSS 3, WebGL, ECMA Script 6 und Web Workers. In Kürze sind diese Technologien:

Eine Komplikation bei der Webentwicklung ist, dass die großen Webbrowser-Anbieter diese Technologien zu ihren eigenen Zeitplänen implementieren, manche viel schneller als andere. Komplizierter wird die Tatsache, dass Endbenutzer ihren Browser nicht häufig (oder überhaupt) aktualisieren. Dadurch entsteht eine Landschaft, in der es eine Technologie-Annahmekurve mit einem sehr langen Schwanz gibt. Entwickler jeder Website müssen eine bewusste Entscheidung darüber treffen, wo sie die Linie ziehen und die für ihre Website erforderlichen Technologien auswählen müssen, um zu wissen, dass einige Benutzer mit älteren Browsern entweder keine optimale Erfahrung haben oder überhaupt keinen Zugriff auf die Website haben .

Für diese Forschung erforschen wir bewusst die neuesten \_Standard-Web-Technologien, mit der Erwartung, dass der Zugang zu diesen Technologien in Zukunft immer häufiger wird. Daher zielen wir ab 2019 auf die neuesten Versionen moderner Webbrowser ab, darunter Google Chrome, Mozilla Firefox und Apple Safari. Alle drei Browser unterstützen die oben aufgeführten Technologien vollständig und, was wichtig ist, alle drei automatischen Updates werden automatisch durchgeführt, um sicherzustellen, dass die meisten Benutzer dieser Browser auf dem neuesten Stand bleiben, wenn sich diese Technologien weiterentwickeln.

## Anforderung 2: Open Source

Das gesamte Projekt, einschließlich des gesamten Front-End (Browser) und Back-End (Server), muss vollständig Open Source sein. Die im Rahmen dieser Forschung entwickelte Software ist vollständig mit der GNU General Public License v3, allgemein als "GPL" (Free Software Foundation, 2007) bekannt, lizenziert. Dies entspricht der Lizenz von MATSim selbst. Einige andere Open-Source-Lizenzen wurden in Betracht gezogen, darunter die MIT-Lizenz und die Apache Public License. Der Vorteil, eine gemeinsame Lizenz mit MATSim zu teilen, wiegt jedoch alle möglichen Vorteile eines Wechsels zu anderen offenen Lizenzen auf.

## Anforderung 3: Verwenden Sie gute Standardeinstellungen mit minimaler Konfiguration und lassen Sie sich einschätzen

Seit ihrer Gründung hat sich die Webplattform unnachgiebig auf Einfachheit und reibungslose Benutzerentwicklung konzentriert. Benutzer sind es gewohnt, sich mit einer Site sofort vertraut zu machen - oft innerhalb von Sekunden nach ihrer ersten Interaktion. Aufgrund dieser Erwartung ist es wichtig, dass diese Forschung den aktuellen Best Practices für Benutzeroberfläche (UI) und User Experience (UX) folgt. Konkret bedeutet dies, dass Sie bekannte UI-Paradigmen wie na verwenden

How satisfied are you with Google Translate today?
Very satisfiedSomewhat satisfiedNeither satisfied nor dissatisfiedSomewhat dissatisfiedVery dissatisfied
5000/5000
Character limit: 5000
Bewährungsbarrieren und Breadcrumbs, Trennen der Konfiguration von der Verwendung, Beschränken der Einstellungen und Optionen auf das Nötigste und "Meinungsbildung", d. h. Anregen für einen korrekten Weg, eine Aufgabe auszuführen.

## Anforderung 4: Eine erweiterbare Plattform

Jeder Anwendungsfall der Datenvisualisierung ist anders. Es gibt keine Möglichkeit vorherzusehen, wie das Werkzeug verwendet wird. Wenn die Plattform zu allgemein ist, ist sie überhaupt nicht nützlich. Wenn dagegen nur fest codierte Visualisierungen für bestimmte Projekte erstellt werden, werden sie auf "Demo-Ware" gesetzt, was bedeutet, dass es sich um eine erfolgreiche Technologiedemonstration handelt, die jedoch für echte Benutzer nicht wirklich nützlich ist.

Um diese Anforderung zu erfüllen, muss die Softwareplattform erweiterbar sein: Es werden grundlegende Funktionen und Vorlagen bereitgestellt, ein Benutzer mit einem gewissen Grad an Codierkenntnissen sollte jedoch in der Lage sein, neue Visualisierungen zu erstellen, die von den Forschern nicht erwartet werden.

# 4. Erste Versuche

In einigen ersten Versuchen wurden verschiedene Ansätze untersucht, bevor sie sich einem Technologie-Stack zuwenden.

## Visualisierung zeitabhängiger Daten auf einer geografischen Karte

Zwei beliebte webbasierte Javascript-Bibliotheken wurden zur Anzeige geografischer Daten getestet. Prospekt und Mapbox GL. Es wurde ein einfacher Testfall mit MATSim-Simulationsausgaben entwickelt, mit dem Ziel, das aggregierte Straßenverbindungsvolumen nach Tageszeit anzuzeigen.

Mapbox GL entwickelte sich deutlich besser als Leaflet. Die Verwendung von 3D-Vektorgrafiken-Mappings anstelle von voreingestellten Kacheln wurde durch Mapbox GL für ein viel angenehmeres Benutzererlebnis mit glatten Animationen zwischen den Zoomstufen und einer besseren Hintergrundverarbeitung während des Ladens der Seite geschaffen. Aus diesen Gründen wurde Mapbox GL als Basiskarte für die verbleibenden geografischen Visualisierungen ausgewählt.

## Visualisierung nicht geografischer Daten

Nach dem Experimentieren mit mehreren Open-Source-Paketen, darunter D3, Raphael, Morris und anderen, zeigte das Paket Vega-Lite (Satyanarayan, 2016) viele der gewünschten Eigenschaften. Vega-lite folgt einer deklarativen Syntax "Grammatik der Grafiken", wie sie von Wilkinson (2005) popularisiert wird, und diese Grammatik ermöglicht eine kurze Beschreibung der bedeutungsvollen Komponenten einer Grafik.

## Umgang mit großen Datensätzen

MATSim-Netzwerkdateien sind normalerweise klein genug, um in den RAM-Speicher zu passen. MATSim-Planungsdateien und Ereignisdateien können jedoch viel größer als der RAM-Speicher sein, so dass eine sorgfältige Überlegung erforderlich ist. Es stellte sich schnell heraus, dass diese lokale browserbasierte Zwischenspeicherung und Speicherung für MATSim-Ausgaben nicht ausreicht. Ein Client-Server-Paradigma stellt sich als eine praktikable Alternative heraus: Der Browser ist nur das Frontend für die umfangreicheren Verarbeitungs- und Speicheraufgaben, die auf dem Server eines anderen Benutzers ausgeführt werden.

# 5. Plattformarchitektur

Die Client / Server-Architektur hängt von einer Reihe von Back-End-Diensten für die Benutzerauthentifizierung und die Dateispeicherung ab. Diese Back-End-Services werden in diesem Dokument nicht beschrieben. Es genügt zu erwähnen, dass das Frontend mit ihnen kommuniziert, um festzustellen, auf welche Ressourcen ein Benutzer Zugriff hat, und eine API zum Abfragen und Abrufen dieser Dateien und Ressourcen bereitstellt.

Die Front-End-Architektur besteht aus mehreren interagierenden Komponenten:

## "Vue" Einzelseitenanwendung

Das zur Erstellung der Anwendung verwendete primäre Framework wird als "Vue JS" (Vue) bezeichnet. Vue ist ein Framework zum Erstellen interaktiver Benutzeroberflächen im Web und hängt von HTML5, CSS 3 und Javascript ab. Vue bietet viele Dienste, mit denen sich eine Webseite mehr wie eine voll funktionsfähige Anwendung verhalten kann, einschließlich Statusverwaltung, Routing zwischen verschiedenen URLs und Codierung von Code auf eine Weise, die die Wiederverwendung und lockere Kopplung fördert.

Vue-Komponenten umfassen jeweils drei Elemente, die für das moderne Web erforderlich sind: das HTML-Layout, der JavaScript-Code und die CSS-Formatierung. Komponenten interagieren nur über genau definierte Pfade von Eigenschaften und Ereignissen miteinander, wodurch die Fehlersuche verbessert wird.

## System erstellen

Das Build-System einer modernen Webanwendung ist ziemlich komplex und das Javascript-Ökosystem ändert sich schnell. Nach zahlreichen Iterationen umfasst das aktuelle Build-System eine Reihe einzelner Tools, die alle zusammenarbeiten, um die endgültigen Elemente zu erstellen, die an den Browser eines Benutzers gesendet werden. Zu diesen Tools gehören die Vue-Befehlszeilenschnittstelle (CLI), der NPM-Paketmanager, Webpack, Babel und TypeScript.

## Visualisierungs-Plug-Ins

Eine der Hauptanforderungen dieser Forschung besteht darin, ein System zu erstellen, mit dem neue Visualisierungen schnell erstellt und in das vorhandene Framework aufgenommen werden können, um neue Fähigkeiten zu generieren.

Die Vue-Komponentenarchitektur ermöglicht dies. Um eine neue Visualisierung zu erstellen, kopiert ein Entwickler eine vorhandene "leere" Visualisierungsvorlage, gibt einen neuen Namen, gibt die erforderlichen Dateieingaben und -parameter an und verwendet dann die oben beschriebenen Bibliotheken, um den Code entsprechend ihren Anforderungen zu ändern.

Dies erfordert derzeit umfangreiche Programmierkenntnisse in Javascript. Es ist kein System, das mit einem Mausklick wie ein Online-Datenerkennungswerkzeug funktioniert.

4874/5000
Character limit: 5000

# 6. Ergebnisse: Der aktuelle Status des Tools

Eine Arbeitsinstanz der Plattform ist jetzt online und unter https://viz.vsp.tu-berlin.de verfügbar. Beispieldatensätze werden hochgeladen, und vorgefertigte Visualisierungen sind öffentlich zugänglich, um den aktuellen Status der Plattform zu demonstrieren. Es gibt auch ein Benutzeranmeldesystem, mit dem Forscher das System erweitern und experimentieren können, ohne dass Daten oder teilweise abgeschlossene Arbeiten der Öffentlichkeit zugänglich gemacht werden.

Grundlegende Benutzer-, Projekt- und Dateiverwaltungsfunktionen sind betriebsbereit. Dies beinhaltet das Gruppieren von Dateien nach Modelllauf oder nach anderen benutzerdefinierten Tags.

Derzeit sind verschiedene Arten von Aggregatvisualisierungen in Betrieb:

- Ursprungs- / Zielflüsse zwischen aggregierten Gebieten
- Link fließt nach Tageszeit
- Transit Supply Explorer, in dem alle Transitstrecken angezeigt werden und der Benutzer sehen kann, welche Routen bestimmte Haltestellen und Links bedienen.
- Sankey-Diagramme, die verwendet werden können, um Änderungen / Flüsse zwischen Szenarien über mehrere Auswahlmöglichkeiten hinweg darzustellen, z. B. Moduswechsel zwischen zwei Szenarien
- Emissionsniveaus auf geografischer Netzbasis

Zusätzlich ist eine disaggregierte Visualisierung verfügbar:

- Eine Fahrzeugflusssimulation, die die einzelnen Fahrzeugagenten in Echtzeit im Netzwerk darstellt. Die Details dieser Visualisierung werden in der Begleitarbeit von J. Laudan (Zitat ausstehend) beschrieben.

In den folgenden Abbildungen in _Abbildung 1_ finden Sie Beispiele für den aktuellen Status der Benutzeroberfläche.

! [Beispielvisualisierungen, 1a - 1f](all-figures.png)

## Leistung

Selbst mit moderner Hardware und den neuesten Browsern ist es schwierig, mit disaggregierten MATSim-Daten performante, visuell ansprechende Ergebnisse zu erzielen. Die Fahrzeugflusssimulation hängt stark vom Back-End-Server ab, um in Echtzeit Simulations- "Frames" für den Browser zu erstellen und zu liefern, sodass der Browser die Daten lediglich rendern muss.

Verschiedene Aggregationsebenen erleichtern die Visualisierung von MATsim-Daten. Dies zeigt sich in der Vielzahl der Visualisierungen, die diese Forschung mit aggregierten Daten erstellen konnte.

Auf dieser Grundlage müssen noch weitere Anstrengungen unternommen werden, um die jetzt verfügbaren Back-End-Serverfunktionen zu nutzen.

# 7. Schlussfolgerungen und Ausblick

Mit den verschiedenen Technologien zu experimentieren und die verschiedenen Teile zusammenzubringen war eine enorme Aufgabe, die viel länger als erwartet dauerte. Diese Entscheidungen liegen jedoch jetzt hinter uns und die Plattform ist ziemlich stabil geworden.

In wenigen Tagen können die Forscher nun eine neue Visualisierung erstellen. Zwar sind die Forscher mit den inneren Abläufen des Systems bestens vertraut, aber es war trotzdem ermutigend, neue Visualisierungen in so kurzer Zeit von der Idee zum groben Entwurf zu bringen.

Keine der oben aufgelisteten Visualisierungen ist besonders bahnbrechend oder optisch atemberaubend. Alle können leicht in anderen Tools erstellt werden. Dies ist zwar etwas enttäuschend, aber die Offenheit der Plattform, die keine Software-Installation durch Endbenutzer erfordert, bietet immer noch einen Vorteil: Sie öffnet die Anzeige der MATSim-Ergebnisse für die Öffentlichkeit und für Entscheidungsträger, auch wenn sie keinen Zugriff darauf haben Desktop-Mapping- oder Reise-Prognosesoftware.

Bemerkenswert ist auch, dass die Welt während der Entwicklung dieser Plattform nicht stillgestanden hat. Erst im vergangenen Jahr wurden bedeutende Datenvisualisierungsbemühungen von gut finanzierten Unternehmen wie Uber und anderen veröffentlicht. Es gibt berechtigte Fragen, inwieweit diese Arbeit von großen, gut finanzierten, professionellen Coding-Teams abgelöst werden könnte.

Trotz dieser Bedenken ist das MATSim-Visualisierungs-Framework einsatzbereit und wird gerade erst für die Forscher seiner Abteilung nützlich. Dies ist ein gutes Zeichen für die weitere Entwicklung in naher Zukunft.

Der gesamte Code ist auf der Website von MATSim Github unter https://github.com/matsim-org/viz verfügbar.
