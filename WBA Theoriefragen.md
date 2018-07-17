# WBA Theoriefragen

## Wie erfolgt die Übergabe der Daten vom Client zum Server mit dem HTTP-GET Befehl?

1. User ruft im Browser eine URL auf
2. Browse löst URL ggf. mit Hilfe von DNS zu einer IP-Adresse auf 
3. Browser baut damit eine TCP-Verbindung mit dem Webserver auf und schickt einen GET-Request
4. Webserver antwortet mit der angeforderten Seite
5. TCP-Verbindung wird wieder abgebaut
6. Browser zeigt die Webseite an

Daten können sich bei einem GET-Befehl in der URI befinden oder in einer Query als Parameter.

?a=5&b=7

## Nennen Sie die wichtigste Quelle für Web-Standards

- W3C (https://www.w3.org/)


## Was ist der Unterschied zwischen strukturellen und semantischen Auszeichnungen?

### strukturelle Auszeichnungen

- Kenntlichmachen von Seiten-Bereichen
- optische Auszeichnung
- Texte zum Beispiel Fett oder Kursiv -> jedoch keine besondere Bedeutung
- dienen der Strukturierung
- Kennzeichnung von Menüs, Artikeln...

### semantische Auszeichnungen

- Auszeichnung von Inhalten -> zur Ermittlung ihrer Bedeutung
- zeigt an, ob es sich um eine Überschrift, Zitat, etc. handelt
- Vokabulare, SemanticWeb


## Nennen Sie die Kaskadierungs-Reihenfolge von CSS

- Browser
- Extern und Intern (in Deklarations-Reihenfolge)
- Inline

## Schreiben Sie eine CSS-Selektor der das Element mit der id „sel“ auswählt

\#sel { MAGIC }
## Auf welche Arten kann ein JavaScript in eine HTML-Seite eingebunden werde?



- External: Aus einer anderen Datei in Header oder Body einbinden
- Internal: Script-Tag in Header oder Body
- InAttribute: In einem onKlick Attribut. Diese möglichkeit ist jedoch veraltet

```html
<head>
    <!----External----->
	<script src=“datei.js“></script>
    <!----Internal----->
  	<script>...</script>
</head>
<body>
    <!----External----->
	<script src=“datei.js“></script>
    <!----Internal----->
    <script>...</script>
    <!----InAttribute----->
	<a href=“#“ onclick=“alert(‘Ausgabe‘)“>Link</a>
</body>
```



## Wann werden JavaScripte ausgeführt?

JavaScripte werden ausgeführt, sobald der Browser sie vollständig geladen hat. 

##Geben Sie alle Eltern-/Kindbeziehungen innerhalb dieser Knotenmenge an

```html
<html>
	<head>
		<title>Beispiel</title>
	</head>
	<body>
		<h1>Hallo DOM</h1>
		<p>Ein 
            <strong>
                <em>kurzes</em>
            </strong>
            Beispiel
        </p>
	</body>
</html>

```

- html
  - head
    - title
      - 	Beispiel
  - body
    - h1

      - Hallo DOM 	
    - p

      - Ein 

      - strong
        - em
          - kurzes
      - Beispiel
        ​    



## Was muss der Browser machen, nachdem er folgende Antwort auf eine GET-Anfrage vom Server bekommen hat?

```http
/HTTP/1.1 401 Unauthorized
Date: Mon, 13 Jan 2003 08:35:41 GMT
Server: Apache/1.3.24 (Win32) PHP/4.3.0 WWW-Authenticate: basic realm=“geschuetzterBereich“
```

**Antwort:**

1. Browser muss nach Benutzername und Password fragen
2. GET-Request mit zusätzlichem Authorization-Header erneut senden

```http
GET /secure_document.html HTTP/1.0
Accept: image/gif, image/jpeg, */* 
Accept-charset: iso-8859-1, *, utf-8 
Accept-encoding: gzip 
Accept-language: en 
User-Agent: Mozilla/4.51 [en] (WINNT; I) 
Authorization: Basic aGVpa286d29laHI
```
## Welche Technologie macht es ihnen bei Java-WebServices einfach, ihre Datenobjekte als JSON oder XML über einen REST-WebService auszuliefern?

Die REST Implementierung in Java kann aus empfangenen Daten automatisch Objekte erstellen.
Annotation von Entities ermöglicht die XML/JSON Serialisierung
JAX-RS (Rest-Implementierung) verwendet (JAXB XML/JSON Interface)

## Was bewirkt die Methode persist() vom Interface EntityManager?

Mit der Methode persist() vom Interface EntityManager wird ein transientes
Entity in der Datenbank gespeichert und in den Zustand managed überführt.

- Transient 
  - Objekt noch nicht an Entity-Manager übergeben, noch kein Äquivalent inder DB


  - Managed
    - Objekt unter Kontrolle des Entity-Managers

    - Managed Entities werden im Persistenzkontext überwacht. 


## Was ist der Unterschied zwischen einer JSP und einem Servlet?

Servlets sind Programme, die auf einem Web- oder Applikationsserver laufen. Sie dienen als Vermittlungsschicht zwischen einem Request von einem Browser (oder anderem HTTP-Client) und Datenbanken oder Applikationen auf dem HTTP-Server.

JSP ist eine Technologie um inhaltlich dynamische Webseiten zu entwerfen, indem Java-Code in HTML-Seiten eingebunden wird. JSP sind aspx/php-Seiten ähnlich und laufen serverseitig. (Javascript- oder HTML-Code in JSP-Seiten läuft clientseitig)

  ### Unterschiede:

  - Bei Servlets wird html in Java eingebunden, während bei JSP java in html eingebunden wird
  - Servlets laufen schneller
  - JSP können in Servlets umkompiliert werden
  - JSP ist eine Web-Skriptsprache, mit der dynamische Inhalte erzeugt werden können, während Servlets kompilierte JavaProgramme sind, mit denen aber auch dynamische Inhalte erzeugt werden können



## Erklären Sie die grundsätzliche Idee der MV* Muster

Grundsätzliche Idee der MV* Muster ist, dass es eine Aufteilung zwischen Model (Logic) und View (Anzeigen) gibt.  Ein dritter Teil (Controller/Presenter/ViewModel) übernimmt die Verbindung zwischen Model und View 

## Was ist ein Framework?

Frameworks für Webapplikationen stellen ein Rahmenwerk zur Umsetzung einer Architektur zur Verfügung. Sie beeinflussen den Entwicklungsprozess. Framewors legen dabei keine Art der Anwendung fest, sondern geben nur den Rahmen vor. Sie rufen die Anwendungslogik auf, wenn diese benötigt wird und gibt die Struktur vor, in welcher diese implementiert werden soll.