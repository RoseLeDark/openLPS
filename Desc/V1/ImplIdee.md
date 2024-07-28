# OTC Overlay Trusted/Tiny Coin

Mit dem aufkommen des hype um Bitcoin, war mir früh schon klar dass in Zukunkunft ein Riesen auf kommen an daten entstehen muss. 
In den letzen Jahren, habe ich mich immer wieder damit beschäftigt. So mit 22 Jahren habe ich mich im Züge der entwicklung meiner Grafik engine mit Graphen beschäftigt. Dabei kahm mir die Idee über ein alternatives System, dass auch offline funktioniert und ähnlich dem System wie Bargeld aufgebaut ist. Immer mal wider habe ich hier und dort mal Code fragmente online gestellt. Von ein Bekannten habe ich vor paar Monaten erfahren, dass er und andere solche Systeme gerade Programmieren. Da ich selbst mal mir ja mal gedanken für so ein System gemacht habe, dachte ich mir meine Überlegungen zu veröffentlichen, mit der hoffnung das es andere Inspierieren oder sogar verwenden.

Der Name OTC, ist angelehnt an die 3 Buchstaben abkürzungen für Währungen und steht für Overlay Tiny Coin. Overlay, weil dieses System andere Währungen als basis verwendet und legt nur eine Digiale verwaltungsebene drüber. Es können mehrere Arten von Währungen verwendet werden, sogar wertgegenstände, die einen Wallet genau zugeordnet werden können, ohne das dieses Object real im Besitz der Person ist. Tiny weil das System sehr einfach gehalten werden soll, so das es auf verschiedenen Platformen verwendet werden kann! 
Was ein Coin ist sollte jeden bekannt sein.

Ich habe mir mein Coin System vom Bargeld inspirieren lassen. Ganz wichtig war mir dass es kein Master Server gibt und dass es auch ohne Internet verwendet werden kann! Dafür ist es wichtig, dass niemand das ganze System bzw Netzwerk kennt, sondern jeder nur ein Teil des ganzen. Also wie eine Brieftasche. Jeder Mensch hat eine, mit geld darin. Den 5€ Schein habe ich von jemanden bekommen, wer ihn davor hatte brauch ich nicht wissen und wenn ich ihm weitergebe, weiß ich maximal wem ich den gegeben habe. Was danach mit dem Schein passiert ist nicht wichtig. Also muss ich diese Buchung auch nicht kennen.
Also erstmal bracuht jeder ein Wallet und eine eindeutige ID, diese ID wird im diesem System mit ein eindeutigen Key repräsentiert, auf basis von PGP - mit diesem Key wird auch das Wallet verschlüsselt. 

Da jeder nur ein Teil des Netzwerkes besitzt und überblicken kann, fällt ein Block in den alle Nodes und Überweisungen gespeichert sind weg. Damit aber eine buchung funktionieren kann, wird für jeden einzeilen Coin eine eigene Buchungsliste hinterlegt, somit ist jeder Coin selbst ein Block. 

## Aufbau des Coins im Code
Jeder Coin ist in der Liste aller Coins im Wallet ein Node. Mit folgenden Daten:

| Member     | Beschreibung | DataType | TransferByBuchung
| -------- | ------- | ------- | ------- |
| EID | ID des Erzeugers | string | YES |
| TimeStamp | Timestamp der erzeugung | long long | YES |
| Hash |  Hash aus EID,TimeStamp,LastHash,Wert, BuchungHash | string | NO |
| LastHash | Hash des Vorherigen Coin, bei root immer NULL | string | NO |
| BuchungHash |  Hash alles Buchungen, verändert sich. | string | YES |
| Wert | Siehe beschreibung unten | struct |  YES |
| Transfers |  Siehe beschreibung unten | struct |  YES |
| CreaterHash| Erzeuger Hash bei der Bank, bei erstellung = Hash, ändert sich nie | string | YES |

Bei der Erzeugung des Wallets wird ein Root Node/Coin erstellt mit dem Wert 0 und als erzeuger wird ein Root Hash des benutzden Netzwerk eingetragen. Somit sind verschiedene Netzwerke mit dieser Biblothek erzeugbar. 

### Wert
Der Member Wert ist eine Structur mit folgenden einträgen:

| Member     | Beschreibung | DataType |
| -------- | ------- | ------- |
| Type | Enum mögliche Werte sind Währung[Euro, Doller ...], Objekt, User .... | int |
| Amount | Welchen Wert stellt das Object dar | int32_t // 1,234 => 1234 |
| LossRatio | Wie hoch in Prozent ist der Verlust der Ausgabe. | int8_t |

Wenn jemand zb ein Node mit 5€ erstellt, ist der Type: Euro und Amount 5. Bedeutet der User muss die 5 € aufheben, bis jamand diesen Coin auszahlt. Diese gebühr kann in Prozent unter LossRatio hinterlegt werden. Als beispiel 1,5 Prozent. 
Wenn sich jemand den Node auszahlen möchte bei dem erzeuger bekommt er nur 4,925 Euro. Im ideal Fall sollte dieser Wert bei 0 sein. Dies kann jeder erzeuger frei wählen.

### Transfers (Sibling)

Die Buchungen selber ist auch eine verkettete Liste. Mit folgenden Aufbau:

| Member     | Beschreibung | DataType |
| -------- | ------- | ------- |
| Name | "TC: {Hash der Buchung}" | string |
| OwnerID | Aktueller Besitzer des Coins | string |
| TimeStamp | Timestamp der Buchung | long long |
| Hash |  Hash | string |
| LastHash | Hash der Vorherigen Buchung | string |


Die erste Buchung ist die erzeugung selbst, somit gibt es kein Coin ohne buchung, diese erste buchung wird auch genutzt um im Coin den Hash zu erzeugen, weitere Buchungen verändern nur den "BuchungHash", im Coin selber.

Der Name der Buchung setzt sich aus dem Hash des Benuztend Netzwerk und dem Timestamp plus einem Random Wert. Jede Bunchung beginnt mit dem kürzel "TC:". 

## Example
TC: { [NetzwerkID] + 202408111243 + 673 }
TC:{ ce86e028e8f608970031e8856fc7f18077e631d8ea8f96fceccc141339eb1a2e7a4986cf938e0fc4217b1245248fa097c2c61b309920145e081d5145b49aadc1:202408111243:673}

"TC:9b9a09efb415a7ccf2c9c8e87eae84d8811ebab63391793ae9f4cfdf15e84e2335c3fb02abcb3a6cb66045c0fd39a50407984c8e77198846b0d6a6a7fe5baed4"

## Erzeugung eines Coins

Jeder der ein Wallet besitzt ist kann auch selbst coins erstellen. Da es auf der Basis eines Wertsystems fungiert, braucht es dafür kein Mining oder sonstiges. Da jeden Coin der Besitzer hinterlegt wird, muss dieser User den echten Wertgegenstand, von dem dieser Gegenstand abhängig ist hinterlegen, bis irgend jemand den als reales Geld beansprucht. 

## Aufbau des Walled 
 - Tusted List
 - UserJSON 
 - Hash des verwendeten Netzwerkes - SHA-512

Im Wallet wird jeder Coin gespeichert denn man besitzt und besitzt hat. Bei der weitergabe des Coins, wird in der Buchung der Transfer hinterlegt. Ist im letzten Transfer eine andere Owner ID, als der des Wallets gild, der Coin als verkauft. Weitere Buchungen oder was mit dem Coin passiert können nicht eingesehen werden. Wie im echten Leben weiß ich nicht was mit mein Geld passiert wenn ich es jemanden gebe.

Desweiteren wird im Walled die benutzte Netzwerk Hash hinterlegt. Nur User des gleichen Netzwerkes können, mit einander agieren.

### UserJSON

Auch wird im Walled eine Liste hinterlegt in den jeder User Daten von sich hinterlegen, mindestens eine Art der Kontakt aufnahme muss  hinterlegt werden. Diese Daten werden als einfache JSON Datei hinterlegt.

Bei einem Transfer wird diese JSON Datei mit gegeben und zwar der des erzeugers des Coins. Dies ist für die ausgabe des Wertes oder Gegenstand unerlässlich. 

Man kann aber auch unabhängig andere User so in seine UserListe bzw Trusted List speichern. 

```json
UserJSON:
{
    "eID": "",
    "NetworkHash": "",
    "Contact": [
        {
            "Type": "Mail",
            "Value": "test@domain.tld",
            "UserData": "PGP Fingerprint"
        },
        {
            "Type": "OTCMS", // OTC Messenger Server - a simple server
            "Value": "IPv6:Port", // PublicPGP: https://IPv6/web/public.asc 
            "UserData": "NOTUSE", 
        },
        {
            "Type": "Messenger",
            "Value": "Signal", // Or Whatsapp, SMS, Telegram, 
            "UserData": "Username or Tel",
        }
    ]
}
```

### Trusted List

Im jeden Walled ist eine vertrauens Liste enthalten, bei jeden Kontakt mit einem anderen im Netzwerk wird diese Liste abgeglichen. Wenn ein Coin übertragen wird wird die erzeuger ID auf diese Liste hinterlegt, dieser Eintrag kann jeder User für sich selbst ein Spitznamen geben - dieser Spitzname wird nicht übertragen, an andere User. 
Ist der Erzeuger noch nicht auf der Liste, wird der Erzeuger mit einem Vertrauenswert von 35 hinterlegt. 



### Abgleich und Bewertung

Wenn bei einem abgleich, dieser User mit einem Niedrigen wert gespeichert ist, als bei einem selbst wird das vertrauens level um 4 punkte herabgesetzt. Ist er höher dann um 4 Punkte hinauf. Der maximal wert beträgt 64 und der Niedrigste 0. 
Dem entsprechend werden die einzelnen Coins im Wallet auch farblich und als Wert hinterlegt.
 
| Farbe | Punkte
| -------- | ------- |
| Schwarz | < 12 | 
| Rot |  12 - 19 |
| Gelb | 20 - 29 |
| Grün | 30 - 39 |
| Blau | 40 - 49 |
| Lila | >= 50 |

Sollte das Vertrauen des erzeugers unter 12 sinken, wird zusätzlich der node durchgestrichen. Den Wert behält der Coin, aber das vertrauen ist dadurch sehr gering.

Ein abschalten dieser Funktion ist nicht erlaubt und stellt ein verstoß des Netzwerkes dar! 
Zusätzlich kann diese Liste zu einen bestimmten intervall an einen Master server des Netzwerkes abgeglichen werden, dies ist kein muss. Dieser Server darf keine Coins erstellen und auch selbst keine Buchungen erzeugen. Der Server darf nur die vertrauen listen verwalten ohne Spitznamen.

Beim Download des Servers werden reale Werte im Walled übernommen.

Sollte eine auszahlung oder in der Kommunikation mit dem Erzeuger desCoins schwierigkeiten auftreten wird dies in der vertrauens Liste anhand des Wertes sichtbar gemacht. Bei einer nicht auszahlung wird das vertrauen um 15 Punkte herabgestüft. 
Bei beleidigungen und unfairen verhalten sind es 4 Punkte. Jede erfolgreiche Buchung steigert den Wert um 10 Punkte. 

Diese Werte können je nach Netzwerk unterschiedlich sein. 

Vertrauen und ein höfflicher Umgang ist vorraussetzung !!

## Verfügbare Netwerke

| Name     | SHA512 | Server |
| -------- | ------- | ------- |
| LibOtC2009  | ce86e028e8f608970031e8856fc7f18077e631d8ea8f96fceccc141339eb1a2e7a4986cf938e0fc4217b1245248fa097c2c61b309920145e081d5145b49aadc1    | NO |


## Implantierung

Die Node Biblothek habe ich vor Jahren schon mal per C# geschrieben, die wird aus sicherheitsgründen komplett in C++ neu geschrieben. Siehe Projekt libnotc. 

Eine anbindung an C#, python und PHP wird über ein wrapper in C implantiert. Der Wrapper ist teil von libnotc. 

PHP: php-notc
Python: python-notc
Mono: notc#

Das Walled selbst wird in C# Implantiert. Auch für den ESP32 wird ein demo Walled implantiert wobei der nur coins erstellen kann, wenn im Automaten dem entsprechend ein Geldschein / Geldstück eingezahl wird. Als kleiner Geld Automat und per NFC an das Walled des einzahlenden überträgt. Dies wird per PlatformIO realisiert. 

## Versionsliste
Version | Datum | Beschreibung
------ | ------ | ------ |
0.0 | Sommer 2009 | Erste überlegung und Aufschreibung der ersten Ideen 
0.1 | Januar 2020 | Erste Version per C# auf github https://github.com/RoseLeBlood/libnode
0.2 | 07.2024 | Starten des Projectes und diese Datei

## Licens: GPL

28.07.2024 Amber-Sophia Schroeck 
