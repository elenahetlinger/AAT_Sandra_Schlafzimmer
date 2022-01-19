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

### Hauptseite
Die Hauptseite -Grid beinhaltet zwei Zimmern und eine Mediensteuerung. Durch das Klicken mit einer Fabi-Button oder das Pusten in die FlipMouse, kann ein Grid ausgewählt werden. Dieses wird zusätzlich laut ausgesprochen und zu einer weiteren Seite des Grids navigiert. 
Diese Einstellungen wurden bei "Aktionen bearbeiten" durchgeführt.
![image](https://user-images.githubusercontent.com/82451150/150108903-94a94886-ede3-4edd-9bbf-32562a374b88.png)
![image](https://user-images.githubusercontent.com/82451150/150138485-daa057fb-a8fa-4d2b-a6df-7d214505008a.png)

### Schlafzimmer -Grid
Im Schlafzimmer Grid können Beleuchtung oder Temperatur ausgewählt werden. Diese leiten zu einer weiteren Seite, wo schließlich die Steuerungen als Asterics Aktionen durchgefüht werden. 
![image](https://user-images.githubusercontent.com/82451150/150139409-b61e4c32-d748-4956-baba-a5e454f33a92.png)
Aufgrund Sandras Sehschwäche wurde große Felder erstellt. 
![image](https://user-images.githubusercontent.com/82451150/150140079-42482fd5-51b6-45bd-bb80-f9966c6eb383.png)






# Computer
# SmartPhone bedienen
