# Mobile App

Per Mobile App soll es möglich sein Coins zu Senden, per NFC und über das Internet per PGP. Wenn eine Session zu einen Anderen User geöffnet wird tauschen beide ihre Public Keys aus und beide senden sich eine Hallo Wold Nachrich mit dem Aktuellen Datum zu. Erst wenn diese Nachrich verifiziert ist, werden die eigentlichen Daten ausgetauscht. 
Wenn dies geschehen ist wird die session geschlossen und der Public Key auf beiden seiten gelöscht. 

Beim Sender wird die Buchung vermerkt und beim empfänger wird der Node in seiner Blockchain hinzugefügt. Der Sender kann nicht nachvollziehen was der Empfänger mit dem Coin macht. 

Zusätzlich wird der Coin der übertragen wurde, grau hinterlegt - bedeutet der ist nicht mehr in seinem Besitz. Die DB bzw die Private Blockchain der App wird per PGP verschlüsselt auf dem Gerät gespeichert, wenn möglich in einem gesicherten Bereich des Gerätes. Password sollte mindestens 35 Stellen lang sein evtl Biometrie. 

Beim ersten Start wird das Netzwerk ausgewählt dem man beitritt, eine Auswahl der vorhandenden Netzwerken sollte vorhanden sein. Man kann auch sein eignes Netzwerk Gründen - diese Funktion ist für profis, den nur Geräte im selben Netzwerk können mit einander agieren. 