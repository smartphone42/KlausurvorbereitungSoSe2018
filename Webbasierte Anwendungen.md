Webbasierte Anwendungen

## Grundlagen (Vorlesung 1

### Problemfelder - Übersicht

![Problemfelder](/Ressourcen/Problemfelder.PNG)

### Standardisierung 

- 1971 -Email
- 1989 -WWW und HTTP
- 1993 -Browser
- 1994- W3C
- 2001 -Semantic Web
- 2004 -Web 2.0

### Protokolle

- TCP (Transmission Control Protocol)
- IP (Internet Protocol)
- FTP (File Transfer Protocol)
- SMTP (Simple Mail Transfer Protocol)  

#### URL

**Definition: Der URL (Uniform Resource Locator) gibt die Position einer Ressource im Internet an**

- protocol://hostname\[:port]\[/path]\[/filename][#section]
  - Protocol: Tansferprotocol (HTTPFTP,FILE etc,)
  - hostname: Name des Hosts (IP oder Hostname)
  - Port: Portnummer (HTTP Standart-Port: 80)
  - path: Pfadname zur Ressource (/illias/wba)
  - filename: Dateiname (Vorlesung1.txt)
  - section: ID eines Abschnittes im Dokument


#### MIME-Type

**Definition: Der MIME-Type (Multimedia Internet Message Extension) beschriebt den Medientyp eines Dokuments im Web**

*Haupttyp/Untertyp*

- text/plain
- text/html
- image/jpeg
- application/pdf
- etc.



#### HTTP

**Definition: Das HyperText Transfer Protocol (HTTP) ist das grundlegende Anforderungs-Antwort-Protokoll für das Web**

##### HTTP 1.1

- 1989 V.1.0 1999 V.1.1
- Zustandslos
- Unverschlüsselt
- Unterstützt HTTPS
- Nicht auf Text Nachrichten Beschränkt

##### HTTP 2.0

- 2015 V.2.0
- Zusammenfassen mehrerer Anfragen
- Bessere Datenkompression
- Übertragung binär kodierter Daten
- Server-initiierte Datenübertragung 



**HTTP legt folgendes fest:**

- Ablauf des Dokumentenabrufs
- Mögliche Arten einer Anfrage
- Inhalt einer Anfrage
- Mögliche Arten einer Antwort
- Inhalt einer Antwort

**HTTPS fügt folgendes hinzu:**

- Verschlüsselungsebene zwischen HTTP und TCP
- Verschlüsselung mit Zertifikaten (SSL/TLS)
- Authentifikation und Identifizierung der Kommunikationspartner

##### Ablauf des Dokumentenabrufes

1. Client (User oder App) aktiviert im Browser die URL
2. Browser bestimmt ggf. durch Domain Name Systems (DNS) die IP-Adresse 
3. Browser baut mit IP-Adresse eine TCP-Verbindung auf und schickt dem Webserver eine Seitenanforderung (Request)
4. WebServer schickt dem Browser die gewünschte Seite zurück (Response)
5. TCP-Verbindung wird wieder gelöst
6. Browser bringt Webseite zur Anzeige 

##### Mögliche Arten einer Anfrage


| Anfrage-Art |               Beschreibung               |
| ----------- | :--------------------------------------: |
| GET         |     Anfordern einer Datei vom Server     |
| POST        | Anfordern einer Datei vom Server. Mitsenden von Datenpaketen mögliche (z.B Formularversand) |
| HEAD        |  Anfordern des HTTP-Headers einer Datei  |
| OPTIONS     | Anfordern einer Liste von Serverseitig ünterstützten Methoden |
| PUT         |    Ablegen einer Datei auf den Server    |
| DELETE      |    Löschen einer Datei auf den Server    |
| TRACE       | liefert Anfragen zurück, so wie sie vom Server empfangen wurde (z.B fürs Debugging) |

**Inhalt einer HTTP Anfrage**

```http
ANFRAGE-ART //URL PROTOKOLL-VERSION
Accept: MIME-TYPEN; QUALITÄTSANSPRUCH
User-Agent: ANGABEN ZUM BROWSER
Accept-Language: GEWÜNSCHTE SPRACHE
```

Beispiel:

``` http
GET //http://www.fh-bielefeld.de:80/ilias/ HTTP/1.1
Accept: text/html, image/gif, image/jpeg ; q=0.9
User-Agent: Mozilla/4.0 (compatible; MSIE 10.0; Windows 10.0)
Accept-Language: en; q=0.5, de; q=0.9… 
```

##### Mögliche Arten einer Antwort
Antwort-Arten werden mittels Status-Codes verständlich gemacht

| Status-Code | Beschreibung                             |
| ----------- | ---------------------------------------- |
| 100-199     | Information während die Anfrage auf dem Server bearbeitet wird |
| 200-299     | Erfolgreiche Anfrage,Aktion              |
| 200         | OK: Daten werden gesendet                |
| 202         | Acceptet: wird später ausgeführt         |
| 300-399     | Umleiten der Anfrage, weitere Bearbeitung notwending |
| 400-499     | Anfrage unvollständig oder fehlerhaft **Abbruch** |
| 400         | Bad Request (Syntaxfehler)               |
| 401         | Unauthorized                             |
| 404         | Not Found                                |
| 405         | Methode not allowed                      |
| 500-599     | Fehler auf dem Server auftreten          |
| 500         | Internal Server Error (Fehler auf den Server aufgetreten) |
| 503         | Servuce Unavailable (Vorrübergehend nicht verfügbar) |

**Inhalt einer Antwort**

```HTTP
PROTOKOLL-VERSION STATUS-CODE
ANTWORT-DATUM
Content-Type: MIME-TYPEN
[…]
[CONTENT]
```

Beispiel:

```http
HTTP/1.1 200
Date: Mo, 18 Oct 2017 23:20:55 GMT
Content-Type: text/html
<html> … </html>
```

## Webapplikationen (Vorlesung 2)

**Definition: Eine Web-Applikation ist ein Softwaresystem, das auf Spezifikationen des World Wide Web Consortium (W3C) beruht und Webspezifische Ressourcen wie Inhalte und Dienste bereitstellt, die über eine Benutzerschnittstelle, den Web-Browser, verwendet werden**

Webanwendungen stellen anderen Anforderungen als klassische Destkopapplikationen:

- Anwederbezug
- Nutzung
- Inhalt
- Verlunkung
- Dastellung
- Software Struktur

### Charakteristika 

1. Anwederbezug
2. Nutzung
3. Inhalt
4. Verlinkung
5. Darstellung
6. Software Struktur
7. Hardware Nutzung
8. Maschinenlesbarkeit

#### Charakteristika 1 - Anwenderbezug

**Definition: Eine Web-Applikation wird von verschiedensten Anwendern mit verschiedensten Kontexten, Fähigkeiten und Vorwissen genutzt**

- Mehrbenutzer

  - Gleichzeitige Nutzung durch mehrere Benutzer
  - Nutzung durch unterschiedliche Geräte
  - Nutzung durch unterschiedliche Software

- Sozialer Kontext

  - Kaum Loyalität der Nutzer
  - Nutzungszahlen sschwer vorhersagbar

- Technische Fähigkeiten

  - Unterschiedliche Vertrautheit mit den Bendienkonzept

- Physische Fähigkeiten

  - Unterschiedliche phyische Fähigkeiten

- Vorwissen

  - Unterschieldiche Vertrautheit mit den Inhalten der Seite

- Präferenzen

  - Unterschiedliche Wünsche an Aussehen und Inhalt

#### Charakteristika 2 - Nutzung

**Definition: Web-Applikationen werden unter verschiedensten Gegebenheiten genutzt**

- Zeitlicher Kontext
  - Nutzbarkeit 24/7
  - Inhalt abhängig vom Zugriffszeitpunkt
- Örtlicher Kontext
  - Anpassung der Sprache
  - Internationalisierung der Inhalte
  - Inhalte abhängig vom Standort des Zugreifenden
- Interaktivität
  - Seitenintegrierte Suchfunktionen
  - Einstellungen auf der Seite vornehmen
  - Benutzerabhängige Inhalte
- Benutzerinteraktion
  - Verschiedene zeitgleiche Anwender können interagieren
- Personalisierte Dienste
  - Auf den Anweder zugeschnittene Inhalte


#### Charakteristika 3 - Inhalt

**Definition: Die Inhalte (Content) einer Web-Applikation sind die Basis für ihre Nutzung und kritischer Faktor für die Akzeptanz** 

- Multimedialer Charakter
  - Text, Grafiken, Animationen, Audio, Video
- Inhaltliche Genauigkeit 
  - Hohe Anforderungen an Konsistenz, Verlässlichkeit und Umfang
  - Aktualität
    - Inhalt muss aktuell und passend sein

#### Charakteristika 4 - Verlinkung

**Definition: Web-Applikationen haben Verbindungen zu anderen WebApplikationen.(Hypertext)**

- Hyptertext-Struktur

  - Aufbau einer Web-Applikation im Kontext anderer Web-Applikationen

- Nicht-lineare Nutzung

  - Stöbern, Suchen, geführtes Navigieren

- Desorientierung

  - Verlieren des Orts- und Richtungssinns und kognitive Belastung 


#### Charakteristika 5 - Darstellung 

**Definition: Die Darstellung (Presentation) einer Web-Applikation ist mit ein wichtiger Faktor bei der Benutzerakzeptanz**

- Ästhetik
  - Die Webanwendung soll ansprechend gestaltet sein
- Usabillity
  - Prinzipien der Usabillity beachten
- Aktualität
  - Die Dastellung unterliegt Modetrends

#### Charakteristika 6 - Software Struktur

**Definition: Eine Web-Applikation ist eine jederzeit verfügbare, verteilte Anwendung**

- Jederzeit Verfügbar
  - Ausfallsicherheit der Hardware und Software 
- Verteilt
  - Server und Client
- Dienstgüte
  - Übertragungseigenschaften des Web (Bandbreite, Verbidnungsabbrüche etc)

#### Charakteristika 7 - Hardware Nutzung

**Definition: Eine Web-Applikation hat einen beschränkten Zugriff auf die Hardware des Anzeigegerätes**

- Keine Hardwareverwendung
- Browser Implementiert:
  - Hardwerbeschleuniger wenn möglich
- User-Can-Allow-Policy
  - Verwendung von Hardware MUSS vom User expliziet erlaubt werden (z.B Kameras)

#### Charakteristika 8 - Maschinenlesbarkeit

**Definition: Web-Applikationen sind zunächst einmal für die Verwendung durch Menschen konzipiert, können aber auch Konzepte zur Verwendung durch Algorithmen implementieren**

- Strukturelle Auszeichnungen
  - Kenntlichmachung von Seiten-Bereichen
- Trennung von Inhalt und Design
  - Inhalt und Design werden getrennt voneinander implementiert
- Semantische Auszeichnung
  - Auszeichnung von Inhalten, damit ihre Bedeutung emittelt werden kann

### Kategorien

| Kategorie                         | Definition                               | Beispiel                                 |
| --------------------------------- | ---------------------------------------- | ---------------------------------------- |
| Dokumentenzentrierte Web-Seiten   | Eine dokumentenzentrierte Web-Seite besteht aus statischen HTML-Seiten |                                          |
| Interaktive Web-Anwendung         | Eine interaktive Web-Anwendung bietet die Möglichkeit einfache Interaktionen über Eingabebereiche auszuführen | News-Seiten, Fahrplanauskünfte           |
| Transaktionale Web-Anwendungen    | Eine transaktionale Web-Anwendung bietet die Möglichkeit schreibende Interaktionen auszuführen | OnlineBanking, E-Shopping, Reservierungssysteme |
| Workflowbasierte Web-Anwendungen  | Bei Workflowbasierte Web-Anwendungen steht die Abwicklung von Geschäftsprozessen (Workflow) im Vordergrund | Business-to-Business lösungen            |
| Kollaborative Web-Anwendungen     | Kollaborative Web-Anwendungen rücken die Teilnahme der Anwender in den Mittelpunkt. | Gruppenterminplanung, Social Media       |
| Portalorientierte Web-Anwendungen | Portalorientierte Web-Anwendungen verstehen sich als Zugriffspunkt auf verteilte, potentiell heterogene Informationsquellen und Dienste im Sinne eines Single Point of Acces | Allgemeine Portale: zentrale Anlaufseiten als Einstiegshilfe ins Netz(z.B. Microsoft, Yahoo);            spezialisierte Portale: Unternehmensportale, Marktplatzportale,Community-Portale |
| Ubiquitäre Web-Anwendungen        | Ubiquitäre Web-Anwendungen bieten uneingeschränkte Verfügbarkeit und personalisierte Dienste. | Mobile Anwendungen                       |
| Semantische Web-Anwendungen       | Semantische Web-Anwendungen bereiten ihre Inhalte so auf, dass sie auch durch Algorithmen in ihrer Bedeutung ausgewertet werden können. | globale Datenanlayse für Unwetterwarnung, Grippewellen |
| Progressive Web-Anwendungen       | Progressive Web-Anwendungen erfüllen Charakteristika, von Web-Anwendungen und nutzen Charakteristika von nativen Anwendungen. | Als Apps erscheinende Web-Anwendungen    |

### app-manifest

**Definition: Das app-manifest ist eine Konfigurationsdatei, welche geeigneten Geräten zeigt, dass es sich bei der Webanwendung um eine Webanwendung handelt, die als App genutzt werden kann.**

## HTML (Vorlesung 3)

**Definition: HTML (HyperText Markup Language) ist eine Auszeichnungssprache mit der Inhalte von Seiten strukturiert und semantisch angereichert werden können**

HTML V1.0 1992

__Auszeichnungssprache (Markup Language)__ 
- Beschreibt die Inhalte eines Dokuments
  -  Legt die Struktur der Inhalte fest (nicht das Erscheinungsbild)
  -  Kann die Semantik (Bedeutung) der Inhalte festlegen

- Implementiert keine Algorithmen 

#### HTML Struktur

##### Doctype 

Doctype:  Der HTML Doctype gibt den Dokumententyp eines HTML Dokuments an	

```html
  <!DOCTYPE html>
```

##### Seitenaufbau

  \<html> Root-Tag – Umfasst den gesamten Dokumenteninhalt<br>
  \<head> Dokumenten-Kopf – Titel, Metadaten, Includes,..<br>
  \<body> Dokumenten-Körper – Enthält die eigentlichen Inhalte

  ```html
  <html>
  	<head>
  		…
  	</head>
  	<body>
  		…
  	</body>
  </html>
  ```

###### Head

\<meta>: Gibt Meta-Informationen an<br>charset: Verwendete Zeichenkodierung auf der Seite<br>viewport: Zu verwendende Breite und Standard-Zoom (Multi-Devices)<br>Allgemein: Meta-Informationen zum Inhalt (Keywords, Beschreibung,…)<br>\<link>: Angabe wichtiger externen Ressourcen<br>\<script>: Einbettung oder Einbindung von Skripten 

```html
<head>
	<title>Titel der Web-Anwendung</title>
	<meta charset="UTF-8">
	<meta name="viewport" content="width=device-width,initial-scale=1.0">
	<meta name=“Name“ content=“Wert“>
	<link href =“Name“ rel=“Name“ type=“Name“>
	<script>…</script>
</head>
```

##### Strukturelle Tags

| Tag        | Beschreibung                             |
| ---------- | ---------------------------------------- |
| \<header>  | definiert den Kopfbereich einer Seite oder eines Abschnitts |
| \<footer>  | definiert die Fußzeile einer Seite oder eines Abschnitts |
| \<nav>     | definiert einen Navigationsbereich einer Seite oder eines Abschnitts |
| \<section> | definiert einen logischen Abschnitt einer Seite oder einer Gruppe von Inhalten |
| \<article> | definiert einen Artikel oder ein in sich abgeschlossenes Inhaltselement |
| \<aside>   | definiert sekundäre oder ähnliche Inhalte |
| \<p>       | definiert einen Absatz (zusammengehörigen Text) |
| \<br>      | erzeugt einen Zeilenumbruch              |

![Strukturelle Tags](/Ressourcen/Strukturelle Tags.PNG)



##### Hyperlinks

```html
Seiten Link: Verweis auf ein Element der selben Seite mit einer ID
<a href=“#ziel“>Seiten Link</a>
<p id=“ziel“>Interner Absatz mit Ziel</p>

Links in der selben Anwendung
<a href=“\unterseite“>Link in der selben Anwendung</a>

Externe Links
<a href=“https:\\www.seite.de“>Externer Link</a>

```

##### Tabellen

\<table>: Die enthaltenen Elemente stellen eine gemeinsame Tabelle dar<br>\<tr>: Umfasst alle Elemente einer Tabellen-Zeile<br>\<th>: Eine Zelle einer Kopfzeile<br>\<td>: Eine Zelle einer Tabellen-Spalte

```html
<table>
	<tr>
		<th colspan="2"> Kopfzeile</th>
	</tr>
	<tr><td>Zelle links</td><td> Zelle rechts</td></tr>
</table>
```

![TabelleExample](/Ressourcen/TabelleExample.PNG)

##### Listen

\<ul>: Eine Liste ungeordneter Elemente<br>\<ol>: Eine Liste geordneter (nummerierter) Elemente<br>\<li>: Ein Listeneintrag für un-, geordnete Listen<br>\<dl>: Eine Liste für Definitionen <br>\<dt>: Term-Eintrag in einer Definitionsliste<br>\<dd>: Erläuterungs-Eintrag in einer Definitionsliste


```html
<ul><li>Ein ungeordneter Eintrag</li></ul>
<ol><li>Ein geordneter Eintrag</li></ol>
<dl>
	<dt>Term</dt>
	<dd>Definition</dd>
</dl>
```

#### HTML Formulare

**Definition: HTML Formulare dienen der Eingabe von Daten durch Benutzer. Sie Werden durch den Browser an eine angegebene Adresse versendet und müssen vom Empfänger verarbeitet werden.**

\<form>: Umschließt alle Elemente eines Formulars und legt Attribute fest

**Attribute:**

action: URL an welche die Daten aus dem Formular gesendet werden<br>method: bestimmt die HTTP-Methode die zum Versand genutzt wird<br>enctype: bestimmt den Mime-Type in dem Versendet wird

```html
<form action=“URL“ method=“POST|GET“ enctype=“TRANSFERFORMAT“>
…
</form>
```

##### Methoden

- **GET**
  - Formulardaten werden als Parameterstring an die URL angehängt
  - Passwörter im Klartext
  - Hyperlink auf Formularparameter möglich
  - Daten als Favorit möglich
  - Längenbegrenzung (ca. 3000 Zeichen)
- **POST**
  - Formulardaten werden im Body des HTTP-Requests codiert
  - unbegrenzte Datenmenge
  - Daten als Favoriten speichern nicht möglich

##### Eingabeelemente

 \<input> Eingabeelement mit unterschiedlicher Darstellung nach Typ:


| Type        | Beschreibung                             | Beispiel                                 |
| ----------- | ---------------------------------------- | ---------------------------------------- |
| text        | einzeiliges Eingabefeld                  | \<input type="text" name=s>              |
| password    | einzeiliges Eingabefeld mit nicht sichtbaren Zeichen | \<input type="password" name=s>          |
| number      | ein Zahlenwert                           | \<input type="number" name=s>            |
| range       | ein Zahlenwert aus einem bereich         | \<input type="range" name=s min="0" max="10"> |
| color       | Farbangaben                              | \<input type="color" name=s>             |
| email       | Eine E-Mail Adresse                      | \<input type="email" name=s>             |
| file        | Eine Datei                               | \<input type="color" name=s>             |
| tel         | Eine Telefonnummer                       | \<input type="file" name=s>              |
| url         | Eine URL                                 | \<input type="url" name=s>               |
| checkbox    | es können beliebig viele Optionen aktiviert werden | \<input type="checkbox" name="s" value="A"> <br> \<input type="checkbox" name="s" value="B"> |
| radio       | es kann nur eine einzige Option aktiviert werden | \<input type="radio" name="s" value="male"> <br> \<input type="radio" name="s" value="female"> |
| \<select>   | Drop-Down-Liste mit <option> Elementen   | \<select> \<option value="A"> A \</option> \</select> |
| \<textarea> | Ein mehrzeiliges Texteingabefeld         | \<textarea rows="4" cols="50"> ...\</textarea> |


**Browser können:** 
- Auf den Datentyp abgestimmte Eingabeelemente anzeigen
- vor dem Absenden prüfen, ob Werte für den angegebenen Typ gültig sind.

##### Button

###### Formular Buttons

\<input>: Buttons in Formularen ins Eingabeelemente mit Typ:<br>submit: Absenden des Formulars<br>reset: Zurücksetzen aller Inhalte auf den Ladezustand

```html
<form action="/action_page.php">
	First name:<br>
	<input type="text" name="firstname" value="Mickey"><br>
	Last name:<br>
	<input type="text" name="lastname" value="Mouse"><br><br>
<input type="submit" value="Submit">
</form> 
```

![formularButton](/Ressourcen/formularButton.PNG)

###### Script Button

\<button>: Buttons für die Verwendung mit Skripten

```html
<button onclick="myFunction()">Click me</button>
```

##### Gestaltung

\<label>: Beschriftung für ein Eingabeelement<br>\<fieldset>: Eingabeelemente gruppieren<br>\<legend>: Beschriftung für eine Gruppierung

```html
<fieldset>
	<legend>Personalia:</legend>
	<label for="name">Name:</label>
	<input id="name" type="text"><br>
	<label for="email">Email:</label>
	<input id="email" type="text"><br>
	<label for="birth">Date of birth:</label>
	<input id="birth" type="text">
</fieldset>
```

![gestaltungLabel](/Ressourcen/gestaltungLabel.PNG)

#### Mediadatein

##### Bilder

\<picture>: Definiert ein Bild Objekt <br>\<source>: Definiert eine Bildquelle<br>media: Gibt an, wann die Bildquelle verwendet werden soll<br>srcset: URL zum Bild<br>\<img>: Fallback-Tag für alte Browser<br>alt: Alternativtext; angezeigt, wenn das Bild nicht verfügbar ist

````html
<picture>
	<source media="(min-width: 650px)" srcset="a.jpg">
	<source media="(min-width: 465px)" srcset="b.jpg">
	<img src="c.jpg" alt="Letters">
</picture>
````

##### Audio


\<audio>: Definiert ein Audio-Objekt <br>\<source>: Definiert eine Audioquelle <br>src: URL zur Audiodatei <br>type: Typ der Audiodatei

```html
<audio controls>
	<source src=„sound.ogg" type="audio/ogg">
	<source src=„sound.mp3" type="audio/mpeg">
	Your browser does not support the audio element.
</audio> 	
```

- Der Browser verwendet die erste Quelle aus der Liste, die er versteht
- Kontrollelemente und Autostart können definiert werden
- Kein Plugin notwendig

##### Video

\<video>: Definiert ein Video-Object<br>\<source>: Definiert eine Videoquelle<br>src: URL zur Videodatei<br>type: Typ der Datei

```html
<video width="320" height="240" controls>
	<source src="movie.mp4" type="video/mp4">
	<source src="movie.ogg" type="video/ogg">
	Your browser does not support the video tag.
</video>
```

- Der Browser verwendet die erste Quelle aus der Liste, die er versteht
- Kontrollelemente und Autostart können definiert werden
- Kein Plugin notwendig


## CSS (Vorlesung 4)

**Definition: CSS (Cascading Style Sheets) ist die Standard Stylesheetsprache für Webseiten. CSS formatieren und positionieren HTML-Elemente**

**Stylesheetsorache:**

- Beschreibt das Aussehen eines Dokumentes
  - Kann dynamisch geändert werden
- Dient nicht der Implementierung von Algorithmen

**CSS:**

- Definiert Selektoren mit denen HTML-Elemente erfasst werden können
- Legt mögliche Style-Attribute fest
- Legt die möglichen Werte für Style-Attrubute fest
- Legt die Interpretation von Positionierungsangaben fest
- Beschriebt wie die Style-Angaben vom Browser zu interpretieren sind

**Browser:**

1. Interpretieren Style-Anweisungen
2. Suchen die zu stylenden Elemente über Selektoren
3. Wenden die Style-Anweisungen an

### Rule-Set

**Definition: Ein CSS Rule-Set ist ein formeller Regelsatz, der das Aussehen unter festgelegten Bedingungen eines bestimmten HTML Elements festlegt.**

Selector: Wählt die Elemente aus, deren Eigenschaften gesetzt werden sollen <br>Property: Ist eine stylebare Eigenschaft eines Elements (hängt vom Element ab) <br>Value: Ist ein Wert, den die Eigenschaft annehmen kann

```css
Selector { Property: Value; Property: Value}
```

### Einbinden

**External:** Aus einer anderen Datei, link im Header

```html
<link rel=“stylesheet“ type=“text/css“ href=“datei.css“>
```

**Internal:** In einen style-Tag im Header

```html
<style>…</style>
```

**Inline:** In einen style-Attrbut bei einem Element

```html
<p style=“…“>…</p>
```

### Kaskadierung

**Definition: Kaskadierung (Cascading) bezeichnet die Eigenschaft von CSS, dass mehrere Stylesheets zu einem gemeinsamen Stylesheet zusammengefasst werden**

**Kaskadierungs-Reihenfolge:**

1. Browser
2. Extern und Intern (in Deklarations Reihenfolge)
3. Inline

### Style Stack

**Die Festlegung eines Style-Stack legt den Aufbau und die Verteilung der Style-Anweisungen fest und sollte in der Planungs-Phase einer Webanwendung erfolgen.**

**Beispiel Style-Stack**

1. Extern (global): Für die gesamte Anwendung
2. Extern (area): Für Elemente die nicht überall, aber auf mehreren Seiten zu finden sind
3. Intern: Für Elemente die nur auf einer Seite vorkommen
4. Inline: Falls ein Element ein spezielles Aussehen benötigt

*Allgemeine Regel: Je tiefer im Stack, desto weniger soll dort geregelt sein*

### Selektoren

| Selektor | Beschreibung                             |
| -------- | ---------------------------------------- |
| .class   | Alle Elemente die diese Klasse haben (HTML Attribut class=" ") |
| \#id     | Das Element mit der ID (HTML Attribut id=" ") |
| *        | Alle Elemente                            |
| element  | Das Element mit den angegebenen Namen (z.B h1) |

| Attributs-Selektor | Beschreibung                             |
| ------------------ | ---------------------------------------- |
| [attribute]        | Alle Elemente die ein Attribut mit diesen Namen haben |
| [attribute=wert]   | Alle Elemente die ein Attribut mit diesen Namen und Wert hat |

#### Pseudo Klassen

**Sind Klassen, die ein Element durch den Browser aufgrund seiner Position im Dokument, seines Verhältnisses zum Benutzer oder dergleichen hat.**

| Pseudo Klasse | Beschreibung                             |
| ------------- | ---------------------------------------- |
| :hover        | Alle Elemente, über die der Benutzer gerade seine Maus hat |
| :focus        | Wenn ein Eingabeelement den Fokus hat    |
| :link         | Alle noch nicht besuchten Links          |
| :first-child  | Das erste Kind-Element (eines davor angegebenen Elements) |

#### Pseudo Elemente

**Sind Elemente die implizit existieren**

| Pseudo Element | Beschreibung                     |
| -------------- | -------------------------------- |
| ::first-line   | Die erste Zeile eines Textes     |
| ::first-letter | Der erste Buchstabe eines Textes |
| ::before       | Der Bereich vor einem Element    |

#### Kombination

Selektoren sind auch Kombinierbar*

**Kommbinations Operatoren:** <br>Kommata: Wählt Selector 1 oder Selector 2 <br>Leerzeichen: Alle Elemente von selector 2 und selector 1

Beispiel:
```css
section article {
color: blue;
}
section, article {
color: red;
}
```

ACHTUNG! Speziellere Regeln haben immer Vorrang vor allgemeineren!

### Eigenschaften

| Eigenschaft         | Beschreibung                             |
| ------------------- | ---------------------------------------- |
| color               | Schriftfarbe                             |
| background-color    | Hintergrundfarbe                         |
| font                | Schriftart                               |
| text-shadow         | Schattenwurf für Text                    |
| text-overflow       | Verhalten bei überlangen Texten          |
| list-style-type     | Typ des Zeichens in Listen               |
| border-collapse     | Zusammenlegen der Ränder einer Tabellenspalte |
| text-align          | Ausrichtung des Texts                    |
| background-image    | Hintergrundbild                          |
| background-repeat   | Wiederholung von Hintergrundbildern      |
| background-position | Positionierung von Hintergründen         |
| border-style        | Typ eines Rahmens (z.B. gepunktet, gestrichelt,…) |
| border-color        | Farbe eines Rahmens                      |
| border-radius       | Abrundung von Rahmen                     |
| border              | Kombinierte Angaben zu Typ, Farbe, Dicke,… |

### Layout

#### Boxmodel

**HTML-Auszeichnungen, die einen Block oder Absatz bilden werden in eine Box eingebettet. Die Box wird umgeben von einer Polsterung (padding), dem Rahmen (border) und dem Rand (margin). Die Gesamtausmaße der Box ergeben sich immer aus einer Addition dieser Größen.**

![boxmodel](/Ressourcen/boxmodel.PNG)

Beispiel:

```css
body {
	border: 1px dotted;
}
section article {
	height: 50px;
	padding: 5px;
	border: 1px solid red;
	margin: 20px;
}
```

#### Darstellung

**Definition: Die Display-Eigenschaft stellt die Art der Darstellung ein.**

| display    | Beschreibung                             |
| ---------- | ---------------------------------------- |
| none       | Das Element wird so dargestellt, als sei es nicht existent |
| inline     | Kein Zeilenumbruch vor und hinter dem Element |
| block      | Das Element wird wie ein Block-Element dargestellt |
| table      | Zweidimensionale Tabellen-ähnliche Designs |
| positioned | Fix positionierte Elemente               |
| flex       | Flexible Positionierung, gleichmäßige Aufteilung, Stacking |

| visibillity | Beschreibung                             |
| ----------- | ---------------------------------------- |
| hidden      | Das Element wird nicht dargestellt, aber der Platz bleibt reserviert |

Beispiel: 

```css
article {
	display: none;
}
section article {
	display: inline;
}
section article p {
	display: inline;
}

```


| position     | Beschreibung                             |
| ------------ | ---------------------------------------- |
| static       | Normale Platzierung innerhalb des Seiteninhalts |
| relative     | Positionsangaben gelten relativ zur normalen Platzierung |
| absolute     | Positionierung absolut zum umgebenden Element |
| fixed        | Absolut positioniert und bleibt beim Scrollen |
| sticky       | Abhängig von scroll-Position. Bleibt sichtbar hängen |
| top, bottom: | Abstand vom oberen oder unteren Rand     |
| left, right: | Abstand vom linken oder rechten Rand     |

Beispiel:

```css
#art1 {
	position: absolute;
	top: 0px;
	left: 0px;
}
#art2 {
	position: relative;
	top: 0px;
	left: 0px;
}
#art3 {		
	position: fixed;
	bottom: 0;
	right: 0;
}
```

### Animation

#### Transistions

**CSS Transitions erlauben es Änderungen an CSS-Eigenschaften animiert auszuführen, indem die Werte schrittweise geändert werden.**

*transition: \[eigenschaft]\[dauer]* <br>\[eigenschaft]: Name der Eigenschaft, die Übergeleitert werden soll <br>\[dauer]: Zeit in Sekunden, die den Effekt in Anspruch nehmen soll

Beispiel: 

```css
a {
	font-size: 12pt;
	border-width: 1px;
	color: black;
}
a:hover {
	font-size: 30pt;
	color: red;
	transition: font-size 2s, color 5s;
}
```



#### Transform

**CSS Transform erlauben es Elemente in ihrer Ausrichtung zu transformieren. Es gibt 2D und 3D Transformationen**

*transform: [transformfunction]* 

| transformfunction | Beschreibung                             |
| ----------------- | ---------------------------------------- |
| translate()       | An der x und y Achse verschieben         |
| scale()           | Skalierung des Elements                  |
| rotate()          | Rotation                                 |
| skew()            | Scherung                                 |
| matrix()          | Freie Transformation anhand einer Matrix |

Beispiel:

```css
div {
	width: 100px;
	height: 100px;
	background-color: blue;
}
div:hover {
	transform: rotate(20deg)
}
```

#### Animations

**CSS Animations erlauben das Definieren eines komplexeren Verlaufes von Werteänderungen zum Erzeugen einer Animation.**

\@keyframes: Schlüsselbegriff zur Definition einer Animation <br> from: Startwerte der Eigenschaft(en) <br>to: Endwerte der Eigenschaft(en) <br>animation-name: Name der Animation, wie bei @keyframes angegeben <br>animation-duration: Dauer der Animation<br>x%: Eingeschaften zum Zeitpunkt x% der Animation

Beispiel: 

```css
div {
	width: 100px;
	height: 100px;
	position: relative;
	background-color: red;
	animation-name: example;
	animation-duration: 4s;
}
@keyframes example {
	0% {background-color:red; left:0px; top:0px;}
	25% {background-color:yellow; left:200px; top:0px;}
	50% {background-color:blue; left:200px; top:200px;}
	75% {background-color:green; left:0px; top:200px;}
	100% {background-color:red; left:0px; top:0px;}
}
```

## Javascript (Vorlesung 5)

**Definition: JavaScript ist eine höhere, dynamisch-typisierte, und prototypbasierte Skriptsprache. Sie unterstützt multi-paradigmen- und modulare Implementierung.**

**Skriptsprache:**

- Automatische Speicherverwaltung
- Mächtige Datenstrukturen

**Höhere Sprache:**

- Spracheelemente höherer Ebene wie Schleifen
- Umfangreiche integrierte Bibliotheken

**Dynamisch-Typisiert:**

- Variablen haben keinen festgelegten Datentyp, können zur Laufzeit unterschiedliche Inhalte annehmen

**Prototyp-basiert:**

- Zur Laufzeit erstellte Objekte können als Schablone für neue Objekte dienen

**Multi-Paradigmen:**

- javaScripte können prozedural, funktional oder objektorientiert sein

**Modulare Implementierung:**

- Skripte können in andere Skripte eingebunden werden

**Anwendungsgebiete:**

- Client-seitige Anwendungen: hauptsächlich im Webumfeld
- Server-seitige Anwendungen: node.js

### ECMAScript

**Definition: ECMAScript ist der W3C standardisierte Kern von JavaScript. Er definiert die Sprachelemente.**![ECMA](/Ressourcen/ECMA.PNG)

### Einbinden

**External:** Aus einer anderen Datei, im Header oder Body

```html
<script src=“datei.js“></script>
```

**Internal:** Im Script-Tag innerhalb Header oder Body

```html
<script>…</script>
```

**InAttribute** In einem onclick Attribut (veraltet!)

```html
<a href=“#“ onclick=“alert(‘Ausgabe‘)“>Link</a>
```

### Ausführungsreihenfolge

**Definition: JavaScripte werden ausgeführt, sobald der Browser sie vollständig geladen hat.**

**Auswirkungen:**

- Skripte können ausgeführt werden, bevor das Dokument vollständig geladen ist
- Funktionen können zu früh ausgeführt werden
- Eventuell sind bei Skriptstart nicht alle Abhängigkeiten geladen



### Prozedurale Elemente

#### Variablen

*var*: globale Variable <br>*let*: Lokale Variable <br>*const*: Konstante lokale Variable

**Eine Variable hat den Datentyp des Wertes, der ihr zugewiesen wurde. Der Datentyp kann sich zur Laufzeit ändern (dynamische Typisierung)**

#### Operatoren

![operatoren](/Ressourcen/operatoren.PNG)

#### Kontrollstrukturen

Wie in Java

- if (Bedingung)
- if (Bedingung)  else
- switch(x) { case 1:
- for (i=0;i<x;i++)
- while(Bedingung)
- do { } while(Bedingung);

#### Funktionen

**Definition: Eine Funktion kapselt Anweisungen in einen, von anderer Stelle aufrufbaren Block. JavaScript Funktionen sind referenzierbar.**

Allgemein:

```javascript
function Funktionsname(Parameter 1, Parameter 2, …) {
 // JavaScript - Anweisungen
}

```

Beispiele:

Normale Funktion:

```javascript
// Deklariere Funktion
function function1(param) {
	return param * param;
}
// Benutze Funktion
function1(2);
```

Funktion als Variable:

```javascript
// Deklariere Funktion und speichere Referenz auf Funktion in Variable
	let functionVar1 = function(param) {
	return param * param;
}
console.log(typeof functionVar1); // Ausgabe: function
// Benutze Funktion
functionVar1(2); // Ausgabe: 4
```

Funktion mit default Value:

```javascript
// Function with default value
function defaultValue(param=2) {
	return param * param;
}
console.log(defaultValue()); // Ausgabe: 4
console.log(defaultValue(4)); // Ausgabe: 16
```

Funktio mit Rest-Parameter

```javascript
function addAll(value1, ...valuesN) {
	let val = value1;
	for(var i=0; i < valuesN.length;i++) {
		val += valuesN[i];
	}
	return val;
}
console.log(addAll(1,2)); // Ausgabe: 3
console.log(addAll(1,2,3,4,5,6)); // Ausgabe: 21

```

Funktionen haben als Standart-Rückgabewert: "undefined"

### Objektorientierung

#### Objekte

**Definition: In JavaScript sind Objekte eine strukturierte Sammlung von Attributen. Attribute können beliebige Typen an Daten halten. JavaScript Objekte werden nicht (notwendigerweise) aus Klassen erzeugt.**

*Möglichkeiten von Objekten:*

- können eine Menge primitiver Attribute halten
- können eine Menge von Objekten halten
- können eine Menge von Funktionsreferenzen halten
- können als Vorlage für andere Objekte dienen (templateing)

Eigenschaften:

- Attribute sind immer public
- Zugriff auf Attribute mit this oder Objektreferenz

```javascript
// Objekt deklarieren
let obj = {
	// Objekt mit einer Eigenschaft ausstatten
	eigenschaft : 'grün',
	// Objekt mit einer Methode ausstatten
	methode : function() {
		console.log(this.eigenschaft); // Ausgabe: grün
		console.log(obj.eigenschaft); // Ausgabe: grün
	}
}
obj.methode();
```

**Definition: JavaScript Objekte können zur Laufzeit Attribute und Funktionen zugewiesen bekommen.**

```javascript
// Objekt deklarieren
let obj = new Object();
// Objekt mit einer Eigenschaft ausstatten
obj.eigenschaft = 'grün';
// Objekt mit einer Methode ausstatten
obj.methode = function() {
	console.log(this.eigenschaft); // Ausgabe: grün
	console.log(obj.eigenschaft); // Ausgabe: grün
}
obj.methode();
```

#### Klassen

**Definition: JavaScript Klassen bilden Prototyp-Objekte.**

**Eigenschaften:**

- JavaScript-Klassen sind Objekte
- Methoden werden ohne Schlüsselwort definiert
- constructor() ist die Methode, die als Konstruktor-Methode verwendet wird Attribute werden im Konstruktor deklariert
- Zugriff auf Attribute in Methoden ausschließlich mit this.
- Objekte aus Klassen sind zur Laufzeit normale Objekte mit allen Fähigkeiten
- Klassen unterstützen einfache Vererbung
- Klassen können erst nach ihrer Deklaration verwendet werden (kein hoisting)
- Eingeführt in ES6. Einfacherer Syntax als das zuvor gebräuchliche prototyping

````javascript
class Klassenname {
	constructor(parameter) { }
	methodenName(parameter) { }
}
````

Beispiel:

```javascript
class MeineKlasse {
	//Hier gibt es keine Attribut-Deklarationen
	constructor(param1) {
		// Hier kommen Attributdeklarationen
		this.attribut1 = param1;
		this.attribut2 = undefined;
	}
	methode1() {
		return this.attribut1;
	}
}
meineVar = new MeineKlasse(20);
console.log(meineVar.attribut1); // Ausgabe: 20
console.log(meineVar.methode1()); // Ausgabe: 20
meineVar.attribut3 = 42;
console.log(meineVar.attribut3); // Ausgabe: 42
```

##### getter und setter

Get und Set sind Schlüsselwörter und können etwas anders benutzt werden, als in Java. 

```javascript
// Klasse anlegen
class MeineKlasse {
	constructor(param1) {
	// Hier kommen Attributdeklarationen
	this.attribut1 = param1; // Ruft den Setter auf
	this.attribut2 = 10; // Legt das Attribut an
	}
	get attribut1() {
		console.log('get attribut1');
		return this.a1;
	}
	set attribut1(param1) {
		console.log('set attribut1');
		this.a1 = param1;
	}
}
meineVar = new MeineKlasse(20); // Ausgabe: set attribute1
console.log(meineVar.attribut1); // Ausgaben: get attribut1, 20
console.log(meineVar.attribut1()); // attribut1 is not a function
console.log(meineVar.a1); // Ausgabe: 20
console.log(meineVar.attribut2); // Ausgabe: 10
```

##### Vererbung

**Eigenschaften:**

- Einfache-Vererbung, keine Mehrfachvererbung
- Es werden alle Methoden der Elternklasse geerbt
- Attribute werden über den Eltern-Konstruktor geerbt
- Eltern-Konstruktor muss verwendet werden, sobald this in Elternklasse verwendet wurde und ein Konstruktor in der abgeleiteten Klasse genutzt wird
- Eltern-Konstruktor wird automatisch verwendet, wenn kein abgeleiteter erstellt wird.
- Methoden können Methoden der Elternklasse überdecken
- Wird ein Getter überdeckt, muss auch der Setter überdeckt werden

```javascript
// Klasse anlegen
class MeineKlasse {
	… // Wie zuvor
}
class MeineKlasse2 extends MeineKlasse {
	constructor(param1) {
	super(param1); //Zwingend
	this.attribut1 = 55;
}
	get attribut1() {
	return this.a1;
	}
	set attribut1(param1) {
	this.a1 = param1 * 2;
	}
}
meineVar = new MeineKlasse2(20);
console.log(meineVar.attribut1); // Ausgabe: 110
console.log(meineVar.attribut2); // Ausgabe: 10

```

### JSON

**Definition: JSON (JavaScriptObjectNotation) ist ein Format für den Datenaustausch zwischen Anwendungen. Es basiert auf einer JavaScript konformen Darstellung der Daten.**

**Eigenschaften:**

- JSON Dokumente können in JavaScript Objekte transformiert werden
- kann mit der JavaScript Funktion eval() interpretiert werden
- ist kompakter als XML
- Es gibt Interpreter für viele Sprachen

**Datentypen:**

- Alle JavaScript Datentypen, aber keine Referenzen und undefined

**Unterschiede in der Notation:**

- Namen von Eigenschaften in doppelte Anführungszeichen
- Strings immer in doppelte Anführungszeichen
- Keine führenden Nullen

Beispiel: 

JSON-File: 

````JSON
{
	"attribut1" : 42,
	"array1" : ["w1","w2","w3","w4"],
	"object1" : {"at1" : 1,"at2" : 2}
}
````

JSON->Object

```javascript
let jsonStr="{\"attribut1\":42, \"array1\":[\"w1\",\"w2\",\"w3\",\"w4\"]}";
jsonObj = JSON.parse(jsonStr);
for(var attr in jsonObj) {
	console.log(attr);
	if(typeof jsonObj[attr] == "object") {
		for(var i in jsonObj[attr]) {
			console.log("> " + jsonObj[attr][i]);
		}
	}
}
Ausgabe:
attribut1
array1
> w1
> w2
> w3
> w4
```

Object->JSON

````javascript
let obj = {
	attr1 : 42,
	array1 : [1,2,3,4],
	object1 : {sub1 : "sub1", sub2 : "sub2"}
}
let newJsonStr = JSON.stringify(obj);
console.log(newJsonStr);
Ausgabe:
{"attr1":42,"array1":[1,2,3,4],"object1":{"sub1":"sub1","sub2":"sub2"}}

````

### (a)synchrone Funktionen

**Definition: Synchron ausgeführte Funktionen, werden strikt in der Reihenfolge ihres Aufrufs ausgeführt. Asynchrone Funktionen lassen die Ausführung anderer Funktionen während ihrer eigene Ausführung zu.**

**Wichtige Eigenschaften von JavaScript zu Synchronizität:**

- JavaScript wird üblicherweise als single-thread ausgeführt
- Asynchron != Nebenläufig (Javascript-Asynchron ~ Queue)
- Viele eingebaute Funktionen arbeiten asynchron

**Synchron:**

- Funktionen werden nacheinander ausgeführt
- Ergebnis ist bei Rückkehr aus der Funktion bekannt

**Asynchron:**

- Funktionen werden nebeneinander ausgeführt
- Ergebnis ist bei Rückkehr aus der Funktion wahrscheinlich nicht bekannt

| Vorteile                                 | Nachteile                                |
| ---------------------------------------- | ---------------------------------------- |
| Vermeiden eventuell langer Wartezeiten (laden von Ressourcen) | Programmablauf ist schwerer nachzuvollziehen |
| Effizientes abarbeiten der Funktionen    | Programmablauf ist nicht immer gleich    |
| Bessere UserExperience, kein „einfrieren“ der Seite | Unübersichtlicherer Programmcode         |
| Ergebnisse werden geliefert, sobald sie verfügbar sind | Wie könne asynchrone Funktionen Ergebnisse liefern? |
| Zeitgesteuerte Funktionsaufrufe sind nur asynchron möglich | Gleichzeitiger Zugriff auf gemeinsame Ressourcen problematisch |

##### Callbacks

**Definition: Der Callback-Mechanismus für asynchrone Funktionen besteht darin, der asynchron ausgeführten Funktion eine CallbackMethode als Parameter mitzugeben, diese wird durch die asynchrone Funktion aufgerufen.**

```javascript
function asyncFunc(callbackFunc);
callbackFunc = function(result) { … };
```

Beispiel:

````javascript
function printAtTime() {
	console.log("Time is over!");
}
setTimeout(printAtTime,100);
for(var i=0; i < 10000; i++) {
	console.log("I'am dooing hard work");
}
````

##### Promises

**Definition: Der Prommise-Mechanismus für asynchrone Funktionen liefert ein Promise-Objekt als sofortige Antwort, welches nach Beendigung eine Funktion aufruft**

**Eigenschaften:** 

- Promise-Objekt kennt Ausführungsstatus
- Executor-Funktion wird sofort ausgeführt
- Executor-Funktion ruft eine asynchrone Funktion auf
- Asynchrone Funktion ruft resolve oder reject-Funktion auf
- Resolve-Funktion wird mit then() registriert (1 Parameter)
- Reject-Funktion wird mit then() registriert (2 Parameter)
- Werden Funktionen erst registriert, nachdem die asynchrone Funktion fertig ist, werden sie direkt ausgeführt.

![promises](/Ressourcen/promises.PNG)

Beispiel:

```javascript
var promise = new Promise(
	function(resolve,reject){
		setTimeout(function() {
			console.log("I do something that needs time...");
			resolve("done!");
		},2000);
	}
);
promise.then(function(erg) { console.log(erg)});
console.log("This should be printed before done!");
```

### Browser-Objekte

**JavaScript nimmt die Browserumgebung über Objekte war und tritt über diese Objekte in Wechselwirkung mit seiner Umgebung**

**Browser-Objekte:**

- beschreiben Eigenschaften und Funktionalitäten
- sind hierarchisch angeordnet
- sind nicht durchgehend standardisiert (aber weit verbreitet)

![browserObjekte](/Ressourcen/browserObjekte.PNG)

**Eine Auswahl der meiner Meinung nach wichtigsten Browser-Objekte** 

##### window

![window01](/Ressourcen/window01.PNG)

![window02](/Ressourcen/window02.PNG)

##### location

![location](/Ressourcen/location.PNG)



##### navigator

![navigator](/Ressourcen/navigator.PNG)



##### document

![document](/Ressourcen/document.PNG)

#### Browser API localStorage/WebStorage

**Definition: WebStorage bezeichnet zwei standardisierte Schnittstellen für clientseitigen assoziativen Speicher**

**Eigenschaften:**

- Speichern von umfangreicheren Datenmengen im Browser (mind. 5MB)
- Vom W3C standardisiert in den meisten aktuellen Browsern implementiert
- Zugriff per JavaScript
- Speicherung von Key-Value Paaren
- Key und Value sind Strings
- Tipp: Umfangreichere Werte als JSON speichern
- PerOrigin (für jede Weburl und das dabei verwendete Protokoll)
- Zwei Schnittstellen: localStorage und sessionStorage
  - APIs der Schnittstellen identisch
  - localStorage: Daten bleiben Dauerhaft erhalten, über BrowserNeustarts hinweg
  - sessionStorage: Daten werden beim Schließen des Tabs gelöscht

**Methoden:**

```javascript
localStorage.setItem(KEY,VALUE); //Fügt ein neues Key-Value-Paar in den Speicher ein
localStorage.getItem(KEY); //Holt den Wert zum angegebenen Key aus dem Speicher
localStorage.removeItem(KEY); //Löscht den Wert zum angegebenen Key aus dem Speicher
localStorage.clear(); //Löscht den gesamten Speicher
```

Beispiel:

```javascript
// Test if Storage is supported
if (typeof(Storage) !== "undefined") {
	let visits = localStorage.getItem("visits");
	if(visits) { // Test if visits is not undefined
		visitsNo = parseInt(visits); // parse because storage is string only
		visitsNo++;
		localStorage.setItem("visits",visitsNo);
      
		if(visitsNo>5) {
			localStorage.removeItem("visits");
		}
	} 
  	else {
		localStorage.setItem("visits",1);
	}
	console.log("This is your " + localStorage.getItem("visits") + " visit");
} 
else {
	console.log("Sorry! No Web Storage support..");
}
```

### Webworker

**Definition: Die WebWorker API ermöglicht es JavaScripte im Hintergrund auszuführen, selbst dann, wenn eine Webapplikation nicht angezeigt wird.**

**Eigenschaften:**

- Skripte können im Hintergrund ausgeführt werden (Nebenläufige Ausführung)
- Zwei Varianten: Dedicated Workers und Shared Workers
- WebWorker Skripte haben eingeschränkten Zugriff auf Objekte außerhalb
- Nur Zugriff auf: navigator-Objekt, location-Objekt (lesend), Anwendungscache
- Ausführung komplexer Berechnungen ohne die Seite zu beeinflussen
- Datenaustausch zwischen Seite und Worker über Methoden
- Datenaustausch immer mit Datenkopie
- Standardisiert vom W3C
- PerOrigin-Policy WebWorker werden nur von der gleichen Adresse ausgeführt
- Keine generelle Ausführung von WebWorkern aus dem fileSystem

### Service Worker

**Definition: Die Service Worker API ermöglicht es JavaScripte zu schreiben, die eine offline-Funktionalität der Webanwendung sicherstellen.**

**Eigenschaften:**

- Ermöglicht WebAnwendungen eine bessere offline-Funktionalität
- Basiert auf WebWorkern
- Kein Zugriff auf Seiten-Elemente
- Funktionieren ähnlich wie Proxy-Server
- Ermöglichen das explizite cachen von Inhalten
- Ermöglichen es Netzwerkanfragen zu modifizieren
- Service Worker funktionieren nur in https-Umgebungen
- PerOrigin-Policy WebWorker werden nur von der gleichen Adresse ausgeführt
- Laufen im Hintergrund, auch wenn die Seite nicht angezeigt wird

Basieren auf zwei Datein. 

1. Die serviceworker.js: Prüft ob der Browser ServiceWorker unterstützt und ruft dann die seriveworker-worker.js auf. 

   ```javascript
   if(navigator.serviceWorker) {
   	let serviceworker = navigator.serviceWorker.register('/pwa/serviceworkerworker.js');
   	let succsessfullRegisterFunc = function(reg) {
   	console.log("Erfolgreich registriert");
   }
   let errorRegisterFunc = function(err) {
   	console.log("Fehler beim Registrieren: " + err);
   }
   serviceworker.then(succsessfullRegisterFunc,errorRegisterFunc);
   } else {
   	console.log("No ServiceWorker support");
   }

   ```

   ​

2. Der serviceworker-worker.js. Hat eine load Methode die bei der initlalisierung aufgerufen wird und alle angegeben Datein in den Chace lädt.

   ```javascript
   // Called on install stage
   this.addEventListener('install', function(event) {
   	// Sicherstellen, das zuerst alle Datein im cache landen
   	event.waitUntil(
   		caches.open('v1').then(function(cache) {
   			return cache.addAll([
   				'/pwa/', // Root muss mit gelistet sein
   				'//ALLES WAS GESPEICHERT WERDEN SOLL.js/html/css etc.
   			]);
   		})
   	);
   });
   ```

   Und einer fetch Methode. die angeforderte Elemente zurückliefert: 

   ```javascript
   // Wird aufgerufen wenn Dateien angefragt werden
   this.addEventListener('fetch', function(evt) {
   	console.log("Hole " + evt.request.url);
   	evt.respondWith( // Responde with erwartet eine asynchrone Funktion
   	caches.match(evt.request).then(
   	function(res) { // res ist Ergebnis von caches.match()
   		console.log("Resource >" + res.url + "< aus dem Cache geholt");
   		return res;
   		}).catch(function(err) {
   	console.log("Resource >" + evt.request.url + "< nicht im Cache gefunden"); 
         //return fetch(evt.request);
   		})
   	);
   });	
   ```

   Der Browser verwaltet den ServiceWorker nach Initlalisierung selber, die fetch Methode muss also NICHT expliziet genutzt werden.  

   **Die Serviceworker-worker.js MUSS sich root-Verzeichnis befinden**

   ​


## DOM (Vorlesung 6)

**Definition: Das Document Object Model (DOM) ist standardisiertes Fundament moderner Webanwendungen**

**Eigenschaften:**

- zum großen Teil in aktuellen Browsern gleich interpretiert
- plattform- und sprachunabhängig
- Schnittstelle für den Zugriff auf XML- und HTML-Dokumente
- dynamischer Zugriff: Bearbeitung und Löschen von einzelnen Dokumentelementen (Inhalt, Struktur, Layout)

**Das Document Object Model (DOM) wird in JavaScript Objekte abgebildet.**

*Zu beachten:*

- Das DOM wird schrittweise geladen, Skripte im Head werden beim Laden ausgeführt, noch bevor der Rest vom DOM geladen ist
- Nur Skripte im selben Scope wie das Dokument haben Zugriff auf das DOM. (Kein Zugriff auf DOM aus WebWorkern / ServiceWorkern)

```javascript
// Funktion die nach dem vollständigen Laden des DOM ausgeführt wird
window.onload = function() {
// Hier ist der Zugriff auf DOM Elemente sicher möglich
}
```

### Baumstrutkur

**Eine vollständig übertragene Webseite repräsentiert einen hierarchisch geordneten Dokumentenbaum, in dem jedes HTMLElement einen Knoten bildet.**

![tree](/Ressourcen/tree.PNG)

#### Knoten

**Definition: DOM Knoten besitzen Eigenschaften und Methoden, abhängig von ihrem Knotentyp. Sie sind Objekte und über JavaScript zugreifbar.**

*Eigenschaften*:

- können Verweise auf (Kind)-Knoten sein (auch Arrays davon)
- können Eigenschaftswerte halten (z.B. Namen eines Knoten)
- können Skript-Definiert sein

```javascript
Knoten.eingeschaft
```

*Methoden*:

- sind mächtige Werkzeuge bei der Bearbeitung einer Seite
- Erlauben das dynamische löschen, verändern oder einstellen von Knoten
- können nützliche Informationen für die Webanwendung liefern

```
Knoten.methode()
```



**DOM definiert 7 Typen von Knoten**



| nodeType | Konstanten     | Beschreibung |
| -------- | -------------- | ------------ |
| 1        | ELEMENT_NODE   | Element      |
| 2        | ATTRIBUTE_NODE | Attribut     |
| 3        | TEXT_NODE      | Text         |
| 8        | COMMENT_NODE   | Kommentar    |
| 9        | DOCUMENT_NODE  | Dokument     |

Der Knotentyp kann über die Eigenschaft nodeType abgefragt werden.

```javascript
if (Knoten.nodeType == 8) alert(„Ich bin ein Kommentar“);
```

![elementNode](/Ressourcen/elementNode.PNG)

![attNode](/Ressourcen/attNode.PNG)

### DOM Zugriff

HTML für die Beispiele:

```html
<body>
	<article id=“art1“>
		Dies ist mein erster Artikel
	</article>
	<section>
	In diesem Bereich stehen die News
		<article id=“art2“ origin="mensa">
			<p>Essen 2.0 in der Mensa!</p>
		</article>
	</section>
</body>
```



#### QuerySlector

ein Element anhand eines CSS-Selectors

```javascript
let allarts = document.querySelectorAll("article");
	for(var art of allarts) {
	console.log(art.innerHTML);
	}
console.log(document.querySelector("article[origin=mensa]").innerHTML);
```

#### getElementByID

ein Element anhand einer CSS-ID

```javascript
console.log(document.getElementById("art1").innerHTML);
```

### DOM Manipulation

![manNode](/Ressourcen/manNode.PNG)

Beispiele:

appendChild

````javascript
let firstArt = document.querySelector("article");
document.getElementById("art2").appendChild(firstArt);
````

cloneNode

```javascript
let cloneArt = document.getElementById("art1").cloneNode(true);
document.querySelector("section").appendChild(cloneArt);
```

removeChild

```javascript
let toDelete = document.getElementById("art1");
toDelete.parentNode.removeChild(toDelete);
```

replaceChild

```javascript
let original = document.getElementById("art1");
let forReplace = original.cloneNode();
forReplace.innerHTML = "Ich bin der Ersatz";
original.parentNode.replaceChild(forReplace,original);
```



![manAtt](/Ressourcen/manAtt.PNG)

Beispiel:

```javascript
let artNodes = document.querySelectorAll("article");
console.log(artNodes[0].getAttributeNode("id"));
artNodes[0].setAttribute("origin","general");
console.log(artNodes[1].hasAttribute("origin"));
artNodes[1].removeAttribute("origin");
console.log(artNodes[1].hasAttribute("origin"));
```

#### Knoten erzeugen

 Beispiel: 

createElement(): erzeugt einen neuen html-Elementknoten <br>createTextNode(): erzeugt einen neune Textknoten

````javascript
let myNewArticle = document.createElement("article");
myNewArticle.setAttribute("origin","newscenter");
let myNewText = document.createTextNode("Dies ist ein neuer Artikel");
myNewArticle.appendChild(myNewText);
let firstArticle = document.querySelector("section article");
firstArticle.parentNode.insertBefore(myNewArticle,firstArticle);
````

### Event-Handling

**Definition: Das Event-Handling im DOM erlaubt das registrieren von Listenern auf bestimmte Ereignisse. Diese Listener sind JavaScriptFunktionen.**

**Eigenschaften:**

- ermöglichen das Abfangen von Ereignissen (Klick, mouseover,…)
- ermöglichen das Auswerten von Mausbewegungen
- ermöglichen somit client-seitige Validierung von Eingaben
- es gibt zahlreiche Events und dazugehörige Event-Objekte
- es können eigene Events definiert werden

Das Event Handling läuft in zwei Phasen ab, der capture Phase und der Bubble Phase. 

**Ablauf**

1. Ein Event wird ausgelöst
2. Capture-Phase beginnt
   1. Jedes Element in der Hierarchie hat die Möglichkeit das Event
     abzufangen
3. Deepest-Point
   1. Das unterste Element in der Hierarchie kann auf das Ereignis
     reagieren
4. Bubble-Phase
   1. Jedes Element in der Hierarchie hat die Möglichkeit zusätzliche
     Aktionen zu starten

#### Implementierung

type: Name des Event-Typs, der behandelt werden soll <br>
listener: Funktion, die beim Eintritt ausgeführt werden soll<br>
capture: boolean, ob der Handler in der Capture-Phase (true) oder in der Bubble-Phase (false) ausgeführt werden soll<br>removeEventHandler: Entfernt einen EventHandler wieder

```javascript
node.addEventListener(type,listener,capture)
node.removeEventListener(type,listener,capture)
```

Die aufgerufene Event-Handler-Funktion bekommt automatisch ein EventObjekt. Je nach aufgetretenem Event hat dieses Event-Objekt unterschiedliche Attribute.

Allgemeine Eigenschaften:

- type: Name des Event-Typs, der aufgetreten ist
- target: Referenz auf das (unterste) Objekt, welches geklickt wurde
- currentTarget: Referenz auf das Objekt, das gerade das Ereignis fing
- eventPhase: Gibt an, in welcher Phase sich das Event befindet timestamp Genauer Zeitpunkt zu dem das Ereignis auftrat

Allgemeine Methoden:

- preventDefault(): Die Standardaktion (des Browsers) für das Ereignis wird nicht ausgeführt
- stopPropagation(): Der Durchlauf durch die Phasen wird abgebrochen

Beispiel:

HTML:

```html
<section>
	In diesem Bereich stehen die News
<article origin="mensa">
	<p>Essen 2.0 in der Mensa!</p>
</article>
</section>
```

JSS:

```javascript
let capture = function(evt) {
	console.log('captured on ' + evt.currentTarget.nodeName);
}
let bubble = function(evt) {
	console.log("bubble on " + evt.currentTarget.nodeName);
}
window.onload = function() {
	document.querySelector("section").addEventListener("click",capture,true);
	document.querySelector("section article").addEventListener("click",capture,true);
	document.querySelector("section article p").addEventListener("click",capture,true);
	document.querySelector("section").addEventListener("click„,bubble,false);
	document.querySelector("section article").addEventListener("click",bubble,false);
	document.querySelector("section article p").addEventListener("click",bubble,false);
}

```

#### Ereignisse

![ehe](/Ressourcen/ehe.PNG)

![ehe1](/Ressourcen/ehe1.PNG)

##### Beispiel submit

````html
Dein Kommentar:
<form id="f" action="">
	<input type="Text" name="Feld"> <br> <br>
	<input type="submit" name="Testsubmit" value="Abgeben">
</form>
````

```javascript
let checkForm = function(evt) {
	let feldvalue =document.getElementsByName("Feld")[0].value;
	if(feldvalue == "") {
		alert("Bitte eine Eingabe!");
	} else {
	alert("Danke für Ihre Eingabe!");
	}
}
window.onload = function() {
	let form = document.getElementById("f");
	form.addEventListener("submit",checkForm);
}
```

##### Beispiel keypress

```javascript
let shortCutHandler = function(evt) {
	console.log("Sie haben " + evt.key + " gedrückt.");
	if(evt.ctrlKey) {
		console.log("Sie haben auch den ctrl-Key gedrückt!");
	}
}
window.onload = function() {
	let form = document.addEventListener("keypress",shortCutHandler);
}
/*
Beim drücken von ctrl + k:
Sie haben k gedrückt.
Sie haben auch den ctrl-Key gedrückt!
*/
```

