# OTC Overlay Trusted/Tiny Coin

Mit dem aufkommen des Hype um Bitcoin, war mir früh schon klar dass in Zukunkunft ein Riesen auf kommen an daten entstehen muss. 
In den letzen Jahren, habe ich mich immer wieder damit beschäftigt. So mit 22 Jahren habe ich mich im Züge der entwicklung meiner Grafik engine mit Graphen beschäftigt. Dabei kahm mir die Idee über ein alternatives System, dass auch offline funktioniert und ähnlich dem System wie Bargeld aufgebaut ist. Immer mal wider habe ich hier und dort mal Code fragmente online gestellt. Von ein Bekannten habe ich vor paar Monaten erfahren, dass er und andere solche Systeme gerade Programmieren. Da ich selbst mal mir ja mal gedanken für so ein System gemacht habe, dachte ich mir meine Überlegungen zu veröffentlichen, mit der hoffnung das es andere Inspierieren oder sogar verwenden.

Der Name OTC, ist angelehnt an die 3 Buchstaben abkürzungen für Währungen und steht für Overlay Tiny Coin. Overlay, weil dieses System andere Währungen als basis verwendet und legt nur eine Digiale verwaltungsebene drüber. Es können mehrere Arten von Währungen verwendet werden, sogar wertgegenstände, die einen Wallet genau zugeordnet werden können, ohne das dieses Object real im Besitz der Person ist. 

Ich habe mir mein Coin System vom Bargeld inspirieren lassen. Ganz wichtig war mir dass es kein Master Server gibt und dass es auch ohne Internet verwendet werden kann! Dafür ist es wichtig, dass niemand das ganze System bzw Netzwerk kennt, sondern jeder nur ein Teil des ganzen. Also wie eine Brieftasche. Jeder Mensch hat eine, mit geld darin. Den 5€ Schein habe ich von jemanden bekommen, wer ihn davor hatte brauch ich nicht wissen und wenn ich ihm weitergebe, weiß ich maximal wem ich den gegeben habe. Was danach mit dem Schein passiert ist nicht wichtig. Also muss ich diese Buchung auch nicht kennen.
Also erstmal braucht jeder ein Wallet und eine eindeutige ID, diese ID wird im diesem System mit ein eindeutigen Key repräsentiert, auf basis von PGP - mit diesem Key wird auch das Wallet verschlüsselt. 

Da jeder nur ein Teil des Netzwerkes besitzt und überblicken kann, fällt ein Block in den alle Nodes und Überweisungen gespeichert sind weg. Damit aber eine buchung funktionieren kann, wird für jeden einzeilen Coin eine eigene Buchungsliste hinterlegt, somit ist jeder Coin selbst ein Block. 

Das OTC Overlay Trusted/Tiny Coin System unterscheidet sich in mehreren wesentlichen Punkten von anderen Kryptowährungen:

#### Dezentralisierung und Offline-Funktionalität
  - **OTC Overlay Trusted/Tiny Coin:** Das System ist so konzipiert, dass es ohne zentrale Server und sogar ohne Internetverbindung funktioniert. Jeder Nutzer kennt nur einen Teil des Netzwerks, ähnlich wie bei Bargeld.
  - **Andere Kryptowährungen:** Die meisten Kryptowährungen, wie Bitcoin und Ethereum, sind auf ein Netzwerk von Knoten angewiesen, die ständig online sein müssen, um Transaktionen zu verifizieren und die Blockchain zu aktualisieren.

#### Transaktionsstruktur
  - **OTC Overlay Trusted/Tiny Coin:** Jede Münze hat eine eigene Transaktionsliste, was bedeutet, dass jede Münze ein eigener Block ist. Dies eliminiert die Notwendigkeit eines zentralen Ledgers.
  - **Andere Kryptowährungen:** Transaktionen werden in Blöcken zusammengefasst und in einer gemeinsamen Blockchain gespeichert, die von allen Knoten im Netzwerk geteilt wird.

#### Sicherheit und Anonymität
- **OTC Overlay Trusted/Tiny Coin:** Verwendet PGP-Schlüssel zur Verschlüsselung von Wallets und zur Sicherstellung der Anonymität der Nutzer. Es gibt keine zentrale Instanz, die das gesamte Netzwerk überwacht.
- **Andere Kryptowährungen:** Nutzen kryptografische Techniken wie SHA-256 (Bitcoin) oder Ethash (Ethereum) zur Sicherung der Blockchain. Transaktionen sind pseudonym, aber die Blockchain ist öffentlich einsehbar.

#### Wertsystem:
- **OTC Overlay Trusted/Tiny Coin:** Kann verschiedene Arten von Werten, einschließlich physischer Gegenstände, integrieren. Der Wert eines Coins kann durch reale Vermögenswerte gedeckt sein, die vom Besitzer hinterlegt werden müssen.
- **Andere Kryptowährungen:** Der Wert basiert hauptsächlich auf Angebot und Nachfrage auf dem Markt. Physische Gegenstände werden in der Regel nicht direkt in das System integriert.

#### Flexibilität und Einfachheit:
- **OTC Overlay Trusted/Tiny Coin:** Das System ist so gestaltet, dass es einfach und auf verschiedenen Plattformen nutzbar ist, ohne die Notwendigkeit für Mining oder komplexe Infrastruktur.
- **Andere Kryptowährungen:** Viele erfordern Mining (z.B. Bitcoin) oder komplexe Smart Contracts (z.B. Ethereum), was eine höhere technische Komplexität und Infrastruktur erfordert.

Diese Unterschiede machen das OTC Overlay Trusted/Tiny Coin System zu einer einzigartigen Lösung für den sicheren und dezentralen Austausch von Werten, die sowohl online als auch offline funktioniert.

Für weitere Informarionen siehe hier: [ImplVersion1000.md](/Desc/V1/ImplIdee.md)
