

## Continued Fractions e Convergent
In matematica le *continued fractions*, sono un modo per poter scrivere un numero com somma della sua **parte intera** ed il reciproco di un certo numero. Chiaramente esso è un processo iterativo che termina dopo un numero finito di steps (generando quelle che sono *finite continued fraction*) oppure procedere all'infinito (*infinte continued fractions*). 
$$ a_0 +\frac{1}{a_1+\frac{1}{a_2+\frac{1}{...}}}$$

La parte intera è rappresentata dai coefficienti $a_{0}, a_{1},...,a_{n}$ . Un esempio esplicativo è il seguente: consideriamo il seguente numero $\frac{415}{93}$ che da come valore razionale il valore $4,4624$. Una prima approssimazione fissa il coefficiente 4, il quale è la parte intera; si veda il valore della parte *frazionale*, ovvero $0,4624$ che è possibile esprimere come $\frac{43}{93}$ . Un nuovo numero razionale, il quale reciproco è $\frac{93}{43} = 2.1628$ . Anche in questo caso possiamo scindere una parte intera ed una parte frazionale: la parte intera vale $2$ mentre la parte frazionale è possibile esprimerla come $\frac{7}{43}$. Otteniamo così ancora un numero razionale, ne consideriamo il reciproco, e reiteriamo il processo. Ci fermiamo quando otteniamo resto zero dalla parte frazionaria. Otteniamo quindi che il numero considerato è esprimibile come:

$$\frac{415}{93} = 4+\frac{1}{2+\frac{1}{6+\frac{1}{7}}}$$

dove i coefficienti visti prima sono 4,2,6 e 7. Se il numero di partenza è un numero razionale, allora il processo segue esattamente l' [[Euclidean Algorithm]] (da vedere poiché fatto durante il corso). 

Parliamo ora dei ***convergenti***. Tutto il ragionamento di prima si basa sul concetto di numero razionale(esprimibile esattamente come il rapporto di due numeri). Solo con questa tipologia di numeri si riesce ad ottenere una *finite continued fraction*, per i numeri che sono irrazionali si ottiene una *infinite continued fraction* il che comporta che l'algoritmo visto prima non termina mai. 

Se quindi il numero è irrazionale? In questo caso, la cosa figa che si può fare è cercare un'approssimazione del numero utilizzando le *continued fractions* e l'insieme dei coefficenti $[a_{0}, a_{1},...,a_{n}]$ . Come costruiamo questa approssimazione? Vediamone un esempio con il numero irrazionale $\pi$. Tale numero ha i seguenti coefficienti 
$$ [a_{0}, a_{1},...,a_{n}] = [3,7,15,1,292,1,1,1,2,…] $$ Partendo da questi valori posso costruire un'approssimazione razionale di $\pi$, utilizzando i convergenti (che "convergono" proprio al valore irrazionale). Definiamo quindi i convergenti per una *continued fraction* i primi quattro valori convergenti (chiaramente, numerati da 0 a 3) come: $$ c_0 = \frac{a_0}{1},\quad c_1 = \frac{a_1 a_0 +1}{a_1}, \quad c_2 = \frac{a_2 (a_1a_0 +1)+a_0}{a_2a_1 +1}, \quad c_3 = \frac{a_3(a_2 (a_1a_0 +1)+a_0)+(a_1a_0 +1)}{a_3(a_2a_1 +1)+a_1} $$
questi valori rappresentano una approssimazione del mio numero irrazionale.

![[convergent_approx.png]]
Per l'esempio di $\pi$ $$ [a_{0}, a_{1},...,a_{n}] = [3,7,15,1,292,1,1,1,2,…] $$
$$ c_0 = \frac{3}{1} = 3$$ $$\quad c_1 = \frac{22}{7}=3.142857$$$$c_2 = \frac{333}{106}=3.141509$$$$ c_3 = \frac{355}{113}=3.141593$$

Quindi man mano che aumentiamo l'indice dei convergenti troviamo una rappresentazione più precisa del numero irrazionale, ma razionale. Sorge una domanda spontanea: come si calcolano gli $a_i$ se non ho una frazione dalla quale partire? Si utilizzano metodi come il *Babylonian method*, ma, nella trattazione specifica dell'attacco partiremo da una frazione e da quella, ricaveremo poi i convergenti.

## RSA
Vediamo come è fatto RSA e come è possibile applicare quello che abbiamo visto a questa tipologia di crittografia asimmetrica.

RSA è un meccanismo di crittografia asimmetrica che considera il messaggio da inviare come un intero $x$ che appartiene ad un certo intervallo $[1, N-1]$ dato uno specifico $n$. Le operazioni di crittazione e decrittazione sono le seguenti:
$$ \displaylines{C = M^e mod \ N \\ M = C^d mod \ N } $$
dove la chiave pubblica è composta da $PU = \{e,\ N\}$ mentre la chiave privata sarà data da $PR = \{d,\ N\}$. $N$ , è un numero primo (solitamente molto grande), che risulta essere il prodotto tra due valori, $p$ e $q$ : $$N=p*q$$
Deve esistere una relazione tra $d$ ed $e$ affinché possa la seconda operazione essere vera. Si deve verificare che $e$ e $d$ siano **inversi moltiplicativi**, ovvero:
$$\displaylines{ \phi(n) = (p-1)(q-1)\\ d = e^{-1} mod\ \phi(N)}$$
Ciò vuol dire che deve esserci un valore $k$ tale per cui è possibile che si verifichi che:
$$\displaylines{ed = k \phi(N) + 1 \\ ed -k\phi(N) = 1}$$
da questa seconda relazione ricaviamo $\phi(N)$:
$$ \phi(N) = \frac{ed -1}{k}$$

## Fattorizzazione di $\phi(N)$
Ricordiamo che $N = pq$ e che il totiente di un numero primo è dato da $\phi(N)=(p-1)(q-1)$
quindi possiamo dire che

$$ \displaylines{\phi(N) = (p-1)(q-1) \\ = N-p-q+1 \\ =N-p-\frac{N}{p}+1}$$
e quindi, moltiplicando il tutto per $p$ otteniamo una equazione di secondo grado$$p^2+p(\phi(N)-N-1)+N =0$$ che sappiamo risolvere tranquillamente, trovando le radici $p_1 \ \text{e} \ p_2$ che compongono $N$.


## Approssimazione dei valori di $k$ e $d$ 
Definita la modalità di stima del totiente della funzione, concentriamoci ora sulla parte centrale di come l'attacco funziona.
Ricordando che $$\displaylines{ed -k\phi(N) = 1}$$ e compiendo dei calcoli banali algebrici, è possibile scrivere che 
$s_{11} = \left.\frac{b_1}{a_1}\right|_{a_2=0}$

$$\Bigg|\frac{e}{\phi(N)} - \frac{k}{d}\Bigg| = \frac{1}{d\phi(N)}$$
Quindi se il secondo membro dell'ultima è sufficientemente piccolo, il rapporto $\frac{k}{d}$ è una approssimazione razionale di $\frac{e}{\phi(N)}$ . Quindi essendo a conoscenza di quest'ultimo valore riusciamo a risalire alla chiave privata. Problema: l'attaccante non conosce il valore di $\phi(N)$ ma solo il valore di $e$ ed $N$. Ci sono alcune condizioni in cui posso derivare $\frac{k}{d}$ conoscendo solo $e$ ed $N$?

Questo viene descritto dal teorema di Wiener.

## Teorema di Wiener
Sia $N = pq$ con $q<p<2q$ . Sia inoltre $d< \frac{1}{3} N^{1/4}$. Allora, data una coppia $(e,\ N)$ è possibile ricavare il valore corretto di $\frac{k}{d}$ tra i convergenti di $\frac{e}{N}$.
## Procedura d'attacco
L'intera procedura di attacco si basa sui seguenti passaggi:
- data una coppia di valori $(e,\ N)$, verificare le condizioni di applicabilità del teorema di Wiener
- cercare dapprima i coefficienti dell'espansione in continued fractions di $\frac{e}{N}$;
- cercare i convergenti del rapporto $\frac{e}{N}$;
- utilizzando i convergenti, per ogni coppia $(k_i,\ d_i)$ provenienti dall'insieme degli stessi, valutare un possibile valore  di $\phi_i(N)$.
- trovare i possibili fattori che compongono $N$ risolvendo l'equazione del secondo ordine vista prima
- se il prodotto tra le radici di tale equazione è proprio pari ad $N$ allora le stime che ho fatto sui valori di $d$ ed $\phi(N)$ sono corrette. L'attacco è completo.

## Esempio