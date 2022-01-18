# Probeklausur Webtechnologien

Die Klausur besteht aus zwei Teilen: einem praktischen und einem theoretischen Teil.
Sie haben insgesamt 90 Minuten Zeit für die Bearbeitung, massgeblich ist der Zeitstempel des entsprechenden Commits.
Sie müssen Ihre Abgabe auf mindestens vier Commits aufteilen (z.B. 1x zu Beginn, 1x nach 25min, 1x nach 50min, 1x nach 89min), ansonsten gibt es Punktabzug von bis zu 20 Punkten.
Es handelt sich um eine Open-Book-Klausur, Sie müssen jedoch nicht offensichtliche Quellen ausreichend kennzeichnen und dürfen keine fremde Leistung als Ihre eigene darstellen.

## Theoretischer Teil (50 Punkte)

Beantworten Sie die Fragen, die Sie in der Datei QUESTIONS.md finden. 
Die Fragen beziehen sich teilweise auf den Code in diesem Repository.
Schreiben Sie Ihre Antworten direkt in diese Datei unter die jeweilige Frage.
Wenn sinnvoll, schreiben Sie Freitext, jedoch höchstens drei Sätze pro Frage (in der Regel weniger).
Bei manchen Fragen ist eine Beantwortung als Auflistung sinnvoller, aber achten Sie hier darauf, dass es unmissverständlich ist, was Sie auflisten.
Reichen Sie das Ergebnis per Git Commit & Push ein. 
Sie können die Beantwortung über mehrere Commits verteilen und Ihre Antworten bis zum Ende der Bearbeitungszeit korrigieren.

## Praktischer Teil (50 Punkte)

Der Umfang des praktischen Teils der Klausur wird kleiner ausfallen als hier.

### Voraussetzungen

Zur Bearbeitung dieser Aufgabe wird folgende Software benötigt:

- Java 11
- gradle 7.3.x
- node 16.11.x

### Aufgaben

Sie werden im Rahmen dieser Aufgabe eine simple Webanwendung implementieren, die dem User zufällige Chuck Norris Sprüche anzeigt.

#### Backend und Frontend starten

1. Forken und Clonen Sie dieses Repository

2. Starten Sie die Spring Boot Anwendung. Rufen Sie in Ihrem Browser oder Postman die URL [`http://localhost:8080/actuator/health`](http://localhost:8080/actuator/health) auf. Wird Ihnen `{"status":"UP"}` angezeigt, ist Ihre Anwendung erfolgreich gestartet.

3. Starten Sie die Vue App. Führen Sie dazu, ausgehend vom Projektverzeichnis, folgende Befehle sequentiell aus:

```shell
cd frontend
npm install
npm run serve
```

4. Navigieren Sie in Ihrem Browser zur Adresse [`http://localhost:3000`](http://localhost:3000). Ihnen sollte die folgende Seite angezeigt werden:

<img width="1656" alt="Bildschirmfoto 2022-01-14 um 18 05 46" src="https://user-images.githubusercontent.com/81008192/149558236-0273d818-abb1-432a-8f50-7673361c8ccd.png">

#### Backend implementieren

5. Implementieren Sie das Interface `QuotesService`. Die Implementierungsdetails entnehmen Sie bitte dem JavaDoc.

6. Implementieren Sie einen Rest-Controller, deren Endpunkt Sie anschließend aus einer Vue-Komponente aufrufen, um einen zufälligen Chuck Norris Spruch zu laden. Berücksichtigen Sie folgende Details:

    - der Controller soll die Implementierung des Interfaces `QuotesService` benutzen, um sich einen Chuck Norris Spruch zu holen
    - der Endpunkt soll unter `/api/v1/quotes` und via `GET` erreichbar sein
    - der Client übermittelt den Index via Request-Parameter `index`, also z.B. `/api/v1/quotes?index=53`
    - Verwenden Sie für die Rückgabe die Klasse `QuoteResponse` (ggf. mit `ResponseEntity` als Wrapper)
    - der Endpunkt soll dem Client ein JSON liefern
    
#### Frontend implementieren

7. Es existiert mit der Komponente `ChuckNorrisQuote.vue` bereits eine Vue-Komponente, die aktuell jedoch keine Dynamik aufweist. Implementieren Sie die Methode `loadRandomQuote()`. Rufen Sie in der Methode Ihren Rest-Endpunkt auf. Verwenden Sie die Methode `getRandomInt()`, um Zufallszahlen zu erzeugen. Die Obergrenze `maxExclusive` muss 79 sein, da es nicht mehr Quotes im Backend gibt. Sobald die Seite neu geladen wird, soll ein neuer Spruch geladen und angezeigt werden.

8. Erweitern Sie die Vue-Komponente wie folgt: Sobald der User auf Chuck Norris klickt, soll ein neuer Spruch angezeigt werden.

9. Implementieren Sie eine Route zur View `AboutMe.vue`.

10. Erstellen Sie im Ordner `frontend/src/components` eine neue Vue-Komponente `AboutMeDetails.vue`. Diese Komponente soll Details über Sie anzeigen, z. B. Ihren Namen und Ihre Matrikelnummer. Sie können hier aber gener kreativ sein. Verwenden Sie mind. 3 CSS-Attribute für das Syling.

11. Verwenden Sie Ihre soeben erstellte Komponente in der View `AboutMe.vue` analog zur View `AboutChuck.vue`. 

12. Testen Sie alle Funktionalitäten Ihrer Vue App im Browser.

#### Unit Tests

13. Implementieren Sie mind. 1 Unit-Test für das Frontend.

14. Implementieren Sie mind. 1 Unit-Test für das Backend.
