# Use Case -Sandra
### ATGL: Ali, Iylmaz & Hetlinger


## Aufgabenstellung: 
Sandra hat eine körperliche Einschränkung und eine starke Sehbeeinträchtigung. Sie hat einen Rollstuhl, einen Laptop und ein SmartPhone. Sie kann Buchstaben nur in dreifacher Größe erkennen, benötigt hohen Kontrast und hat eine Rotsehschwäche (Protanopie). Sie würde gerne eine gewisse Autonomie zurückerlangen und ihre Umgebung (z.B. Licht, Jalousien, Musik) steuern zu können. Darüberhinaus würde sie gerne Klänge erzeugen können und sich die Zeit mit
Computerspielen vertreiben. Sie möchte gerne im Internet surfen oder am Smartphone mit ihren Freunden kommunizieren können.

## Vorhandene Funktionen:
- linker Arm: Daumen+Zeigefinger
- Kopfbewegung
- Mund/Lippen, Saugen/Pusten
- Sprache

## Verwendete Komponenten:
- Asterics Grid
- IrTrans (Fernsehersteuerung) 
- FlipMouse
- Fabi
- Sprachsteuerung (Siri)

## Wunsch
### 1. Umgebungssteuerung
- Steuerung Licht, Temperatur/Jalousien
- Fernseher 
### 2. Computer
- Internet surfen
- E-Mail schreiben
- Computerspiel spielen
### 3. SmartPhone bedienen
- SMS schreiben
- Anruf tätigen

# Lösung
## Umgebungssteuerung 
### AsTeRICs Grid
Für die Umgebungssteuerung wird ein zentraler OpenHab Server verwendet, um die Beleuchtung zu steuern sowie die Temperatur in der Wohnung des Schlafzimmers zu regeln. 
Desweiteren soll die Beschattung des Wohnzimmers gesteuert werden. 
Es wird das Asterics Grid verwendet, um diese Steuerungen durchzuführen. Die Tatsache, dass Sandra nur ihren Mund bzw. ihre Lippen bewegen kann, ermöglicht die Verwendung einer FlipMouse. 

### Grid-Konfiguration
![image](https://user-images.githubusercontent.com/82451150/150108903-94a94886-ede3-4edd-9bbf-32562a374b88.png)

Das Hauptseite -Grid beinhaltet zwei Zimmern und eine Mediensteuerung. Durch das Klicken mit einer Fabi-Button oder das Pusten in die FlipMouse, kann ein Grid ausgewählt werden. Dieses wird zusätzlich laut ausgesprochen und zu einer weiteren Seite des Grids navigiert. Zudem wird eine Asterics Aktion ausgeführt, welches Daten zu einem OpenHab Server sendet. 
Dabei ist es wichtig ein OpenHab Model in der Asterics Configuration Suite (ACS) hochzuladen und anschließend diese mit dem ARE zu verbinden. 
Für eine korrekte Verbindung mit dem OpenHab-Server im Smart Homes Labor ist im ACS der richtige Hostname unter Properties zu vergeben. (Siehe unten) 

![image](https://user-images.githubusercontent.com/82451150/150504706-97677766-b0d2-44f5-878c-5c8c323ee72c.png)

### Asterics Aktion bearbeiten
Um die Smart Homes Elemente durch einem Tastendruck oder durch das Pusten/Saugen in die FlipMouse zu steuern, muss die Asterics Aktion richtig konfiguriert werden.
Als erstes muss eine neue Asterics Aktion angelegt werden. Gleichzeitig sollte das ARE im Hintergrund laufen, damit das Model zum Grid heruntergeladen werden kann. Als nächstes wählt man die Komponente openHAB.1_c und sendet zum Port actionString die richtigen Befehle für die Steuerungen. Im untenstehenden Bild sind die verwendeten Befehle zu sehen.

![image](https://user-images.githubusercontent.com/82451150/150149946-65dae4a3-f71d-41f6-9b7f-2396d3143a0e.png)
![image](https://user-images.githubusercontent.com/82451150/150150656-a9532e06-b39e-4776-9414-d8710455f783.png)


Einpaar Items wie Temperatur Regelung und das Dimmbares Licht Ein-/Ausschalten sind nicht im Smart Lab integriert und daher nur in der Basic-UI ersichtlich. 

![image](https://user-images.githubusercontent.com/82451150/150325462-3e419ddd-273e-4ae3-8fab-4d7f54ec7910.png)

### Schlafzimmer -Grid
Im Schlafzimmer Grid können Beleuchtung oder Temperatur ausgewählt werden. Diese leiten zu einer weiteren Seite, wo die Steuerungen als Asterics Aktionen durchgeführt werden. 
Aufgrund Sandras Sehschwäche wurden große Felder erstellt.

![image](https://user-images.githubusercontent.com/82451150/150139409-b61e4c32-d748-4956-baba-a5e454f33a92.png)
  
![image](https://user-images.githubusercontent.com/82451150/150140079-42482fd5-51b6-45bd-bb80-f9966c6eb383.png)


### Temperatur -Grid
Im Temperatur Grid kann zwischen 5, 10, 15 und 22 Grad ausgewählt werden. Weiters gibt es noch die Option eine automatische Nachtabsenkung zu aktivieren oder zu deaktivieren. 

![image](https://user-images.githubusercontent.com/82451150/150153535-753db912-e2d4-4fb7-bf0d-50207b566115.png)

### Mediensteuerung -Grid
Mit diesem Grid kann der Fernseher gesteuert werden. Mittels IrTrans Aktuator wurden Infrarot Signale aus der Fernbedienung eingelesen und abgespeichert. Anschießend ... <todo>

### Wohnzimmer -Grid 
Im Wohnzimmer Grid können die Jalousinen hinauf und hinunter navigiert werden. Auch hier musste das richtige Befehl zu dem Port "ActionString" versendet werden, um das gewünschte Ziel zu erreichen.
  
![image](https://user-images.githubusercontent.com/82451150/150153827-4815036a-c410-49bd-8f10-3ce8d6d902f6.png)


## Computer
### Accessibility Settings
Für den Wunsch Sandras Computerspiele spielen zu können und Emails zu schreiben wurde ein Windows 11 Laptop verwendet.
Unter dem Feld Barrierefreiheit "Sehen" wurde die Bildschirmlupe um 300% vergrößert und ein Rot-Grün Farbfilter aktiviert. Zudem wurde ebenfalls die Sprachausgabe aktiviert. 
Für eine einfachere Handhabung des Kommunizierns werden Emails über die Sprachassistentin Siri mittels SmartPhones versendet. Als Alternative kann auch der Computer verwendet werden. 

![image](https://user-images.githubusercontent.com/82451150/150518950-d1e30a60-6a0b-42f6-bd54-fc41daca9b17.png)
![image](https://user-images.githubusercontent.com/82451150/150518996-3b571642-957a-4468-bc69-5a3fa521a465.png)
![image](https://user-images.githubusercontent.com/82451150/150519020-946b1b24-c578-4f50-952a-4fc75320e31b.png)

  
## Eingabegeräte
### FlipMouse
### Fabi
  
## SmartPhone bedienen mit Siri
