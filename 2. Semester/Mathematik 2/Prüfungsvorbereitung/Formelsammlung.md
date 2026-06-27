-------------------------------------------------------------------***KOMBINATORIK:***-------------------------------------------------------------------
**Entscheidungsbaum:**-----------------------------------------------------------------------------------------**Fakultät:**
Reihenfolge?------------------------------------------------------------------------------------------------------$n! = 1\cdot2\cdot3\dots n$
- Ja--------------------------------------------------------------------------------------------------------------$0!=1$
	- Zurücklegen(PIN, Passwort, Würfelwurf, Münzwurf) -> $n^k$
	- Kein Zurücklegen(Flaggen, Sitzordnung, Podestplätze, Ämter) -> $\frac{n!}{(n-k)!}$
- Nein (Lotto, Team, Ausschuss)                                 
	- Zurücklegen(Eiskugeln, Bonbons, Kugeln mit Wiederholung) -> $\pmatrix{n+k-1\\k}$
	- Kein Zurücklegen(Lotto, Team wählen, Ausschuss, Jury) -> $\pmatrix{n\\ k}$

**Sonderfälle:**--------------------------------------------------------------------------------------------------------**Bitstrings:**
"erste Stelle $\neq 0$" -> Fälle unterscheiden(Statt $10^6$, $9\cdot10^5$)----------------------------------------------genau k einsen -> $\pmatrix{n\\ k}$
"genau k" -> Positionen wählen----------------------------------------------------------------------------------genau k Nullen -> Positionen wählen
"mindestens k" -> Summe bilden                                 
"höchstens k" -> Summe bilden(k=max. 2 = $\pmatrix{n\\0}+\pmatrix{n\\1}+\pmatrix{n\\2}$) 
"Nicht erlaubt" (Kennzeichen, 0000 verboten) -> Möglichkeiten - verbotene Möglichkeiten
**Binomialkoeffizient:** $\pmatrix{n\\ k} = \frac{n!}{k!\cdot(n-k)!}$
----------------------------------------------------------------------***ANALYSIS:***----------------------------------------------------------------------
**Länge:** $|v| = \sqrt{x^2+y^2}$ ------------------ **Skalarprodukt:**  $\overrightarrow{a}\cdot\overrightarrow{b}=a_x\cdot b_x+a_y\cdot b_y$ ----------------------**Winkel zw. 2 Vektoren:** $\cos{\alpha} = \frac{\overrightarrow{a}\cdot\overrightarrow{b}}{||\overrightarrow{a}||\cdot||\overrightarrow{b}||}$------------------**Orthogonal** <=> $\overrightarrow{a}\cdot\overrightarrow{b}=0$ -----------------**Gerade:** $\overrightarrow{x}=\overrightarrow{p}+t\cdot\overrightarrow{r}$ ----------------------**Parralel(Kein Punkt auf geraden) oder Identisch(Punkt auf geraden):** $r_1=\lambda\cdot r_2$ ---------------**Vektor von A nach B:** $\overrightarrow{AB}=\pmatrix{x_{B}-x_{A}\\ y_{B}-y_{A}}$ ---------- **Abstand zweier Punkte:** $d(A,B)=\sqrt{(x_2 - x_1)^2+(y_2-y_1)²}$ 
**Punktprobe:** $g: \overrightarrow{x}=\overrightarrow{p}+t\cdot\overrightarrow{r}$  -------------- $P(x_P | y_P)$ ------------- 1. x-Koordinate einsetzen -> $t$ berechnen ($x=p+t\cdot r$) ---------- 2. $t$ in y-Koordinate einsetzen ------- 3.Stimmen beide Gleichungen? ------ Ja -> P liegt auf g ------- Nein -> P liegt nicht auf g
**Abstand Punkt-Gerade:** Geg. $g: \overrightarrow{x}=\pmatrix{p_x\\ p_y}+t\cdot\pmatrix{r_x\\ r_y}$ , Punkt $Q(Q_x,Q_y)$ ----- Schritt 1. Punkt auf Gerade $S(t) = \pmatrix{p_x+r_x\cdot t\\ p_y+r_y\cdot t}$  ----- Schritt 2. Verbindungsvektor $\overrightarrow{SQ}=\pmatrix{Q_x\\ Q_y}-\pmatrix{p_x+r_x\cdot t\\ p_y+r_y\cdot t}$ ----- Schritt 3. Orthogonalitätsbedingung: $\overrightarrow{SQ}\cdot\overrightarrow{r}=0$ -> Skalarprodukt und nach t umstellen ----- Schritt 4. Lotfußpunkt $S$ bestimmen -> t einsetzen $S=\pmatrix{p_x+r_x\cdot t\\ p_y+r_y\cdot t}$ ----- Abstand berechnen $d = |Q-S|$ mit $|Q-S|=\sqrt{(x_Q - x_S)^2+(y_Q-y_S)^2}$ 
---------------------------------------------------***ZAHLENTHEORIE & MODULARE ARITHMETIK:*** ---------------------------------------------------
**Teilbarkeit:** $a | b$ <=> $b = a\cdot k$ 
**ggT(a,b):** **Euklid:** $a = q\cdot b + r$ -> $ggT(a,b)=ggT(b,r)$->$r_n=0$->fertig------------------------------**Erweiterter Euklid:**
![[megaCoolAlgorithm.png|398]] $a\cdot x + b\cdot y=ggT$ ------- wenn ggT=1 -> x bzw. y liefert Inverse.
**Multiplikative Inverse:** Existiert nur wenn $ggT(a,m)=1$ --------- Dann $a\cdot a^{-1} \equiv 1 \mod m$
**Lineare Kongruenz:** $a\cdot x\equiv b \mod m$ ------- Gibt es lösung: $ggT(a,m) = 1$? ------ Ja: Inverse berechnen -> beide Seiten mit Inverser multiplizieren -> $x=a^{-1}\cdot b \mod m$ ----- $ggT(a,m)=d$ -- wenn $d\nmid b$ dann keine Lösung -- wenn $d\mid b$ dann $d$ Lösungen 
**Modulo:** $(a+b) \mod m = ((a \mod m) + (b \mod m)) \mod m$ ---- $(a\cdot b) \mod m = ((a\mod m)\cdot(b \mod m)) \mod m$ 
**Euler $\varphi$:** Primzahl: $\varphi(p)=p-1$ ------ Produkt zweier Primzahlen: $\varphi(p\cdot q)=(p-1)\cdot(q-1)$ ----Allgemein: $\varphi(n)=n\cdot\displaystyle\prod_{p|n}{(1-\frac{1}{p})}$
**Satz von Euler:**$ggT(a,m)=1$ -> $a^{\varphi(m)}\equiv1\mod{m}$ ---- Große Potenzen $a^k$ -> k durch $\varphi$ reduzieren

---

---

**RSA:** Geg. $p, q, e$ ---- 1. $n=p\cdot q$ ---- 2. $\varphi=(p-1)\cdot(q-1)$ ---- 3. $ggT(e,\varphi)=1$? ---- 4. $d=e^{-1}\mod{\varphi}$ ---- 5. Öffentlich $=(n,e)$  ---- 6. Privat $= d$ ----- **Verschlüsseln:** $c=m^e\mod{n}$ ----- **Entschlüsseln:** $m=c^d\mod{n}$ 
**ISBN-10:** $10\cdot a_1+9\cdot a_2+\dots+2\cdot a_9+p\equiv 0 \pmod{11}$ ---- Prüfziffer = p -> Ziffern mult. & summieren. -> $sum + p \equiv 0 \pmod{11}$
**Chinesischer Restsatz:** Geg. $x_1\equiv y_1 \pmod{m_{1}}$ und  $x_2\equiv y_2 \pmod{m_{2}}$ und $x_3\equiv y_3 \pmod{m_{3}}$ ------- Schritt 1: $M = m_1 \cdot m_2 \cdot m_3$ ------ Schritt 2: ${M_i=\frac{M}{m_i}}$ für jedes $m$ ------ Schritt 3: für jedes $M_i$ die Inverse $M_{i}^{-1}$ bestimmen ----- Schritt 4: $S=\displaystyle \sum_{n=1}^{i}{(y_n \cdot M_n \cdot M_{i}^{-1})}$  ------ Schritt 5: $S \mod M = Y$ -> $x \equiv Y \pmod{M}$ ------ *Kontrolle:* $Y \mod{m_i} = y_i$? 
-----------------------------------------------------------------***GRAPHENTHEORIE:***-----------------------------------------------------------------
**Grundbegriffe:** $G = (V, E)$ -> $(V)$ = Knotenmenge, $(E)$ = Kantenmenge ----------- **_Grad(v)_** = Anzahl der Kanten am Knoten ------- **_Baum:_** zusammenhängend, kreisfrei, $|E| = |V|-1$ ------ **_Adjazenz:_** direkt verbundene Knoten
**Euler:** **_Eulerweg_:** jede Kante genau 1x ---- **_Eulerkreis_:** jede Kante genau 1x und Start=Ende ---- **_Voraussetzung:_** zsm. hängend
**Anzahl ungerader Grade:** 0 -> Eulerkreis ----- 2 -> Eulerweg ------ >2 -> keiner
**Hamilton:** **_Hamiltonweg:_** jeder Knoten genau 1x ----- **_Hamiltonkreis:_** jder Knoten genau 1x und Start=Ende
**Zuständigkeit:** **Euler => Kanten** und **Hamilton => Knoten**
**DFS (Depth First Search/Tiefensuche):** Datenstruktur=Stack ---- **Algorithmus:** Schritt 1. Startknoten ---- Schritt 2. ersten unbesuchten Nachbarn ---- Schritt 3. weiter in Tiefe(Entfernung vom Start) ---- Schritt 4. Sackgasse? zurück ---- Schritt 5. weiter
**BFS (Breadth First Search/Breitensuche):** Datenstruktur=Queue ---- **Algorithmus:** Schritt 1. Startknoten ---- Schritt 2. alle Nachbarn ---- Schritt 3. Nachbarn der Nachbarn ---- Schritt 4. weiter
**Minimaler Spannbaum:** Prim vs Kruskal:  (Knoten, wächst zsm.hängend, innen nach außen) vs (Kanten, verbindet Teilbäume)
**Prim:** Start bei beliebigem Knoten -> billigste Nachbarkante -> kein Kreis? -> wiederholen
**Kruskal:** Schritt 1. alle Kanten sortieren ---- Schritt 2. billigste wählen ---- Schritt 3. entsteht Kreis? -- Ja, weg -- Nein, nehmen
**Graphfärbung:** Ziel: möglichst wenige Farben & Benachbarte Knoten $\neq$ gleiche Farbe ---- $\chi(G) =$ kleinste benötigte Farbanzahl
**Bipartiter Graph:** 2 Knotenmengen ----- innerhalb einer Menge keine Kanten ----- **Erkennung:** -> kein Kreis ungerader Länge
**Matching:** kein Knoten doppelt ----- **Vollständiges Matching:** alle Knoten links einem Knoten rechts zugeordnet ----- **Maximales Matching:** Möglichst viele Kanten verbunden
**Isomorphie:** prüfen: gleiche Knotenzahl, gleiche Kantenzahl, gleiche Gradfolge -> erst dann Zuordnung suchen