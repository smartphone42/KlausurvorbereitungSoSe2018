Webbasierte Anwendungen

## Grundlagen (Vorlesung 1

### Problemfelder - Übersicht

![Problemfelder](Ressourcen\Problemfelder.PNG)

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

  \<html> Root-Tag – Umfasst den gesamten Dokumenteninhalt
  \<head> Dokumenten-Kopf – Titel, Metadaten, Includes,..
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

\<meta>: Gibt Meta-Informationen an

charset: Verwendete Zeichenkodierung auf der Seite

viewport: Zu verwendende Breite und Standard-Zoom (Multi-Devices)

Allgemein: Meta-Informationen zum Inhalt (Keywords, Beschreibung,…)

\<link>: Angabe wichtiger externen Ressourcen

\<script>: Einbettung oder Einbindung von Skripten 

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

![Strukturelle Tags](Ressourcen\Strukturelle Tags.PNG)



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

\<table>: Die enthaltenen Elemente stellen eine gemeinsame Tabelle dar

\<tr>: Umfasst alle Elemente einer Tabellen-Zeile

\<th>: Eine Zelle einer Kopfzeile

\<td>: Eine Zelle einer Tabellen-Spalte

```html
<table>
	<tr>
		<th colspan="2"> Kopfzeile</th>
	</tr>
	<tr><td>Zelle links</td><td> Zelle rechts</td></tr>
</table>
```

![TabelleExample](C:\Users\Andre\Desktop\WBA-Vorlesung\Zusammenfassung\Ressourcen\TabelleExample.PNG)

##### Listen

\<ul>: Eine Liste ungeordneter Elemente

\<ol>: Eine Liste geordneter (nummerierter) Elemente

\<li>: Ein Listeneintrag für un-, geordnete Listen

\<dl>: Eine Liste für Definitionen 

\<dt>: Term-Eintrag in einer Definitionsliste

\<dd>: Erläuterungs-Eintrag in einer Definitionsliste


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

<form>: Umschließt alle Elemente eines Formulars und legt Attribute fest

**Attribute:**

action: URL an welche die Daten aus dem Formular gesendet werden

method: bestimmt die HTTP-Methode die zum Versand genutzt wird

enctype: bestimmt den Mime-Type in dem Versendet wird

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


| Type       | Beschreibung                             | Beispiel                                 |
| ---------- | ---------------------------------------- | ---------------------------------------- |
| text       | einzeiliges Eingabefeld                  | \<input type="text" name=s>               |
| password   | einzeiliges Eingabefeld mit nicht sichtbaren Zeichen | \<input type="password" name=s>           |
| number     | ein Zahlenwert                           | \<input type="number" name=s>             |
| range      | ein Zahlenwert aus einem bereich         | \<input type="range" name=s min="0" max="10"> |
| color      | Farbangaben                              | \<input type="color" name=s>              |
| email      | Eine E-Mail Adresse                      | \<input type="email" name=s>              |
| file       | Eine Datei                               | \<input type="color" name=s>              |
| tel        | Eine Telefonnummer                       | \<input type="file" name=s>               |
| url        | Eine URL                                 | \<input type="url" name=s>                |
| checkbox   | es können beliebig viele Optionen aktiviert werden | \<input type="checkbox" name="s" value="A"> <br> \<input type="checkbox" name="s" value="B"> |
| radio      | es kann nur eine einzige Option aktiviert werden | \<input type="radio" name="s" value="male"> <br> \<input type="radio" name="s" value="female"> |
| \<select>   | Drop-Down-Liste mit <option> Elementen   | \<select> \<option value="A"> A \</option> \</select> |
| \<textarea> | Ein mehrzeiliges Texteingabefeld         | \<textarea rows="4" cols="50"> ...\</textarea> |


**Browser können:** 
- Auf den Datentyp abgestimmte Eingabeelemente anzeigen
- vor dem Absenden prüfen, ob Werte für den angegebenen Typ gültig sind.

##### Button

###### Formular Buttons

\<input>: Buttons in Formularen ins Eingabeelemente mit Typ:

submit: Absenden des Formulars

reset: Zurücksetzen aller Inhalte auf den Ladezustand

```html
<form action="/action_page.php">
	First name:<br>
	<input type="text" name="firstname" value="Mickey"><br>
	Last name:<br>
	<input type="text" name="lastname" value="Mouse"><br><br>
<input type="submit" value="Submit">
</form> 
```

​	![formularButton](.\Ressourcen\formularButton.PNG)

###### Script Button

\<button>: Buttons für die Verwendung mit Skripten

```html
<button onclick="myFunction()">Click me</button>
```

##### Gestaltung

\<label>: Beschriftung für ein Eingabeelement

\<fieldset>: Eingabeelemente gruppieren

\<legend>: Beschriftung für eine Gruppierung

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

![gestaltungLabel](.\Ressourcen\gestaltungLabel.PNG)

#### Mediadatein

##### Bilder

\<picture>: Definiert ein Bild Objekt

\<source>: Definiert eine Bildquelle

media: Gibt an, wann die Bildquelle verwendet werden soll

srcset: URL zum Bild

\<img>: Fallback-Tag für alte Browser

alt: Alternativtext; angezeigt, wenn das Bild nicht verfügbar ist

````html
<picture>
	<source media="(min-width: 650px)" srcset="a.jpg">
	<source media="(min-width: 465px)" srcset="b.jpg">
	<img src="c.jpg" alt="Letters">
</picture>
````

##### Audio


\<audio>: Definiert ein Audio-Objekt

\<source>: Definiert eine Audioquelle

src: URL zur Audiodatei
type: Typ der Audiodatei
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

\<video>: Definiert ein Video-Object

\<source>: Definiert eine Videoquelle

src: URL zur Videodatei

type: Typ der Datei

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

