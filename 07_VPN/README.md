# Leitfragen zum Thema VPN

**Ausgangslage**
***
Ein Unternehmen hat einen veralteten Internetzugang mit einer Übertragungsrate von 50 Mbit/s im Download und 5 Mbit/s im Upload mit ADSL. Die Firma produziert Kaffeemaschinen in einer städtischen Gegend in der Schweiz. Das Marketing benutzt moderne Webapplikationen mit viel Multimediaanwendungen und ein Shop für Endkunden ist ebenfalls vorhanden. Alle Mitarbeiten-den benutzen Mail und Browserapplikationen. Die Firma hat 90 Internetnutzer.

Eine Firewall ist nicht vorhanden und die Server stehen alle beim Provider.


## **Aufgabe**

Vergleichen Sie folgende VPN-Lösungen für ihren Internetanschluss:  

- Hardwarelösung (Cisco-ASA oder Ähnliches) 
- VPN-Service des Providers 
- PC-Lösung mit Windows und Linux.  

Welche Vergleichskriterien finden Sie, welche sind für welche Einsatzfälle wie wichtig? 

Diskutieren Sie einige „typische Fälle“ und vergleichen Sie. 


## **1 Vergleich**

### **Vergleich verschiedener VPN-Lösungen**

![grafik](https://user-images.githubusercontent.com/62818267/135760829-9faebc6e-3e36-4ba0-9556-78431d75e56f.png)


### **Kriterien**
Form
- Welche Form hat der VPN-Server,Hardware-Appliance oder Software?

Kosten 

- Wie hoch sind die Kosten? 

Durchsatz
- Wie hoch ist der VPN-Tunnel Durchsatz?

VPN-Typen 

- Welche Formen von VPN-Typen werden unterstützt? Site-To-Site, Client-To-Site

Max. Anzahl Peers

- Wie viele Peers (Anzahl Clients) können sich mit dem VPN verbinden?

VPN-Client

- Gibt es einen VPN-Client und wie einfach ist dieser zu bedienen?

Management

- Wie wird der VPN gemanaged? 




## **2 Typische Fälle**

Nachdem ich mir Gedanken über Vergeleichskriterien angeschaut habe, habe ich diese auf "Typische Fälle" bei VPN-Verbindungen angewendet und geschaut, was wo wie wichtig ist. 


### **VPN für die Verbindung mehrerer Standorte**

Beispielsweise die Verbindung zwischen einer Cloud wie Azure und dem On-Premise Netzwerk oder eine Verbindung mehrerer Standorte mit dem Firmennetzwerk.  

Für solch eine Verbindung braucht es eine Site-To-Site VPN. Man braucht dafür zwei Endpunkte, welche eine Site-To-Site VPN zulassen. Das kann eine Firewall auf jeder Seite sein, mit welcher ein IPsec Site-To-Site VPN aufgebaut wird. 

Ebenfalls wichtig ist meist ein hoher Durchsatz, da normalerweise der gesamte Netzwerktraffic über den VPN-Tunnel läuft und es im Netzwerk nur einen Internet-Breakout gibt. Durch dieses Netzwerk läuft also alles von VOIP, zu internem Traffic zu Internet-Browsen. 

Da durch den VPN-Tunnel alle Daten laufen ist eine gute Ausfallsicherheit sehr wichtig. Am besten ist hier also ein Produkt, welches auf genau solch eine Aufgabe zugeschnitten ist. 

Zusammenfassung:
- Site-To-Site VPN 
- Hoher Durchsatz
- Gute Ausfallsicherheit



### **VPN für das Umgehen von Geo-Blocking oder das täuschen der eigenen IP-Adresse**
Um Dienste aus anderen Ländern zu nutzen oder aus Gründen der Privatsphäre. 

In diesem Fall braucht es ebenfalls eine Point-To-Site VPN-Verbindung. Für das Umgehen von Geo-Blocking ist ein public-VPN-Provider wie NordVPN oder ProtoonVPN am einfachsten, da diese viele VPN-Server rund im die Welt haben. 

Ebenfalls ist eine einfache Bedienbarkeit des VPN-Clients wichtig, da diese von Usern genutzt wird. 

Zusammenfassung:
- Point-To-Site VPN 
- Einfache bedienbarkeit

### **VPN für die Verbindung in ein bestimmtes Netzwerk über eine gesicherte Verbindung** 
Ein Systemadministrator oder ein Benutzer braucht eine Sichere Verbindung zum Firmennetzwerk, um dieses auch von überall aus zu erreichen. 

Hier braucht es eine Point-To-Site VPN. Es gibt also einen Client der sich mit einem Netzwerk über einen gesicherten Tunnel verbindet. Auf dem Client installiert man eine VPN-Client-Software. 

Ebenfalls ist eine einfache Bedienbarkeit des VPN-Clients wichtig, da diese von Usern genutzt wird. 

Zusammenfassung:
- Point-To-Site VPN 
- Einfache bedienbarkeit


## **3 Begriffserklärung**

- **Site-To-Site**: Site-To-Site bedeutet im Bezug auf VPNs, dass damit zwei Netzwerke verbunden werden können. So kann ein externes Rechenzentrum oder ein externer Standort mit dem Firmennetzwerk verbunden werden. Die wird über den Router/die Firewall realisiert. 

- **Point-To-Site / Client-To-Site**: Bei einer Client-To-Site VPN wird nur ein Client mit dem VPN-Netzwerk verbunden. Hierfür wird ein VPN-Client auf Z.B. Windows installiert. 

- **VPN-Peers**: Ein VPN-Peer ist ein "Client". Die maximale Anzahl Peers bestimmt also, wieviele  Clients gleichzeitig mit dem VPN verbunden sein können. 
