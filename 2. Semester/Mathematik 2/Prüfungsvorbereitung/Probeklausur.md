1. Norwegische KFZ-Kennzeichen bestehen aus 2 Großbuchstaben, gefolgt von 4 Ziffern, wobei die Ziffernkombination 0000 nicht erlaubt ist. Wie viele verschiedene Nummernschilder sind in Norwegen möglich? (4P)
   A: $26^2 \cdot (10^4-1)=6759324$  
2. Wie viele verschiedene Flaggen kann man aus fünf Farben bilden, wenn die Flagge aus drei horizontalen Streifen besteht und alle drei Farben verschieden sein sollen. (5P)
   A: $\frac{5!}{(5-3)!}=60$ 
3. Wie viele unterschiedliche Dezimalzahlen mit 6 Ziffern gibt es, wenn 2 Positionen gleich Null sein sollen? (5P)
   A: Erste Stelle keine Null darum $\pmatrix{5\\2}=10$ 
   Die übrigen vier stellen jeweils 1-9: $9^4$ 
   Also: $10\cdot9^4=10\cdot6561=65610$  
4. Gegeben ist die Zahl $a = 7$ in $Z_{23}$ 
   (a) Besitzt $a$ eine multiplikative Inverse? Begründen Sie ihre Antwort (3P)
   A: ggT(7, 23) = 1 -> Es existiert ein multiplikatives Inverse, da $7$ und $23$ teilerfremd sind.
   (b) Berechnen Sie die multiplikative Inverse mittels des erweiterten Euklidischen Algorithmus. (12P)
   A: 

| k   | r         | q        | x                 | y              |
| --- | --------- | -------- | ----------------- | -------------- |
| 0   | 7         | -        | 1                 | 0              |
| 1   | 23        | -        | 0                 | 1              |
| 2   | $7\%23=7$ | $7/23=0$ | $1-0\cdot 0=1$    | $0-0\cdot 1=0$ |
| 3   | $23\%7=2$ | $23/7=3$ | $0-3\cdot1=-3$    | $1-3\cdot0=1$  |
| 4   | $7\%2=1$  | $7/2=3$  | $1-3\cdot(-3)=10$ | $0-3\cdot1=-3$ |
| 5   | $2\%1=0$  | -        | -                 | -              |
Multiplikatives Inverse: $7\cdot10\equiv1 \mod 23$ 
5. Berechnen Sie die Prüfziffer nach dem ISBN-10-Code für die folgende ISBN (5P)
   ISBN=3-540-25782-p
   $10\cdot3+9\cdot5+8\cdot4+6\cdot2+5\cdot5+4\cdot7+3\cdot8+2\cdot2=200$ 
   $200 + p \equiv 0 \mod{11}$
   $2+p\equiv0\mod{11}$ 
   $2+9\equiv0\mod{11}$
   $p=9$
   ISBN mit Prüfziffer: 3-540-25782-9
6. Bei einem RSA-Algorithmus werden die Primzahlen $p=7$ und $q=9$ gewählt. Zur Verschlüsselung dient der Wert $e=5$.
   (a) Wie lautet der öffentliche Schlüssel? (3P)
   A: $n=p\cdot q=63$ 
   Öffentlicher Schlüssel=$(63,5)$ 
   (b) Die Buchstaben $\{a,b,c,\dots,z\}$ werden durch die Zahlen $\{0,1,2,\dots,25\}$ dargestellt. Verschlüsseln Sie unter dieser Rahmenbedingung die Buchstaben $c$ und $d$. (2P)
   A: Verschlüsselung für c = $2^5 \mod{63} =32$, Verschlüsselung für d = $3^5 \mod{63}=54$ 
   (c) Ermitteln Sie $d=e^{-1}$. (5P)
   A: $d = 5^{-1} \mod{\varphi}$ 
   $\varphi=(7-1)\cdot(9-1)=48$ 

| k   | r         | q        | x                   | y                |
| --- | --------- | -------- | ------------------- | ---------------- |
| 0   | 5         | -        | 1                   | 0                |
| 1   | 48        | -        | 0                   | 1                |
| 2   | $5\%48=5$ | $5/48=0$ | $1-0\cdot0=1$       | $0-0\cdot1=0$    |
| 3   | $48\%5=3$ | $48/5=9$ | $0-9\cdot1=-9$      | $1-9\cdot0=1$    |
| 4   | $5\%3=2$  | $5/3=1$  | $1-1\cdot-9=10$     | $0-1\cdot1=-1$   |
| 5   | $3\%2=1$  | $3/2=1$  | $(-9)-1\cdot10=-19$ | $1-1\cdot(-1)=2$ |
| 6   | $2\%1=0$  |          |                     |                  |
$ggT(e,\varphi)=1$ 
$5 \cdot (-19)\equiv1\mod48$ 
$d = -19 \mod{48} \rightarrow d=29$
(d) Zusatzaufgabe: Sie erhalten den verschlüsselten Wert 4. Entschlüsseln Sie diesen und ordnen Sie den Buchstaben zu. (6P)
A: Entschlüsselter wert 4 = $4^29 \mod{63}=16$ welches dem Buchstaben $q$ entspricht.
7. Lösen Sie folgendes System von Kongruenzen. (10P)
   $x_1\equiv4\pmod{5}$, $x_2\equiv0\pmod{9}$, $x_3\equiv3\pmod{11}$ 
   Schritt 1: $M = 5\cdot9\cdot11=495$
   Schritt 2: $M_1=\frac{495}{5}=99$, $M_2=\frac{495}{9}=55$, $M_3=\frac{495}{11}=45$
   Schritt 3: $M_1^{-1} \equiv 1 \pmod{5}$, $M_2^{-1}\equiv1\pmod{9}$, $M_3^{-1}\equiv1\pmod{11}$
   Schritt 4:    