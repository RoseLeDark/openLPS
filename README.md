# OTC Overlay Trusted/Tiny Coin

Mit dem aufkommen des Hype um Bitcoin, war mir früh schon klar dass in Zukunkunft ein Riesen auf kommen an daten entstehen muss. 
In den letzen Jahren, habe ich mich immer wieder damit beschäftigt. So mit 22 Jahren habe ich mich im Züge der entwicklung meiner Grafik engine mit Graphen beschäftigt. Dabei kahm mir die Idee über ein alternatives System, dass auch offline funktioniert und ähnlich dem System wie Bargeld aufgebaut ist. Immer mal wider habe ich hier und dort mal Code fragmente online gestellt. Von ein Bekannten habe ich vor paar Monaten erfahren, dass er und andere solche Systeme gerade Programmieren. Da ich selbst mal mir ja mal gedanken für so ein System gemacht habe, dachte ich mir meine Überlegungen zu veröffentlichen, mit der hoffnung das es andere Inspierieren oder sogar verwenden.

Der Name OTC, ist angelehnt an die 3 Buchstaben abkürzungen für Währungen und steht für Overlay Tiny Coin. Overlay, weil dieses System andere Währungen als basis verwendet und legt nur eine Digiale verwaltungsebene drüber. Es können mehrere Arten von Währungen verwendet werden, sogar wertgegenstände, die einen Wallet genau zugeordnet werden können, ohne das dieses Object real im Besitz der Person ist. Tiny weil das System sehr einfach gehalten werden soll, so das es auf verschiedenen Platformen verwendet werden kann! 
Was ein Coin ist sollte jeden bekannt sein.

Ich habe mir mein Coin System vom Bargeld inspirieren lassen. Ganz wichtig war mir dass es kein Master Server gibt und dass es auch ohne Internet verwendet werden kann! Dafür ist es wichtig, dass niemand das ganze System bzw Netzwerk kennt, sondern jeder nur ein Teil des ganzen. Also wie eine Brieftasche. Jeder Mensch hat eine, mit geld darin. Den 5€ Schein habe ich von jemanden bekommen, wer ihn davor hatte brauch ich nicht wissen und wenn ich ihm weitergebe, weiß ich maximal wem ich den gegeben habe. Was danach mit dem Schein passiert ist nicht wichtig. Also muss ich diese Buchung auch nicht kennen.
Also erstmal bracuht jeder ein Wallet und eine eindeutige ID, diese ID wird im diesem System mit ein eindeutigen Key repräsentiert, auf basis von PGP - mit diesem Key wird auch das Wallet verschlüsselt. 

Da jeder nur ein Teil des Netzwerkes besitzt und überblicken kann, fällt ein Block in den alle Nodes und Überweisungen gespeichert sind weg. Damit aber eine buchung funktionieren kann, wird für jeden einzeilen Coin eine eigene Buchungsliste hinterlegt, somit ist jeder Coin selbst ein Block. 

Für weitere Informarionen siehe ImplVersion1000.md
