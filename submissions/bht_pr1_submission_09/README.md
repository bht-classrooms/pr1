# Übung 9 – Blitzer

![Photo by Pixabay](pexels-pixabay-248747.jpg)
 *https://www.pexels.com/photo/close-up-of-electric-lamp-against-black-background-248747/*

## Einleitung

In dieser Übung scheiben Sie ein Programm, welches auf Basis von Geschwindigkeitsmessungen bestimmt, ob ein Auto zu schnell gefahren ist, und Tickets für zu schnell fahrende Autos ausstellt. Eine Messung findet an zwe Punkten statt um somit die Geschwindigkeit zu bestimmen.

## codeboard.io 

Rufen Sie das Codeboard zur [Übung 9 im Moodle-Kurs](https://lms.bht-berlin.de/mod/lti/view.php?id=918231) auf. 

Falls Sie in Codeboard nicht eingeloggt sind, melden Sie sich bitte mit dem Codeboard-Account ein, den Sie in der [Übung 0](../bht_pr1_submission_00/README.md) angelegt haben.

## Aufgabe

* Eine Messung hat vier Eigenschaften/Attribute
  * `badge`: Das Nummernschild des Autos
  * `start`: Die Start-Zeit der Messung
  * `end`:   Die End-Zeit der Messung
  * `distance`: Der Strecke, die das Auto zwischen `start` und `end` gefahren ist (in Meter).

Die Geschwindigkeitsmessungen liegen Ihnen in einem Textformat vor:

```
badge     ; start               ; end                 ; distance
D-HF 2345 ; 2000-01-23T11:22:33 ; 2000-01-23T12:22:33 ; 1000
B-AT 6724 ; 2001-03-12T00:00:00 ; 2001-03-12T00:01:00 ; 800
...
```

Als String ist dieses Texformat folgendermaßen codiert:

```
String input = 
    "badge     ; start               ; end                 ; distance\n"
  + "D-HF 2345 ; 2000-01-23T11:22:33 ; 2000-01-23T12:22:33 ; 1000\n"
  + "B-AT 6724 ; 2001-03-12T00:00:00 ; 2001-03-12T00:01:00 ; 800\n"
  + ...
;
```

* Jede Zeile repräsentiert eine Messung:
  * Zeilen sind durch das Zeichen `\n` getrennt
  * Spalten sind durch das Zeichen `;` getrennt

* Der Inhalt der Messgungen kann korrupt/verfäscht sein:
  * Es können zusätzliche Zeilen (`\n`) ohne Spalten enthalten sein
  * Es könnten falsche Trennzeichen für Spalten verwendet werden (nicht `;`) 

Nach dem Einlesen und Bereinigen der Messungen wird von Ihrem Programm erwartet, dass sie sie Anzahl der Messungen in der Konsole ausgeben:

```
Total transit count: x
```

wo bei `x` die Anzahl der einlesbaren Messungen ist.

### Regeln um ein Parkticket auszustellen:
* Jede Messung hat eine ***75%ige Chance*** stichprobenartig ausgewählt zu werden.
* Wenn eine Messung ausgewählt ist, so darf die Geschwindigkeit nicht höher als 50 km/h sein.
* Ist die Geschwindigkeit zu hoch wird folgende Ausgabe auf der Konsole erwartet:

```
Car with badge 'X-YZ xxxx' was speeding at xx.x km/h. Sending a ticket.
```

wobei `X-YZ xxxx` und `xx.x` nur Beispielwerte sind.


### Codeboard

* Das codeboard-projekt enthält die `Main.java` und die `TicketMachine.java`. 
* In der `Main.java` ist ein String (`input`) mit einigen Beispielmessungen, aber auch mit Fehlmessungen (z.B. zusätzliche `\n`) definiert.

## Hilfreiche Klassen und Methoden

### String#split(String)
[split(String)](https://docs.oracle.com/javase/7/docs/api/java/lang/String.html#split(java.lang.String)) Methode der Klasse `String`

```
"test; foo".split(";")
``` 
ergibt
```
String[] { "test", " foo" }
```

### String#trim()
[trim()](https://docs.oracle.com/javase/7/docs/api/java/lang/String.html#trim()) Methode der Klasse `String`

```
" fooo ".trim() 
```
ergibt
```
"fooo"
```

### LoalDateTime#parse(CharSequence)

[parse(CharSequence)](https://docs.oracle.com/javase/8/docs/api/java/time/LocalDateTime.html#parse-java.lang.CharSequence-) Methode der Klasse `String`

```
LocalDateTime.parse("2018-02-08T15:22:04")
```
ergibt eine Instanz/Objekt der `LocalDateTime` Klasse.

### Integer.valueOf(String)
[valueOf(String)](https://docs.oracle.com/javase/7/docs/api/java/lang/Integer.html#valueOf(java.lang.String)) Methode der Klasse `Integer`

```
Integer.valueOf("1000")
```

ergibt die Integer-Zahl `1000`.

### Random.nextDouble()

[nextDouble()](https://docs.oracle.com/javase/8/docs/api/java/util/Random.html#nextDouble--) Methode der Klasse `Integer`

Bei diesem Code:
```
Random random = new Random();
if(random.nextDouble() > 0.33) {
    // ...
}
```

wird der If-Block nur mit einer Wahrscheinlichkeit von 33% ausgeführt.

### Code Konvention / Stil

***Generell***
* Verwenden Sie kein `static` bei Methoden oder Attributen, wenn es nicht notwendig ist.
* Halten Sie möglichst alle Attribute `private`, bis Sie einen Grund haben es `public` zu machen. 
* Getter für private Attribute sind besser, als ein Attribut public zu machen.
* Beachten Sie die Einrückung (_indentation_) des Codes
* Schreiben Sie genug Kommentare, damit Sie oder jemand anderes ihr Programm besser verstehen kann.
* Vergeben sie sinnvolle Variablen-Namen, die zum Verständnis des Programms beitragen.
* "Hard-Coden" Sie keine Lösungen.

## Hinweis für die Auto-Bewertung

* Wenn Sie den Schalter `Test` in codeboard betätigen, werden einige wenige Testfälle gerüft. 
* Sie sollten Ihren Code aber gründlich für verschiedene Randfälle von Eingaben des Benutzers prüfen. In dieser Übung gibt es keine weiteren Extra-Tests, die bei `Submit` ausgeführt werden. Sie können also alle Tests sehen, mit denen Sie 100% der Punkte erreichen können.

---

<a href="https://www.pexels.com/photo/123-let-s-go-imaginary-text-704767/">
<img src="../pexels-sevenstorm-juhaszimrus-704767.jpg" width="100" height="100" alt="Photo by SevenStorm JUHASZIMRUS: https://www.pexels.com/photo/123-let-s-go-imaginary-text-704767/">
</a>

Ich wünsche Ihnen viel Spaß bei der Übung! 

