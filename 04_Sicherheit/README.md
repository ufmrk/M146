# Leitfragen zum Thema Sicherheit

**Ausgangslage**
***
Ein Unternehmen hat einen veralteten Internetzugang mit einer Übertragungsrate von 50 Mbit/s im Download und 5 Mbit/s im Upload mit ADSL. Die Firma produziert Kaffeemaschinen in einer städtischen Gegend in der Schweiz. Das Marketing benutzt moderne Webapplikationen mit viel Multimediaanwendungen und ein Shop für Endkunden ist ebenfalls vorhanden. Alle Mitarbeiten-den benutzen Mail und Browserapplikationen. Die Firma hat 90 Internetnutzer.

Eine Firewall ist nicht vorhanden und die Server stehen alle beim Provider.


**Aufgabe**
Die Firma entscheidet sich, dass die Server alle inhouse stehen sollen.

Welche Anforderungen an die Sicherheit gemäss ISO 27000 sind zu beachten?
Bitte stellen Sie der Klasse ein sinnvolles Sicherheitskonzept für diesen Anwendungsfall vor.

Beachten Sie, dass es technische und nicht technische Massnahmen geben kann.


# **1 Anforderungen nach ISO 27000** 
ISO 27000 hilft dabei ein Framework für Sicherheit zu schaffen und zu standardisieren. 

**Grundlegende Anforderungen**

Anforderungen 

- Informationssicherheit 
- Physische Sicherheit von Dokumenten/Zugängen etc. 
- Digitale Sicherheit von Informationen

Bei ISO 27000 gibt es drei generelle Ziele zur Informationssicherheit. 
Schutzziele:

- Verfügbarkeit 
- Integrität 
- Authentizität


# **2 Nicht technische Massnahmen**

## **1 Einführung eines ISMS** 
- Regelmässige Sicherheitsaudits




# **3 Technische Massnahmen** 
In diesem Teil haben wir uns technische Massnahmen zur Sicherheit überlegt. 


## **Übersicht über die technischen Massnahmen** 
- Firewall mit Proxyfunktion 
- Netzwerksegmentierung 
- Doppelte Internetanbindung 
- Verschlüsselung wo es geht
- Sinnvoller Aufbau der Server

## **1 Aufbau des Netzwerkes**

**Redundante Firewall mit Proxy Funktion**
- Diese Firewalls filtern HTTPS Traffic per Proxy
- Firrewalls mit SPI und DPI

**Redundanter Core-Switch**
- Der Core-Switch ist sehr wichtig im Netzwerk, da der gesamte Netzwerktraffic und alle VLANs über diesen Switch geroutet werden

**Netzwerksegmentierung** 
- Wir nutzen VLANs, welche auf dem Core-Switch geroutet werden können
- So kann die Server Umgebung von den Usern getrennt werden
- Gleichzeitig kann aber z.B. VOIP oder Internet Traffic vom Webserver priorisiert werden
Verfügbarkeit: Webservertraffic und VOIP haben priorität
Authentiziät: Traffic kommt nur dorthin, wo er auch hinsoll
Integrität: Es ist schwieriger den Netzw erktraffic zu manipulieren 

**Trennung des WLAN in Guest und Internal**
- Das Guest läuft auf einem anderen VLAN 
- Beide WLANs haben nur Zugriff zum Internet und nicht zu internen Ressourcen
- Dadurch sind die beiden Netzwerke getrennt 

## **2 Aufbau der Server-Infrastruktur**
Bei den Servern lohnt es sich zu überlegen, wie man diese Infrastruktur am besten aufbaut

**Active Directory**
- Wir nutzen zwei Domainencontroller für eine fortlaufende Replikation 
- Authentizität: Zugriffsverwaltung ist zentral 

**Rredunante Domainencontroller**
- Verfügbarkeit: Redundante Domainencontroller ermöglichen Replikation und somit bessere Aussfallsicherheit

**Redundante Webserver**
- Wir nutzen zwei Instanzen des Webservers
- Der Traffic wird über einen Reverse-Proxy gesteuert
- Die Webserver nutzt für sein Backend eine SQL-Datenbank auf dem SQL-Server. 

**Reverse Proxy**
- Um die Last auf den Webservern auszugleichen, nutzen wir einen Reverse Proxy 

**Mailserver** 
- Als Mailserver nutzen wir Exchange Server
- Dieser hat seine Datenbanken auf dem SQL-Server

**SQL Server für Datenbanken** 
- Um einfache Backups und Restores der Datenbanken vom Exchange und Webserver zu machen, setzen wir auf einen dedizierten Datenbankserver
- Der SQL-Server ermöglicht zudem, dass die Sicherheit der Datenbanken zentral gemanged werden kann 
- 

**Virtualisierungscluster**
- Hier nutzen wir zwei physische Server, damit die Verfügbarkeit sehr hoch gehalten werden kann
- Live-Migration jederzeit möglich
- Das Virtualisierungscluster nutzt kein zentrales SAN, sondern speichert die VMs lokal

**Backup**
- Es werden regelmässig full- und incremental Backups gemacht

## **3 Weitere technische Massnahmen**
Verschlüsselung: 
- Jeglicher Speicher ist verschlüsselt 
- Netzwerktraffic verschlüsselt (WPA, HTTPS, SFTP)
- Authentifizierung durch Benutzername und Passwörter 
- Authentifizierung durch Zwei-Faktor-Authentifzierung und Smart-Cards


