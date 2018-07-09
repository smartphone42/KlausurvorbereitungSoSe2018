# Webbasierte Anwendungen

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




