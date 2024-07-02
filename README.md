## Vorgaben Technische Voraussetzung

Diesem Projekt liegt die Aufgabenstellung voraus, eine interaktive App zum Themenbereich der Astronomie, zu erstellen. Umgesetzt werden sollte die App mit dem Svelte Framework. Die App spiegelt die über das Semester gelernten Inhalte wieder.

---

## API

Unteranderem Pflicht für die Anwendung ist es, eine API zu verwenden. 
Fündig geworden bin ich auf [N2YO.COM](http://N2YO.COM) mit der **N2YO.COM REST API v1**. Darin enthalten sind Daten zu Satelliten die aktuell im All unterwegs sind. Vor allem Informationen zur Position bzw. zukünftigen Positionen und zum Verwendungszweck der Satelliten. 

---

## Idee Visualisierung

Klar war also meine App soll Informationen zu Satelliten bereitstellen, als eine Art Lern- bzw. Informationsanwendung. 

Herausgekommen ist eine Visualisierung, welche Satelliten visualisiert, die sich über einem bestimmten Punkt auf der Erde befinden. Genau genommen soll es sich bei dem Punkt um den Standort des Nutzers handeln. Daher auch der Name “What’s above you?”. Vorläufig wird in der Anwendung der Standort Schwäbisch Gmünd berücksichtigt. 

Angegeben wird der Ort in Koordinaten. Zudem wird ein Radius festgelegt in welchem über dem Punkt gesucht werden soll (0° - 90°)

[https://api.n2yo.com/rest/v1/satellite/above/48/9/0/10/0/&apiKey=](https://api.n2yo.com/rest/v1/satellite/above/48/9/0/10/0/&apiKey=H5W4P7-C4NVAN-VVAXWF-59LC)

Request: /above/{observer_lat}/{observer_lng}/{observer_alt}/{search_radius}/{category_id} 

Abrufbar sind für den Nutzer der App nun informationen über den Satelliten:

Name

International Designator

ID

Launch Date

Altitude

Koordinaten (lat und lng)

Der Nutzer hat die Wahl zwischen einer Visualisierung der Satelliten, wie sie über der Erde schweben und einer Tabellen-Ansicht. Die Tabelle bietet dem Nutzer neben den genannten Informationen zudem die Möglichkeit die aktuell vorhandenen Satelliten nach ihren Eigenschaften auf- und absteigend zu sortieren und dementsprechend zu vergleichen.

---

## Code / Features

Aus Coding Perspektive verbaute Features der Anwendung und Herausforderungen meinerseits, gibt es folgende:

Die “Visualisierung” der Satelliten war wohl die komplizierteste Aufgabe. Vor allem im Bereich css. Die Anzeigehöhe der Satelliten ist auf deren Altitude Information gemappt. Dass die Satelliten alle vollständig sichtbar und nicht teilweise abgeschnitten über der Welt im Container erscheinen, gestaltete sich als Schwierigkeit.

Hovert man mit der Maus über einen der abgebildeten Satelliten, bekommt man als Nutzer einen Tooltip zu sehen, welcher die bereits genannten Informationen über die jeweiligen Satelliten beinhaltet.

Neben der Visualisierungsansicht, welche mit ihren fotorealistischen Abbildungen etwas an einen realistischen Blick aus dem All erinnern soll, lässt sich über die Navbar auf die Tabellenansicht navigieren. Das Feature Dort ist die Sortierfunktion, nach all den möglichen Kategorien.

Im Hintergrund werden die Daten, welche Satelliten sich gerade über dem Nutzer befinden, alle 10 Sekunden aktualisieret, was man als Nutzer auch zu sehen bekommt, wenn sich der Inhalt verändert.

---

## Zukünftige Features?

Um dem Namen “What’s above you?” gerecht zu werden, bietet es sich an den tatsächlichen Live Standort des Nutzers der Anwendung abzufragen und dementsprechend auch die Satelliten zu laden, welche sich aktuell wirklich über dem Nutzer befinden.

Zudem könnte man die Anwendung wunderbar als Plattform Nutzen noch mehr Informationen, mittels weiteren Datenquellen, über die Satelliten darzustellen und die Satelliten auch dementsprechend unterschiedlich visualisieren, filtern etc..

---

Moritz Nussbaumer, Hochschule für Gestaltung Schwäbisch Gmünd - Programmiersprachen 3 SoSe 24
