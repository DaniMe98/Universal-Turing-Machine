# Universal-Turing-Machine
A simple UTM implemented in JFlap 8.0 for Turing Machine that accept unary language only.

MACCHINA DI TURING UNIVERSALE – DANILO MELELEO 

La macchina lavora su 3 nastri, il primo contiene la macchina da simulare codificata in una stringa di 0,1,$ il secondo nastro contiene l’input su cui la macchina nel nastro uno deve operare, e sul terzo nastro verranno copiate di volta in volta tutte le transizioni richieste.

La codifica delle transizioni delle macchine da simulare deve essere fatta nel seguente modo:
![](https://github.com/DaniMe98/Universal-Turing-Machine/blob/master/docs/utm.png)

dove • σr indica il carattere letto dalla stringa di input,
(1 sta per 0, 11 sta per 1) ,

• σw indica il carattere da scrivere al posto di σr (1 sta per 0, 11 sta per 1, 111 sta per blank), 

• op.code indica la mossa della testina sul nastro 2 (1=Right,11=left),

• q_out indica la prossima transizione da cercare.

Le transizioni sono definite in blocchi da 3(una per ogni carattere che la UTM puo leggere dal nastro 2, dove c’è l’input) 
,sulle transizioni è definito un ordine totale quindi ogni volta per cercare una transizione si fa un rewind del nastro 1 e si cerca la transizione, 
una volta trovata la prossima transizione, la transition search unit cercherà la prossima transizione sulla base del carattere di input (se il prossimo carattere da analizzare è 0 sceglie la prima transizione disponibile, se 1 la seconda, se blank la terza) dopo di che l’unità di copia,
copierà la transizione sul nastro 3 e passa alla transition analizer, che effettua le operazioni scritte sulla transizione del nastro 3,
alla fine delle operazioni se nel q_out abbiamo il simbolo $ significa che abbiamo raggiunto lo stato finale, o quello di errore nel caso di doppio $$, quindi l’esecuzione termina.

## Macchine su cui è stata testata:
•	10110101001101010100101011011001011010$0011010110110010101101100      effettua il complemento a 2 di un qualsiasi numero binario

•	1011010110011011010100101010100101010110011011010110010101101110010101011001101010$00101011011100 addizione unaria senza pulire il nastro input (formato input 11101)

•	101101011001101101010010101010010101011001101101011001010110111001010101100110111010$00101011011100 addizione unaria con pulitura nastro input 

•	101010110011011010100101010100101010110011010110111001010110$00101011011100110101011001010110$00 sottrazione unaria senza pulitura nastro input (formato input 1101)

•	10101011001101101010010101010010101011001101011011100101011011110010101101110011010101100101011011110010111011011110011011010$001010110111100 
sottrazione unaria con pulitura nastro

## ATTENZIONE:
dato il grande numero di transizioni, potrebbe uscire il seguente messaggio su jflap:
![](https://github.com/DaniMe98/Universal-Turing-Machine/blob/master/docs/utm2.png)
![](https://github.com/DaniMe98/Universal-Turing-Machine/blob/master/docs/ut3.png)

in tal caso basta premere “SI” e continuare.
