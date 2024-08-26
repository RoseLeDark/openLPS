# Coin Erstellung, Transfer

## Bank
Eine Bank sind zu erstellung, validierung und auszahlung vorbehalten. In einen Netzwerk dürfen mehrere "Banken" exestieren. Eine Bank muss in einen Netzwerk erreichbar sein, ob im Internet, Intranet, Bluethoot etc. pp. spielt keine Rolle. Dies obliegt dem Betreiber der Netzwerkes.
Jede Bank muss mindesten eine Art der Komunikation angeben und alle Eistellungen die getroffen worden sind. Als JSON. Diese Information wird dem jenigen angezeit der mit diser Bank ein Coin erstellen möchte. Jede Bank hat eine eindeutige ID.

Eine Bank ist auch gleichzeitig ein User und kann handeln.

## Erstellung
Wenn ein Coin erstellt wird, wird in einer Liste der Coin gespeichert und die letzten 10 Transaktionen (standart einstellung). In der 1. Transaktion wird die Transaktion von der Bank zum 1. User gespeichert. Den Wert gegenstand bleibt bis zur Uasgabe im Besitz der Bank, erst bei der Einfoderung wechselt der Besitzer und der Coin wird als wertlos gespeichert. 



## Transfer
Bei einen Transfer muss man der Sender nicht online sein. Dies erhöht aber die sicherheit, dass der Coin auch gedeckt ist. Bei einem Transfer wird beim vorherigen Besitzer der Transfer gespeichert und beim neuen Besitzer die Transfer liste mit den vorherigen Besitzer übertragen, die enthält aber nicht alle buchungen sondern nur den ersten Transfer vom ersteller und die Letzte Buchung, also diese hier. Somit ist nicht ersichtlich wer den Coin schon alles besessen hat. Wenn einer von den beiden online ist wird die Buchung an die Bank übertragen. Die Bank speichert das Datum und die Letze Buchung, nur die letzten 10 Buchungen werden gepsichert (standart einstellung) und überträgt zum aktuellen Besitzer ein Hash um die Buchung zu validieren. Dies kann auch nachträglich passieren, aber erst mit diesem Hash kann dieser Coin weiterverwendet werden.

## Validierung
Bei der Validierung des Coins wird bei der Bank überprüft ob die Aktuelle ID, hash der Buchung und das Datum passt  zu der letzten gespeicherten Buchung. Wenn dies Passt wird der Coin grün makiert. Nach einen Transfer wird der Coin grau hinterlegt oder ausgeblendet, je nach einstellung der verwendeten App.
Besteht keine möglichkeit der Validierung dann wird der Coin gelb mackiert.
Ist der Coin nicht validierbar wird er rot mckiert und jeglicher Transfer ist mit diesem Coin nicht mehr möglich. Eine Freischaltung ist nur über den ersteller möglich! 

Zur Validierung wird keine möglichkeit vorgeschrieben, bei der Verwendung in ein eigenen Netzwerk kann dies jeder selbst implantieren. 
