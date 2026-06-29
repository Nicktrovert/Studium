# Inhaltsverzeichnis
### 1. Grundlagen
- Internet und Protokolle
- Schichtenmodell
- Kapselung
- Paketvermittlung vs. Leitungsvermittlung
- Verzögerungen
- Durchsatz
- Netzwerkarchitekturen

---
### 2. Anwendungsschicht
- Client-Server und P2P
- HTTP
- Cookies
- Web Caching
- DNS
- DHCP
- E-Mail
- CDN (falls relevant)

---
### 3. Transportschicht
- UDP
- TCP
- Ports
- Multiplexing/Demultiplexing
- Three-Way Handshake
- Four-Way Termination
- Sequenznummern
- ACKs
- Sliding Window
- Flusskontrolle
- Staukontrolle
- Slow Start
- AIMD
- Fast Retransmit

---
### 4. Netzwerkschicht
- IPv4 Header
- Fragmentierung
- MTU
- CIDR
- Routing
- Forwarding
- Longest Prefix Match
- Dijkstra
- Link State
- Distance Vector
- NAT
- ICMP

---
### 5. Sicherungsschicht
- Ethernet
- MAC-Adressen
- Switches
- ARP
- Broadcast
- CRC
- Parität
- Fehlererkennung
- Fehlerkorrektur

---
### 6. Klausurwissen

---
# Kapitel 1 – Grundlagen der Rechnernetze

(Basierend auf _Dako 01 – Einführung_ sowie den Grundlagen der weiteren Folien.)

---

# 1. Was ist das Internet?

Das Internet ist **kein einzelnes Netzwerk**, sondern ein **Netzwerk aus vielen miteinander verbundenen Netzwerken** ("Network of Networks").

Sein Zweck besteht darin, **Daten zwischen Endsystemen weltweit auszutauschen**.

Beispiele für Internetanwendungen:
- Web (HTTP/HTTPS)
- E-Mail
- Videostreaming
- Gaming
- Cloud
- VoIP
- IoT

---
# 2. Was ist ein Protokoll?

Ein **Protokoll** legt fest,
- wie Nachrichten aufgebaut sind,
- in welcher Reihenfolge sie gesendet werden,
- welche Aktionen nach Empfang ausgeführt werden.

Man kann es sich wie eine Sprache vorstellen.

Wenn beide Seiten dieselben Regeln kennen, funktioniert die Kommunikation.

### Beispiel

HTTP:
```
Client
GET /index.html

↓

Server
HTTP/1.1 200 OK
...
```

Ohne gemeinsames Protokoll könnten Client und Server nicht miteinander kommunizieren.

---
# 3. Schichtenmodell

Die Internetprotokolle sind in Schichten organisiert.

Jede Schicht hat eine klar definierte Aufgabe.
```
Anwendungsschicht
↑
Transportschicht
↑
Netzwerkschicht
↑
Sicherungsschicht
↑
Bitübertragungsschicht
```

Jede Schicht
- bietet der darüberliegenden Schicht einen Dienst an,
- nutzt den Dienst der darunterliegenden Schicht.

---
# Aufgaben der einzelnen Schichten

## Anwendungsschicht

Kommunikation zwischen Anwendungen.

Beispiele:
- HTTP
- DNS
- DHCP
- SMTP

---
## Transportschicht

Kommunikation zwischen Prozessen.

Aufgaben:
- Ports
- Multiplexing
- Flusskontrolle
- Zuverlässigkeit (TCP)
- Reihenfolge

Protokolle:
- TCP
- UDP

---

## Netzwerkschicht

Transport von Paketen durch das gesamte Internet.

Aufgaben:
- Routing
- Weiterleitung (Forwarding)
- Fragmentierung
- IP-Adressen

Protokoll:
- IPv4

---

## Sicherungsschicht

Kommunikation zwischen **zwei direkt verbundenen Geräten**.

Aufgaben:
- MAC-Adressen
- Ethernet
- Fehlererkennung (CRC)
- Switches
- ARP

---
## Bitübertragungsschicht

Überträgt lediglich Bits über das Medium.

Beispiele:
- Kupferkabel
- Glasfaser
- WLAN-Funksignal

Diese Schicht wird laut Vorlesung kaum behandelt.

---
# 4. Kapselung (Encapsulation)

Jede Schicht fügt ihren eigenen Header hinzu.
```
Anwendungsdaten
```
↓
```
TCP Header
Anwendungsdaten
```
↓
```
IP Header
TCP Header
Anwendungsdaten
```
↓
```
Ethernet Header
IP Header
TCP Header
Anwendungsdaten
CRC
```

Beim Empfänger passiert das Gegenteil (Entkapselung).

---
## Merksatz

**Jede Schicht kennt nur ihren eigenen Header.**

---
# 5. Endsysteme und Router

## Endsysteme (Hosts)

Endgeräte, auf denen Anwendungen laufen.

Beispiele:
- PC
- Laptop
- Smartphone
- Server

Sie besitzen den vollständigen Protokollstack.

---
## Router

Router verbinden verschiedene Netzwerke.

Sie arbeiten hauptsächlich auf der **Netzwerkschicht (Layer 3)**.

Aufgaben:
- Weiterleitung
- Routing
- TTL reduzieren
- Fragmentierung (IPv4)

Router interessieren sich **nicht für HTTP oder TCP-Daten**, sondern hauptsächlich für den IP-Header.

---
# 6. Paketvermittlung vs. Leitungsvermittlung

## Leitungsvermittlung (Circuit Switching)

Vor der Kommunikation wird eine feste Verbindung aufgebaut.

Beispiel:
Telefonnetz.

Eigenschaften:
✔ garantierte Bandbreite
✔ feste Route
✖ Ressourcen bleiben reserviert

---
## Paketvermittlung (Packet Switching)

Daten werden in viele kleine Pakete zerlegt.

Jedes Paket kann unabhängig durchs Netzwerk laufen.

Eigenschaften:
✔ bessere Auslastung
✔ flexibler
✖ Verzögerungen
✖ Paketverlust möglich
✖ unterschiedliche Wege möglich

Das Internet verwendet **Paketvermittlung**.

---
## Klausurfrage

Welche Vorteile besitzt Paketvermittlung?

Antwort:
- bessere Ressourcenauslastung
- mehrere Nutzer teilen sich Leitungen
- keine Reservierung nötig

---

# 7. Nachrichtenarten

## Unicast
1 Sender
↓
1 Empfänger

Normaler Internetverkehr.

---
## Broadcast

1 Sender
↓
Alle Geräte im lokalen Netzwerk

Beispiel:
- ARP
- DHCP Discover

---

## Multicast
1 Sender
↓
Mehrere ausgewählte Empfänger

Beispiel:
- IPTV
- Videokonferenzen

---

# 8. Wichtige Begriffe

|Begriff|Bedeutung|
|---|---|
|Host|Endgerät|
|Router|verbindet Netzwerke|
|Switch|verbindet Geräte innerhalb eines LAN|
|Link|direkte Verbindung zwischen zwei Geräten|
|Paket|Netzwerkschicht|
|Segment|Transportschicht|
|Frame|Sicherungsschicht|

---

# 9. Typische Klausurfragen

## Welche Schicht macht was?

|Aufgabe|Schicht|
|---|---|
|HTTP|Anwendung|
|DNS|Anwendung|
|DHCP|Anwendung|
|TCP|Transport|
|UDP|Transport|
|Routing|Netzwerk|
|Forwarding|Netzwerk|
|IP|Netzwerk|
|Ethernet|Sicherung|
|ARP|Sicherung|

---

## Welche Geräte arbeiten auf welcher Schicht?

|Gerät|Schicht|
|---|---|
|Switch|Sicherungsschicht (Layer 2)|
|Router|Netzwerkschicht (Layer 3)|
|Host|alle Schichten|

---

# 10. Merksätze für die Prüfung

- **Internet = Netzwerk von Netzwerken.**
- **Protokolle definieren Format, Reihenfolge und Reaktionen auf Nachrichten.**
- **Jede Schicht nutzt die darunterliegende und bietet der darüberliegenden einen Dienst an.**
- **TCP-Segmente → IP-Pakete → Ethernet-Frames.**
- **Router verbinden Netzwerke, Switches verbinden Geräte innerhalb eines Netzwerks.**
- **Das Internet verwendet Paketvermittlung, nicht Leitungsvermittlung.**
- **Broadcast bleibt auf das lokale Netz beschränkt und wird nicht von Routern weitergeleitet.**

---
# Kapitel 2 – Anwendungsschicht

(Basierend auf _Dako 02 – Anwendungsschicht_)

---

# 1. Aufgabe der Anwendungsschicht

Die Anwendungsschicht stellt Netzwerkdienste für Programme bereit.

Sie legt fest, **wie Anwendungen miteinander kommunizieren**.

Die Anwendungsschicht nutzt dabei die Dienste der Transportschicht (TCP oder UDP).

Beispiele:
- HTTP
- HTTPS
- DNS
- DHCP
- SMTP
- POP3
- IMAP
- FTP

---

# 2. Client-Server-Modell

Die meisten Internetdienste arbeiten nach dem **Client-Server-Prinzip**.

## Client
- fordert einen Dienst an
- startet die Kommunikation
- besitzt meist eine wechselnde IP-Adresse

Beispiele:
- Browser
- E-Mail-Programm

---
## Server
- bietet einen Dienst an
- wartet ständig auf Anfragen
- besitzt meist eine feste IP-Adresse oder Domain

Beispiele:
- Webserver
- DNS-Server
- Mailserver

---
### Beispiel
```text
Browser
   │ HTTP GET
   ▼
Webserver
   │ HTTP Response
   ▼
Browser
```

---
## Vorteile
- einfache Verwaltung
- leicht skalierbar
- zentrale Datenhaltung

## Nachteile
- Single Point of Failure
- hohe Last auf dem Server

---

# 3. Peer-to-Peer (P2P)

Hier existiert **kein zentraler Server**.

Jeder Teilnehmer kann gleichzeitig
- Client
- Server
sein.

Beispiele
- BitTorrent
- ältere Skype-Versionen

---
## Vorteile
- hohe Skalierbarkeit
- Last verteilt sich
- keine zentrale Infrastruktur notwendig

## Nachteile
- schwieriger zu verwalten
- wechselnde IP-Adressen
- Sicherheit schwieriger

---
# 4. Socket

Ein **Socket** ist die Schnittstelle zwischen Anwendung und Betriebssystem.

Über den Socket werden Daten verschickt oder empfangen.

---

## Identifikation
UDP:
```text
(IP-Adresse, Ziel-Port)
```

TCP:
```text
(Quell-IP,
Quell-Port,
Ziel-IP,
Ziel-Port)
```

TCP benötigt das vollständige 4-Tupel, da mehrere Verbindungen zum selben Server gleichzeitig existieren können.

---
# 5. Ports

Da auf einem Rechner viele Programme gleichzeitig laufen, reicht die IP-Adresse allein nicht aus.

Der **Port identifiziert den Prozess**.

---
## Portbereiche

|Bereich|Bedeutung|
|---|---|
|0–1023|Well-Known Ports|
|1024–49151|Registered Ports|
|49152–65535|Dynamische (Ephemeral) Ports|

---
## Wichtige Ports

|Port|Protokoll|
|--:|---|
|20/21|FTP|
|22|SSH|
|25|SMTP|
|53|DNS|
|67/68|DHCP|
|80|HTTP|
|110|POP3|
|143|IMAP|
|443|HTTPS|

---
## Klausurwissen

Server besitzen meist feste Ports.

Clients verwenden normalerweise **zufällige hohe Ports (Ephemeral Ports)**.

---
# 6. HTTP

HTTP (**HyperText Transfer Protocol**) dient zur Übertragung von Webseiten.

Eigenschaften:
- Client-Server
- Request-Response
- nutzt TCP
- Standardport 80

HTTPS nutzt ebenfalls HTTP, allerdings verschlüsselt über TLS auf Port 443.

---
## HTTP Request

Beispiel:
```http
GET /index.html HTTP/1.1
Host: example.com
```

---
## HTTP Response
```http
HTTP/1.1 200 OK
Content-Type: text/html
```

---
## Wichtige Methoden

|Methode|Bedeutung|
|---|---|
|GET|Ressource abrufen|
|POST|Daten senden|
|HEAD|Nur Header abrufen|

---
## Wichtige Statuscodes

|Code|Bedeutung|
|--:|---|
|200|OK|
|301|Permanent Redirect|
|304|Not Modified|
|400|Bad Request|
|403|Forbidden|
|404|Not Found|
|500|Internal Server Error|

---
# 7. Zustandslosigkeit (Stateless)

HTTP speichert **keinen Sitzungszustand**.

Jede Anfrage ist unabhängig.

Der Server weiß ohne zusätzliche Mechanismen nicht, wer zuvor bereits verbunden war.

---
## Konsequenz

Ohne Hilfsmittel müsste sich ein Benutzer bei **jeder Anfrage** erneut anmelden.

---
# 8. Cookies

Cookies lösen dieses Problem.

Der Server speichert eine kleine Kennung beim Client.

Bei jeder weiteren Anfrage sendet der Browser den Cookie automatisch mit.
```text
Client
GET
↓
Server

Set-Cookie: abc123
↓
Client

Cookie gespeichert
↓
Nächster Request

Cookie: abc123
```

---
## Verwendung
- Login
- Warenkorb
- Spracheinstellungen
- Tracking

---

## Klausurfalle
Cookies existieren **nicht**, weil HTTP unsicher ist.
Cookies existieren, weil **HTTP zustandslos** ist.
Diese Aussage kam bereits in einer Beispielklausur vor.

---

# 9. Persistentes HTTP

Früher:

Für jede Datei wurde eine neue TCP-Verbindung aufgebaut.

Heute:

Eine TCP-Verbindung wird mehrfach genutzt.

Vorteile:
- weniger Overhead
- geringere Verzögerung
- weniger Verbindungsaufbauten

---
## Klausurbeispiel

Eine Webseite enthält:
- HTML
- 4 Bilder

Davon:
- HTML + 2 Bilder auf Server A
- 1 Bild auf Server B
- 1 Bild auf Server C

Mit persistentem HTTP:
→ **3 TCP-Verbindungen**
→ **5 HTTP-GET-Anfragen**

Genau dieser Aufgabentyp findet sich in einer der Beispielklausuren.

---

# 10. Web-Caching

Ein Cache speichert häufig verwendete Webseiten.

Beim nächsten Abruf muss die Seite nicht erneut vom Ursprungsserver geladen werden.

Vorteile:
- geringere Latenz
- weniger Netzlast
- weniger Serverlast

---
# 11. Conditional GET

Der Browser fragt:

> Hat sich die Datei seit Zeitpunkt X geändert?

```http
If-Modified-Since:
```

Server antwortet:

**Nicht geändert**
↓
```http
304 Not Modified
```

Es werden **keine Daten erneut übertragen**.

---
## Vorteile
- spart Bandbreite
- schneller Seitenaufbau

---
# 12. DNS

DNS (**Domain Name System**) übersetzt **Domainnamen** in **IP-Adressen**.

Beispiel:
```text
google.com
↓
142.250.x.x
```

Menschen merken sich Namen.

Computer benötigen IP-Adressen.

---

## Hierarchie
```text
Root
↓
Top Level Domain (.de)
↓
uni-emden.de
↓
www.uni-emden.de
```

---
# 13. Iterative DNS-Auflösung

Wenn kein Cache vorhanden ist:
1. Client → lokaler DNS-Resolver
2. Resolver → Root-Server
3. Root → .de-Server
4. Resolver → .de-Server
5. .de → autoritativer Server
6. Resolver → autoritativer Server
7. Autoritativer Server → IP-Adresse
8. Resolver → Client

---
## Klausur

Eine der Beispielklausuren verlangt genau diese Abfolge grafisch mit allen beteiligten Servern.

---

# 14. DHCP

DHCP vergibt automatisch:
- IP-Adresse
- Subnetzmaske
- Gateway
- DNS-Server

---

## Ablauf (DORA)
```text
Discover
↓
Offer
↓
Request
↓
ACK
```

Merksatz:
**DORA**

---

## Broadcast

Zu Beginn kennt der Client weder seine eigene IP-Adresse noch den DHCP-Server.

Deshalb wird **DHCP Discover per Broadcast** gesendet.

---
# 15. Wichtige Merksätze
- Anwendungsschicht stellt Dienste für Anwendungen bereit.
- Port = Prozess.
- IP = Rechner.
- HTTP nutzt TCP.
- HTTPS = HTTP + TLS.
- HTTP ist zustandslos.
- Cookies speichern Sitzungsinformationen.
- Persistentes HTTP verwendet eine TCP-Verbindung für mehrere Requests.
- Web-Caching reduziert Server- und Netzlast.
- Conditional GET liefert oft **304 Not Modified**.
- DNS übersetzt Domain → IP.
- DHCP vergibt Netzwerkkonfiguration automatisch.
- DHCP Discover und ARP verwenden Broadcast.

---
# Klausurwissen (unbedingt können)
✓ Unterschiede Client-Server ↔ P2P
✓ Wichtige Portnummern (22, 53, 67/68, 80, 443)
✓ HTTP-Ablauf
✓ Warum Cookies existieren
✓ Persistentes HTTP
✓ Web-Caching
✓ DNS-Hierarchie
✓ Iterative DNS-Auflösung
✓ DHCP (DORA)

---
# Kapitel 3 – Transportschicht

(Basierend auf _Dako 03 – Transportschicht_)

---

# 1. Aufgabe der Transportschicht
Die Transportschicht sorgt für die **Ende-zu-Ende-Kommunikation zwischen Prozessen**.

Die Netzwerkschicht bringt Pakete nur bis zum Zielrechner.

Die Transportschicht bringt sie **zum richtigen Programm**.

Beispiele:
Browser → Webserver
Discord → Discord-Server
Spiel → Gameserver

---
## Aufgaben
- Multiplexing
- Demultiplexing
- Ports
- Zuverlässigkeit
- Reihenfolge
- Flusskontrolle
- Staukontrolle
- Fehlererkennung

---
# 2. TCP vs UDP

|TCP|UDP|
|---|---|
|verbindungsorientiert|verbindungslos|
|zuverlässig|unzuverlässig|
|Reihenfolge garantiert|Reihenfolge nicht garantiert|
|ACKs|keine ACKs|
|Retransmissions|keine Retransmissions|
|Flusskontrolle|keine Flusskontrolle|
|Staukontrolle|keine Staukontrolle|
|größerer Overhead|kleiner Overhead|

---
## Merksatz
TCP = **zuverlässig**
UDP = **schnell**

---
# 3. Wann verwendet man welches?
## TCP
Für Anwendungen, bei denen **kein Datenverlust akzeptabel** ist.

Beispiele
- HTTP
- HTTPS
- FTP
- SSH
- E-Mail

---
## UDP

Für Anwendungen, bei denen **Geschwindigkeit wichtiger** ist.

Beispiele
- VoIP
- Videokonferenzen
- Online-Spiele
- DNS
- DHCP

---
## Klausurfalle

DNS benutzt meistens **UDP**, obwohl es zur Anwendungsschicht gehört.

---
# 4. Multiplexing und Demultiplexing
## Multiplexing

Mehrere Anwendungen senden gleichzeitig Daten.

Die Transportschicht versieht jedes Segment mit Portnummern.

---
## Demultiplexing

Beim Empfänger entscheidet der Zielport,

welcher Prozess die Daten erhält.
```text
Browser  ─┐
Discord  ─┼── TCP ───► Internet
Spotify  ─┘
```

---
# 5. Ports
Server besitzen bekannte Ports.

Clients benutzen zufällige Ports.

Beispiel
```text
Client

192.168.0.15:50412
↓
Server

141.82.xx.xx:80
```

---
# 6. TCP Header
Wichtige Felder:
- Source Port
- Destination Port
- Sequence Number
- Acknowledgement Number
- Flags
- Window Size
- Checksum

---
## Klausurwissen

Nicht alle Felder auswendig lernen.

Wichtig sind:
- Sequence Number
- ACK Number
- Flags
- Window

---
# 7. TCP Flags

|Flag|Bedeutung|
|---|---|
|SYN|Verbindung aufbauen|
|ACK|Bestätigung|
|FIN|Verbindung beenden|
|RST|Verbindung sofort abbrechen|

---
# 8. Three-Way Handshake

TCP muss zuerst eine Verbindung aufbauen.

Ablauf:
```text
Client

SYN Seq=100
↓
Server

SYN ACK Seq=500 Ack=101
↓
Client

ACK Ack=501
```

Danach beginnt die Datenübertragung.

---
## Warum drei Nachrichten?

Der Server muss
- den Client bestätigen
- gleichzeitig seine eigene Sequenznummer mitteilen.

---
## Klausurwissen

Die Reihenfolge muss sitzen:

**SYN**
↓
**SYN ACK**
↓
**ACK**

---
# 9. Four-Way Termination

TCP wird kontrolliert beendet.

```text
Client

FIN
↓
Server

ACK
↓
Server

FIN
↓
Client

ACK
```

---
## Merksatz
Aufbau:
3 Pakete

Abbau:
4 Pakete

---
# 10. Sequenznummern
TCP nummeriert **jedes Byte**.

Nicht jedes Paket.

Beispiel:
Paketgröße:
100 Byte

Erstes Segment
Seq = 2000

↓

zweites Segment
Seq = 2100

↓

drittes Segment
Seq = 2200

---
## ACK
ACK bedeutet:

"Alle Bytes **bis einschließlich Byte 2099** sind angekommen."

ACK = 2100

---
## Klausurwissen
ACK zeigt **immer das nächste erwartete Byte**.

Nicht das zuletzt empfangene!

---
# 11. Sliding Window
Mehrere Pakete dürfen gleichzeitig unterwegs sein.

Nicht auf jedes ACK muss gewartet werden.
```text
Sender

1
2
3
4

────────►

ACK
```
Dadurch steigt der Durchsatz erheblich.

---
# 12. Flusskontrolle
Ziel:

Empfänger nicht überlasten.

Der Empfänger teilt mit, wie groß sein Empfangspuffer noch ist.

Dies geschieht über das **Receive Window (rwnd)**.

---
## Wichtig

Flusskontrolle schützt
→ **den Empfänger**

---
# 13. Staukontrolle (Congestion Control)
Ziel:

Das Netzwerk nicht überlasten.

TCP nutzt dazu
- cwnd
- Slow Start
- Congestion Avoidance

---
## Klausurfalle
Flusskontrolle ≠ Staukontrolle

---
## Unterschied
Flusskontrolle
→ Empfänger schützen

Staukontrolle
→ Netzwerk schützen

---
# 14. Slow Start

Nach dem Verbindungsaufbau kennt TCP die verfügbare Bandbreite nicht.

Deshalb startet TCP vorsichtig.

Start:
```text
cwnd = 1 MSS
```

---

Entwicklung:
```text
1
↓
2
↓
4
↓
8
↓
16
```

Exponentielles Wachstum.

---
# 15. Congestion Avoidance
Nach Erreichen von **ssthresh**

steigt das Fenster nur noch langsam.

```text
16
↓
17
↓
18
↓
19
```

Lineares Wachstum.

---
## Merksatz
Slow Start = Exponentiell

Congestion Avoidance = Linear

---
# 16. Paketverlust
TCP erkennt Verluste

durch
- Timeout
- Duplicate ACKs

---
Nach einem Verlust
```text
ssthresh = cwnd / 2
```
Danach beginnt abhängig vom TCP-Verfahren (z. B. Tahoe oder Reno) die Erholung.

Für die Klausur reicht in der Regel:
- Fenster wird reduziert
- vorsichtiger Neuaufbau beginnt

---
# 17. TCP Checksum
TCP besitzt eine Prüfsumme.

Sie erkennt Bitfehler.

Sie kann
✔ erkennen

aber
✖ nicht korrigieren.

---
# 18. UDP
UDP besitzt
- Source Port
- Destination Port
- Length
- Checksum

Mehr nicht.

Dadurch ist UDP sehr klein.

Headergröße:

**8 Byte**

---
## UDP kann NICHT
- Reihenfolge garantieren
- Pakete erneut senden
- Verbindung aufbauen
- Flusskontrolle durchführen
- Staukontrolle durchführen

---
# 19. TCP oder UDP?

|Anwendung|Protokoll|
|---|---|
|HTTP|TCP|
|HTTPS|TCP|
|FTP|TCP|
|SSH|TCP|
|DNS|UDP (meist)|
|DHCP|UDP|
|Videostream|UDP|
|VoIP|UDP|
|Gaming|meist UDP|

---
# 20. Typische Klausuraufgabe

In einer Beispielklausur soll eine **frisch aufgebaute TCP-Verbindung** dargestellt werden. Gefordert sind:
- Three-Way Handshake
- Übertragung von **7 Paketen à 100 Byte**
- korrekte **Sequenz- und ACK-Nummern**
- anschließend der **Verbindungsabbau mit Four-Way Termination**.

**Vorgehen:**
1. Handshake einzeichnen.
2. Sequenznummern jeweils um die Nutzdaten erhöhen.
3. ACK zeigt immer das nächste erwartete Byte.
4. Verbindung mit FIN/ACK sauber schließen.

---

# 21. Typische Multiple-Choice-Fallen
❌ UDP garantiert Reihenfolge.
→ **Falsch**

---
❌ TCP nutzt keine ACKs.
→ **Falsch**

---
❌ Flusskontrolle schützt das Netzwerk.
→ **Falsch**

---
❌ Staukontrolle schützt den Empfänger.
→ **Falsch**

---
❌ ACK enthält die Nummer des zuletzt empfangenen Bytes.
→ **Falsch**

ACK enthält **das nächste erwartete Byte**.

---

# 22. Merksätze
- **TCP = zuverlässig, UDP = schnell.**
- **Port = Prozess.**
- **IP = Rechner.**
- **Sequence Number zählt Bytes.**
- **ACK = nächstes erwartetes Byte.**
- **Three-Way Handshake: SYN → SYN/ACK → ACK.**
- **Four-Way Termination: FIN → ACK → FIN → ACK.**
- **Slow Start wächst exponentiell.**
- **Congestion Avoidance wächst linear.**
- **Flusskontrolle schützt den Empfänger.**
- **Staukontrolle schützt das Netzwerk.

---
# Kapitel 4 – Netzwerkschicht

(Basierend auf _Dako 04 – Netzwerkschicht_)

---
# 1. Aufgabe der Netzwerkschicht

Die Netzwerkschicht sorgt dafür, dass **Pakete von einem Endsystem zu einem anderen gelangen**, auch wenn viele Router dazwischen liegen.

Sie verwendet dafür **IP (Internet Protocol)**.

Die beiden Hauptaufgaben sind:
- **Forwarding (Weiterleitung)**
- **Routing (Wegewahl)**

---
# 2. Forwarding vs. Routing

Diese beiden Begriffe werden in Klausuren sehr gerne verwechselt.

## Forwarding (Weiterleitung)
**Forwarding** bedeutet:
> Ein Router entscheidet anhand seiner Routingtabelle, über welches Interface ein eingehendes Paket weitergeleitet wird.

Eigenschaften:
- passiert für **jedes Paket**
- lokal im Router
- sehr schnell
- nutzt die Routingtabelle

---
## Routing
**Routing** bedeutet:

> Berechnen der besten Wege durch das Netzwerk.

Routing erstellt also erst die Routingtabellen.

---
## Unterschied

|Forwarding|Routing|
|---|---|
|Weiterleitung eines Pakets|Berechnung der Wege|
|lokal|verteilt|
|schnell|langsamer|
|Routingtabelle benutzen|Routingtabelle erstellen|

---
## Klausurfalle
**Router routen nicht jedes Paket neu.**

Sie berechnen gelegentlich Routingtabellen.

Beim normalen Betrieb wird **Forwarding** durchgeführt.

---
# 3. Best-Effort-Dienst
IP garantiert **nichts**.

Keine Garantie für:
- Zustellung
- Reihenfolge
- Bandbreite
- Verzögerung

IP versucht lediglich, das Paket möglichst gut weiterzuleiten.

---
# 4. IPv4-Adresse
IPv4 besteht aus

**32 Bit**
also
**4 Byte**

Schreibweise:
```text
192.168.10.15
```

Jedes Byte:
0–255

---
# 5. IPv4-Header
Wichtige Felder:

|Feld|Bedeutung|
|---|---|
|Version|IPv4|
|IHL|Headerlänge|
|Total Length|Paketgröße|
|Identification|Fragment-ID|
|Flags|Fragmentierung|
|Fragment Offset|Position des Fragments|
|TTL|Lebensdauer|
|Protocol|nächstes Protokoll (TCP/UDP)|
|Header Checksum|Prüfsumme|
|Source Address|Quell-IP|
|Destination Address|Ziel-IP|

---
## Was sollte man auswendig können?
Unbedingt:
- TTL
- Protocol
- Identification
- Fragment Offset
- Flags

Die übrigen Felder kennen, aber nicht im Detail auswendig lernen.

---
# 6. TTL (Time To Live)
TTL verhindert, dass Pakete endlos im Netzwerk kreisen.

Jeder Router
```text
TTL = TTL - 1
```
Erreicht TTL den Wert **0**,

wird das Paket verworfen.

---
## Beispiel
Start:
TTL = 64

Nach Router 1:
63

Nach Router 2:
62

...

---
# 7. Protocol-Feld
Dieses Feld sagt, welches Transportprotokoll folgt.

Beispiele:

|Wert|Protokoll|
|--:|---|
|6|TCP|
|17|UDP|
|1|ICMP|

---
# 8. Fragmentierung
Jede Sicherungsschicht besitzt eine maximale Rahmengröße.

Diese nennt man

**MTU (Maximum Transmission Unit)**.

---

Wenn
```text
IP-Paket > MTU
```
muss fragmentiert werden.

---
## Fragmentierung geschieht
**im Router**

Nicht im Sender.

---
## Wiederzusammensetzen
Geschieht

**nur beim Empfänger**

Nicht unterwegs.

---
# 9. Wichtige Felder für Fragmentierung
## Identification
Alle Fragmente desselben Pakets besitzen die gleiche ID.

---
## Fragment Offset
Gibt an, an welcher Stelle das Fragment im ursprünglichen Paket liegt.

Einheit:
**8 Byte**

---
## MF-Flag (More Fragments)
MF = 1
→ weitere Fragmente folgen

MF = 0
→ letztes Fragment

---
# Beispiel
Original:
2000 Byte

MTU:
1500 Byte

IP-Header:
20 Byte

Erstes Fragment:
- Daten = 1480 Byte
- Offset = 0
- MF = 1

Zweites Fragment:
- Daten = 500 Byte
- Offset = 185 (1480 / 8)
- MF = 0

Genau dieses Beispiel wird in den Vorlesungsfolien erläutert.

---
# 10. Probleme der Fragmentierung
- Router müssen zusätzliche Arbeit leisten.
- Geht **ein Fragment verloren**, ist das **gesamte IP-Datagramm unbrauchbar**.
- Zusätzlicher Header-Overhead.

---
# 11. CIDR
CIDR beschreibt, welche Bits das Netzwerk bilden.

Beispiel
```text
192.168.1.25/24
```

bedeutet
24 Bit Netzwerk
8 Bit Host.

---
## Merksatz
Je größer die Präfixlänge, desto kleiner das Netzwerk.

---
# 12. Longest Prefix Match
Router wählen
**immer den längsten passenden Präfix.**

Nicht den ersten.

Nicht den kleinsten.

Nicht den größten.

Immer
**den längsten Match.**

---
## Beispiel
Routingtabelle
```text
10.0.0.0/8

10.1.0.0/16

10.1.2.0/24
```

Paket:
```text
10.1.2.17
```

Treffer:
alle drei

gewählt wird
```text
10.1.2.0/24
```

weil
24 > 16 > 8

---
## Klausur
Eine komplette Aufgabe besteht aus einer Routingtabelle, für verschiedene Zieladressen muss das richtige Interface bestimmt werden.

Dieser Aufgabentyp kommt in den Beispielklausuren mehrfach vor.

---
# 13. Routing
Routing berechnet die besten Wege.

Dazu existieren verschiedene Algorithmen.

---
## Link State
Jeder Router kennt die komplette Topologie.

Algorithmus:
**Dijkstra**

---
### Vorteile
- schnelle Konvergenz
- optimale Wege
### Nachteile
- hoher Speicherbedarf
- hoher Informationsaustausch

---
## Distance Vector
Jeder Router kennt nur seine Nachbarn.

Beispiel:
RIP

---
### Vorteile
- einfach
### Nachteile
- langsam
- Count-to-Infinity-Problem

---
# 14. Dijkstra
Dijkstra berechnet den kürzesten Weg von einem Startknoten.

---
## Ablauf
1. Startknoten festlegen.
2. Distanz = 0.
3. Alle anderen = ∞.
4. Kleinste bekannte Distanz auswählen.
5. Nachbarn aktualisieren.
6. Wiederholen.

---
## Prüfung
Immer Tabelle vollständig ausfüllen.

Nicht nur Endergebnis.

Fast jede Beispielklausur enthält eine Dijkstra-Aufgabe.

---
# 15. NAT
NAT = Network Address Translation

---
Zweck:
Mehrere Geräte teilen sich eine öffentliche IP-Adresse.

---
## NAT verändert
- IP-Adressen
- Portnummern

Nicht
- HTTP
- TCP-Daten
- Nutzdaten

---
## Vorteile
- spart IPv4-Adressen
- private Netze möglich

---
## Klausurfalle
NAT verändert **nicht** die Anwendungsschicht.

Es verändert Netzwerk- und Transportschicht-Header.

Eine ähnliche Aussage findet sich als Multiple-Choice-Frage in den Beispielklausuren.

---
# 16. Private IP-Adressen
Nicht im Internet routbar.

Bereiche:

|Bereich|
|---|
|10.0.0.0/8|
|172.16.0.0/12|
|192.168.0.0/16|

---
## Eigenschaften
✔ weltweit mehrfach nutzbar
✔ benötigen NAT
✖ nicht direkt im Internet erreichbar

---
# 17. ICMP
Internet Control Message Protocol

Dient für
- Fehlermeldungen
- Diagnose

Beispiele
- Ping
- Destination Unreachable
- Time Exceeded (TTL)

---
# 18. Typische Klausurfallen
❌ Routing = Forwarding
→ falsch

---
❌ NAT verändert HTTP
→ falsch

---
❌ TTL steigt an jedem Router
→ falsch

---
❌ Fragment Offset in Byte
→ falsch

Einheit:
**8 Byte**

---
❌ Router setzen Fragmente wieder zusammen
→ falsch

Nur der Empfänger setzt Fragmente wieder zusammen.

---
# 19. Merksätze
- **Forwarding benutzt Routingtabellen.**
- **Routing erstellt Routingtabellen.**
- **IP ist Best Effort.**
- **TTL wird an jedem Router um 1 reduziert.**
- **Protocol-Feld gibt TCP/UDP/ICMP an.**
- **Fragmentierung erfolgt im Router.**
- **Zusammensetzen erfolgt beim Empfänger.**
- **Longest Prefix Match gewinnt immer.**
- **Dijkstra = Link State.**
- **Private IP-Adressen sind nicht im Internet routbar.**
- **NAT verändert IP-Adressen und Portnummern.**

---
# Kapitel 5 – Sicherungsschicht

(Basierend auf _Dako 05 – Sicherungsschicht_)

---
# 1. Aufgabe der Sicherungsschicht
Die Sicherungsschicht sorgt für die **Übertragung eines Frames zwischen zwei direkt verbundenen Geräten**.

Wichtig:
Sie arbeitet **nicht über das gesamte Internet**, sondern immer nur auf einem **einzelnen Link**.

Beispiel:
```text
PC ───── Switch ───── Router
```

Die Sicherungsschicht kümmert sich immer nur um **eine Verbindung**.

---
## Hauptaufgaben
- Framing
- MAC-Adressierung
- Fehlererkennung
- Fehlerkorrektur (teilweise)
- Medienzugriff
- teilweise Flusskontrolle

---
# 2. Frame
Die Sicherungsschicht überträgt **Frames**.

Kapselung:
```text
Ethernet Header
↓
IP-Paket
↓
CRC
```

Merksatz:
**Frame = Ethernet + IP-Paket + Prüfsumme**

---
# 3. MAC-Adresse
Jede Netzwerkkarte besitzt eine **MAC-Adresse**.

Eigenschaften:
- 48 Bit
- weltweit eindeutig
- hexadezimale Darstellung

Beispiel
```text
00:1A:2B:3C:4D:5E
```

---
## Unterschied zur IP-Adresse

|IP-Adresse|MAC-Adresse|
|---|---|
|logisch|physisch|
|kann sich ändern|normalerweise fest|
|Routing|lokale Übertragung|
|Layer 3|Layer 2|

---
## Merksatz
IP sagt:
> **Zu welchem Rechner?**

MAC sagt:
> **Zu welcher Netzwerkkarte?**

---
# 4. Ethernet
Ethernet ist die wichtigste Sicherungsschicht-Technologie.

Ein Ethernet-Frame besteht aus:
- Ziel-MAC
- Quell-MAC
- Typ
- Nutzdaten
- CRC

---
## Ethernet kennt keine
- Ports
- IP-Adressen
- TCP

Nur MAC-Adressen.

---
# 5. Switch
Ein Switch verbindet Geräte innerhalb eines LAN.

Er arbeitet auf **Layer 2**

---
## Aufgaben
- Frames weiterleiten
- MAC-Adressen lernen
- Broadcast weiterleiten

---
## Self Learning
Switches lernen automatisch, welche MAC-Adresse an welchem Port angeschlossen ist.

Dadurch müssen sie nicht konfiguriert werden.

---
## MAC-Tabelle
Beispiel

|MAC|Port|
|---|---|
|A|1|
|B|2|
|C|5|

---
## Unbekannte MAC-Adresse
Ist die Ziel-MAC unbekannt, sendet der Switch den Frame an **alle Ports außer dem Eingangsport**

(Flooding).

---
# 6. Broadcast
Broadcast bedeutet:

Ein Frame wird an **alle Geräte im lokalen Netzwerk** geschickt.

Broadcast-Adresse:
```text
FF:FF:FF:FF:FF:FF
```

---
## Wichtig
Broadcasts werden **nicht von Routern weitergeleitet**.

Sie bleiben im lokalen Netzwerk.

---
# 7. ARP
ARP = Address Resolution Protocol

---
Aufgabe:

IP-Adresse
↓
MAC-Adresse

ermitteln.

---
## Beispiel
PC möchte 192.168.1.5 anschreiben.

Die MAC-Adresse ist unbekannt.

---
Ablauf
```text
ARP Request (Broadcast)
↓
Wer hat 192.168.1.5?
↓
ARP Reply (Unicast)
↓
MAC-Adresse bekannt
```

---
## Merksatz
ARP = IP → MAC

---
## Klausurfalle
ARP arbeitet **nur innerhalb eines LANs**.

Nicht über Router hinweg.

---
# 8. Fehlererkennung
Während der Übertragung können Bitfehler entstehen.

Die Sicherungsschicht erkennt diese mit Prüfsummen.

---
# 9. Paritätsbit
Die einfachste Prüfsumme.

---
## Gerade Parität
Paritätsbit wird so gewählt, dass insgesamt eine gerade Anzahl von Einsen entsteht.

---
## Ungerade Parität
Anzahl der Einsen ist ungerade.

---
## Nachteil
Erkennt nur eine **ungerade Anzahl** von Bitfehlern.

Zwei Bitfehler bleiben unentdeckt.

---
# 10. Mehrdimensionale Parität
Parität über
- Zeilen
- Spalten

Dadurch können Einbitfehler nicht nur erkannt, sondern auch korrigiert werden.

---
## Grenzen
Mehrere Bitfehler sind nicht immer korrigierbar.

---
# 11. CRC
CRC = Cyclic Redundancy Check

---
CRC ist deutlich besser als die Internet-Prüfsumme.

Es wird z. B. bei Ethernet verwendet.

---
## Idee
Sender berechnet eine Prüfsumme.

Empfänger berechnet dieselbe Prüfsumme erneut.

Sind beide gleich, ist das Paket wahrscheinlich fehlerfrei.

---
# 12. CRC-Berechnung
Gegeben:
- Daten D
- Generator G

Sender:
1. Daten mit Nullen erweitern.
2. Modulo-2-Division durchführen.
3. Rest anhängen.

Empfänger:
Division erneut durchführen.

Rest = 0
↓
kein Fehler erkannt.

---
## Modulo-2-Arithmetik
Es gibt **keinen Übertrag**.

Addition = XOR

Beispiele:
```text
0 ⊕ 0 = 0
0 ⊕ 1 = 1
1 ⊕ 0 = 1
1 ⊕ 1 = 0
```

---
## Klausur
Wenn CRC gerechnet wird, immer sauber die XOR-Division durchführen.

---
# 13. Fehlerkorrektur
Es gibt zwei Möglichkeiten:

---
## Forward Error Correction (FEC)
Der Empfänger kann Fehler selbst korrigieren.

Keine erneute Übertragung notwendig.

---
## Automatic Repeat Request (ARQ)

Fehlerhaftes Paket
↓
erneut senden.

TCP verwendet ARQ.

---
# 14. Gemeinsamkeiten der Prüfsummen

|Verfahren|erkennt|korrigiert|
|---|---|---|
|Parität|teilweise|nein|
|Mehrdimensionale Parität|viele Fehler|Einbitfehler|
|CRC|sehr viele Fehler|nein|

---
# 15. Typische Klausurfallen
❌ Switch arbeitet auf Layer 3.
→ falsch

---
❌ Router kennt MAC-Adressen aller Geräte.
→ falsch

---
❌ Broadcast geht durchs Internet.
→ falsch

---
❌ ARP übersetzt MAC → IP.
→ falsch

ARP:
**IP → MAC**

---
❌ CRC korrigiert Fehler.
→ falsch

CRC erkennt Fehler, korrigiert sie aber nicht.

---
❌ Switch verändert IP-Adressen.
→ falsch

Switches verändern keine IP-Adressen und arbeiten transparent.

---
# 16. Merksätze
- **Frame = Einheit der Sicherungsschicht.**
- **MAC-Adresse = 48 Bit.**
- **IP = Routing.**
- **MAC = lokale Übertragung.**
- **Switch = Layer 2.**
- **Router = Layer 3.**
- **ARP übersetzt IP → MAC.**
- **Broadcast bleibt im LAN.**
- **CRC erkennt Bitfehler sehr zuverlässig.**
- **CRC verwendet XOR statt normaler Addition.**
- **Switches lernen MAC-Adressen automatisch (Self Learning).**

---
# Kapitel 6 – Klausurwissen & Prüfungstipps

---
# 1. Die wichtigsten Protokolle

|Protokoll|Schicht|Transport|Standard-Port|Aufgabe|
|---|---|---|---|---|
|HTTP|Anwendung|TCP|80|Webseiten|
|HTTPS|Anwendung|TCP|443|Webseiten (verschlüsselt)|
|DNS|Anwendung|UDP (meist)|53|Domain → IP|
|DHCP|Anwendung|UDP|67/68|IP-Konfiguration|
|SMTP|Anwendung|TCP|25|E-Mail senden|
|POP3|Anwendung|TCP|110|E-Mail abrufen|
|IMAP|Anwendung|TCP|143|E-Mail verwalten|
|FTP|Anwendung|TCP|20/21|Dateitransfer|
|TCP|Transport|-|-|zuverlässiger Transport|
|UDP|Transport|-|-|schneller Transport|
|IPv4|Netzwerk|-|-|Routing|
|ARP|Sicherung|-|-|IP → MAC|
|Ethernet|Sicherung|-|-|Frame-Übertragung|

---
# 2. Welche Schicht macht was?

|Aufgabe|Schicht|
|---|---|
|Webseiten übertragen|Anwendung|
|Ports|Transport|
|Zuverlässigkeit|Transport|
|Routing|Netzwerk|
|Forwarding|Netzwerk|
|IP-Adressen|Netzwerk|
|Fragmentierung|Netzwerk|
|MAC-Adressen|Sicherung|
|Switches|Sicherung|
|CRC|Sicherung|

---
# 3. Welche Geräte arbeiten auf welcher Schicht?

|Gerät|Schicht|
|---|---|
|Host|alle|
|Switch|Layer 2|
|Router|Layer 3|

---
# 4. TCP vs UDP

| Eigenschaft                            |    TCP     |  UDP   |
| -------------------------------------- | :--------: | :----: |
| Verbindungsorientiert                  |     ✅      |   ❌    |
| Zuverlässige Übertragung               |     ✅      |   ❌    |
| Reihenfolge garantiert                 |     ✅      |   ❌    |
| ACKs                                   |     ✅      |   ❌    |
| Neuübertragung verlorener Pakete       |     ✅      |   ❌    |
| Flusskontrolle                         |     ✅      |   ❌    |
| Staukontrolle                          |     ✅      |   ❌    |
| Verbindung vor Datentransfer notwendig |     ✅      |   ❌    |
| Geringer Overhead                      |     ❌      |   ✅    |
| Sehr geringe Latenz                    |     ❌      |   ✅    |
| Geeignet für Echtzeitanwendungen       |     ❌      |   ✅    |
| Headergröße                            | 20–60 Byte | 8 Byte |
### Typische Anwendungen

| TCP   | UDP            |
| ----- | -------------- |
| HTTP  | DNS (meist)    |
| HTTPS | DHCP           |
| FTP   | VoIP           |
| SSH   | Videostreaming |
| SMTP  | Online-Gaming  |
| IMAP  | Livestreams    |

---
### Merkhilfe für die Klausur
**TCP**
- Verbindungsorientiert
- Zuverlässig
- ACKs
- Reihenfolge garantiert
- Flusskontrolle
- Staukontrolle
- Höherer Overhead

**UDP**
- Verbindungslos
- Unzuverlässig
- Keine ACKs
- Keine Reihenfolge
- Keine Fluss- oder Staukontrolle
- Sehr kleiner Header (8 Byte)
- Dafür deutlich schneller

---
# 5. Reihenfolgen, die auswendig sitzen müssen

## TCP-Verbindungsaufbau
```text
SYN
↓
SYN ACK
↓
ACK
```

---
## TCP-Verbindungsabbau
```text
FIN
↓
ACK
↓
FIN
↓
ACK
```

---
## DHCP
```text
Discover
↓
Offer
↓
Request
↓
ACK
```

Merksatz:
**DORA**

---
## DNS (iterativ)
```text
Client
↓
lokaler DNS
↓
Root
↓
TLD
↓
Authoritative DNS
↓
IP-Adresse
↓
Client
```

---
# 6. Broadcast oder nicht?

|Protokoll|Broadcast?|
|---|---|
|DHCP Discover|✔|
|ARP Request|✔|
|HTTP|✖|
|TCP|✖|
|DNS|✖ (normalerweise Unicast)|

---
# 7. NAT
Merken:
✔ verändert
- Quell-/Ziel-IP
- Quell-/Ziel-Port

✖ verändert nicht
- HTTP
- TCP-Nutzdaten
- Webseiten

---
# 8. Private IPv4-Adressen

|Bereich|
|---|
|10.0.0.0/8|
|172.16.0.0/12|
|192.168.0.0/16|

Eigenschaften:
- nicht im Internet routbar
- mehrfach weltweit verwendbar
- NAT notwendig

---
# 9. IPv4-Header (nur die wirklich wichtigen Felder)

|Feld|Bedeutung|
|---|---|
|TTL|verhindert Endlosschleifen|
|Protocol|TCP / UDP / ICMP|
|Identification|Fragment-ID|
|Fragment Offset|Position des Fragments|
|MF|weitere Fragmente vorhanden|

---
# 10. Longest Prefix Match
Merksatz:
> **Immer den längsten passenden Präfix wählen.**

Nicht:
- den ersten
- den kleinsten
- den größten

Sondern:
**die höchste Präfixlänge.**

---
# 11. Dijkstra

Immer dieselben Schritte:
1. Start = 0
2. alle anderen = ∞
3. kleinste Distanz auswählen
4. Nachbarn aktualisieren
5. wiederholen

---
# 12. Flusskontrolle vs Staukontrolle

|Flusskontrolle|Staukontrolle|
|---|---|
|schützt Empfänger|schützt Netzwerk|
|Receive Window|Congestion Window|

---
# 13. Slow Start
Merken:

```text
1
↓
2
↓
4
↓
8
↓
16
```

Exponentiell.

---
# Congestion Avoidance

```text
16
↓
17
↓
18
↓
19
```

Linear.

---
# 14. ARP
ARP bedeutet:
```text
IP-Adresse
↓
MAC-Adresse
```
Nicht andersherum.

---
# 15. CRC
CRC
✔ erkennt Bitfehler
✖ korrigiert keine Bitfehler

---
# 16. Typische Multiple-Choice-Fallen
## HTTP
❌ HTTP speichert Sitzungen.
→ falsch

HTTP ist zustandslos.

---
## Cookies
❌ Cookies erhöhen die Sicherheit.
→ falsch

Cookies speichern Zustand.

---
## TCP
❌ ACK zeigt letztes empfangenes Byte.
→ falsch

ACK zeigt das nächste erwartete Byte.

---
## UDP
❌ UDP garantiert Reihenfolge.

→ falsch

---
## NAT
❌ NAT verändert Webseiten.
→ falsch

---
## Routing
❌ Router berechnen bei jedem Paket neue Wege.
→ falsch

Sie nutzen vorhandene Routingtabellen (Forwarding).

---
## Switch
❌ Switch arbeitet auf Layer 3.
→ falsch

---
## Broadcast
❌ Router leiten Broadcasts weiter.
→ falsch

---
## ARP
❌ ARP übersetzt MAC → IP.
→ falsch

---
## CRC
❌ CRC korrigiert Fehler.
→ falsch

---

# 17. Themen mit der höchsten Priorität
**Unbedingt beherrschen**
- TCP (Handshake, ACKs, Sequenznummern)
- Slow Start
- Dijkstra
- Longest Prefix Match
- DNS
- IPv4-Fragmentierung
- Routing vs. Forwarding

**Sehr wichtig**
- HTTP
- Cookies
- DHCP
- NAT
- Private IP-Adressen
- ARP
- Switches

**Sollte man kennen**
- CRC
- Ethernet-Frame
- Mehrdimensionale Parität
- Link State vs. Distance Vector
- ICMP

---

# 18. 15 Merksätze für die Klausur
1. **TCP zählt Bytes, nicht Pakete.**
2. **ACK = nächstes erwartetes Byte.**
3. **Slow Start wächst exponentiell.**
4. **Congestion Avoidance wächst linear.**
5. **Flusskontrolle schützt den Empfänger.**
6. **Staukontrolle schützt das Netzwerk.**
7. **Forwarding nutzt Routingtabellen.**
8. **Routing erstellt Routingtabellen.**
9. **Longest Prefix Match gewinnt immer.**
10. **TTL sinkt an jedem Router um 1.**
11. **Fragmentierung im Router, Zusammensetzen beim Empfänger.**
12. **ARP übersetzt IP → MAC.**
13. **Broadcasts verlassen das lokale Netz nicht.**
14. **Switch = Layer 2, Router = Layer 3.**
15. **HTTP ist zustandslos, Cookies speichern den Zustand.**

---
