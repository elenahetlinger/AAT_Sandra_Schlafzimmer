# Use Case - Sandra
### ATGL: Ali, Ylmaz & Hetlinger


## Aufgabenstellung: 
Sandra hat eine körperliche Einschränkung und eine starke Sehbeeinträchtigung. Sie hat einen Rollstuhl, einen Laptop und ein SmartPhone. Sie kann Buchstaben nur in dreifacher Größe erkennen, benötigt hohen Kontrast und hat eine Rotsehschwäche (Protanopie). Sie würde gerne eine gewisse Autonomie zurückerlangen und ihre Umgebung (z.B. Licht, Jalousien, Musik) steuern zu können. Darüberhinaus würde sie gerne Klänge erzeugen können und sich die Zeit mit
Computerspielen vertreiben. Sie möchte gerne im Internet surfen oder am Smartphone mit ihren Freunden kommunizieren können.

## Vorhandene Funktionen:
- linker Arm: Daumen+Zeigefinger
- Kopfbewegung
- Mund/Lippen, Saugen/Pusten
- Sprache

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

## Verwendete Komponenten:
- Asterics Grid
- IrTrans (Fernsehersteuerung) 
- Sprachsteuerung (Siri)
- OpenHab

## Eingabegeräte
### FlipMouse
Was ein FlipMouse ist findet man in dem Link: https://www.asterics-foundation.org/projekte-2/flipmouse/

Die Einstellungen von FlipMouse 
![image](https://user-images.githubusercontent.com/82451150/150942130-8e2d975d-9cd0-4c8d-a70d-2fc108b7f34e.jpeg)

### Fabi - Flexible Assistive Button Interface
Was ein FABI ist findet man in dem Link: https://www.asterics-foundation.org/projects/fabi/

Die Einstellungen von FABI
![image](https://user-images.githubusercontent.com/82451150/150942191-6641a9e6-45f5-45bf-b5fd-f33d19b22e19.jpeg)

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
Mit diesem Grid kann der Fernseher gesteuert werden. 
Mittels IrTrans Aktuator wurden Infrarot Signale aus der Fernbedienung eingelesen und abgespeichert. 
Auch hier musste das richtige Befehl zu dem Port "ActionString" versendet werden, um das gewünschte Ziel zu erreichen.
![image](https://user-images.githubusercontent.com/82451150/150939912-f62d167d-b206-42e0-aee5-ce788530f561.png)
![image](https://user-images.githubusercontent.com/82451150/150940311-24cd13a1-a19d-4ded-a892-ac19fe3cd101.png)
![image](https://user-images.githubusercontent.com/82451150/150940322-1dac7bba-7d4b-474d-b9ee-081249e47909.png)
![image](https://user-images.githubusercontent.com/82451150/150938843-50166c19-874c-4d44-b134-dfdb0a5bc6fe.png)
![image](https://user-images.githubusercontent.com/82451150/150940333-902dd9e5-5a0b-4d63-85c7-f0790c8740d4.png)


### Wohnzimmer -Grid 
Im Wohnzimmer Grid können die Jalousinen hinauf und hinunter navigiert werden. Auch hier musste das richtige Befehl zu dem Port "ActionString" versendet werden, um das gewünschte Ziel zu erreichen.
  
![image](https://user-images.githubusercontent.com/82451150/150153827-4815036a-c410-49bd-8f10-3ce8d6d902f6.png)

## Computer
### Accessibility Settings
Für den Wunsch Sandras Computerspiele spielen zu können und Emails zu schreiben wurde ein Windows 11 Laptop verwendet.
Unter dem Feld Barrierefreiheit "Sehen" wurde die Bildschirmlupe um 300% vergrößert und ein Rot-Grün Farbfilter aktiviert. Zudem wurde ebenfalls die Sprachausgabe aktiviert. 
Für eine einfachere Handhabung des Kommunizierns werden Emails über die Sprachassistentin Siri mittels SmartPhones versendet. Als Alternative zum Versenden von Mails kann auch der Computer verwendet werden. Hierfür wird die Bildschirmtastatur mittels FlipMouse angewendet.

![image](https://user-images.githubusercontent.com/82451150/150518950-d1e30a60-6a0b-42f6-bd54-fc41daca9b17.png)
![image](https://user-images.githubusercontent.com/82451150/150518996-3b571642-957a-4468-bc69-5a3fa521a465.png)
![image](https://user-images.githubusercontent.com/82451150/150519020-946b1b24-c578-4f50-952a-4fc75320e31b.png)

### Computerspiel
Hier Wird ein Computerspiel gespielt nur mit die 2 Buttons von Fabi
![image](https://user-images.githubusercontent.com/82451150/150941310-f68e9740-6560-44e3-8e5f-f93db2366129.jpeg)

## SMS schreiben und Anruf tätigen mittels Siri
Das Apple Siri ist eine Sprachassistentin, der für Sandra perfekt geeignet ist, um Anrufe zu tätigen oder Emails zu verschicken. In den Einstellungen muss das erste Feld "Auf Hey Siri achten" aktiviert sein, um nur über die Sprache an Siri Befehle zu übermitteln.
Im untenstehenden Video ist die Kommunikation mit Siri erkennbar.
  
![image](https://user-images.githubusercontent.com/82451150/150521434-c37ad077-de36-483d-9412-56acc774e2cc.png) 

Hier kann man sehen wie Siri verwendet wird um einen Anruf zu tätigen und ein SMS zum schreiben.

https://user-images.githubusercontent.com/82451150/150940882-3ecf04d8-4103-4a96-99e5-6f6bac8f750d.mp4

https://user-images.githubusercontent.com/82451150/150940897-e765220e-fa53-482a-b873-101674127b6f.mp4


# Ergebnis FitsTask
![seq_sum3](https://user-images.githubusercontent.com/82451150/150532914-944404b7-801e-4000-9805-7f27d12a3c7b.JPG)

