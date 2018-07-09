# Webbasierte Anwendungen

##Grundlagen (Vorlesung 1)

### Problemfelder - Übersicht

![Problemfelder](C:\Users\Andre\Desktop\WBA-Vorlesung\Problemfelder.PNG)

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
- texxt/html
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

