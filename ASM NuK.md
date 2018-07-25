# n über k in asm

Von André M. und Jonas P.

n über k = n! /(k! (n-k)! )

Bitte beachtet, die Syntax der asm Befehle hängt unteranderem vom Mikrocontroller ab

Annahmen: 

- In Register 1 steht n
- In Register 2 steht k
- in Register 3 soll das Ergebniss stehen
- Es soll eine "Methode" zur Fakultätsberechnung geben
- Kommentare mit //



## Fakultät

- In Register 4 steht die zu fakultierende Zahl
- Das Ergebniss wird in Register 5 gespeichert

```Asm
factory: 
	mov r5, #1 // Standartwert 0!=1 -1!=NICHT DEFINIERT
	loop:
		cmp r4,#0 // Vergleichen des Werts in r4 mit 0
		ittt gt  // Wenn größer als 0 i->if ttt -> drei anweisungen 
			mul gt r5,r4  
			sub gt r4, #1 // Entspricht n-1
			bl loop //Zurück zu loop
		blx lt  //Zurück zur Abrufenden stelle 
	
	
```

## Abrufen

````Asm
//n!
mov r4,r1 // n in r4 laden
bl faculty //fakultäts funktion aufrufen
mov r3,r5  // das errechnete Ergebniss in r3 ablegen
//In r3 steht nun n!

//k!
mov r4,r2
bl factory
mov r6,r5
//In r6 steht nun k!

//(n-k)!
mov r4,r1
sub r4,r2 //n-k
bl factory
//In r5 steht nun (n-k)!

//k!(n-k)!
mul r6,r5
// In r6 stegt jetzt k!(n-k)!

//n!/(k!(n-k)!)
div r3,r6
//In r3 steht das Ergebniss von n über k
````

