# Com depurar (debugar) codi Python amb VSCode

Depurar vol dir **aturar l'execució d'un programa a un punt concret i observar, pas a pas, què val
cada variable**, en comptes d'intentar endevinar l'error només llegint el codi. És una habilitat que
farem servir a **totes les activitats del curs**, i que també t'ajuda directament a l'examen PCEP (PE1):
moltes preguntes de l'examen et donen un fragment de codi i et demanen "quin és el valor de X en
aquest punt" — depurar pas a pas és exactament practicar aquest raonament amb l'ordinador al davant
en comptes de fer-ho de cap.

## 1. Conceptes bàsics

* **Breakpoint (punt de ruptura):** una marca en una línia de codi que diu a VSCode "quan arribis
  aquí, atura't abans d'executar-la". El programa es queda "pausat" en aquell punt.
* **Step Over (F10):** executa la línia actual sencera (sense entrar dins de funcions que cridi) i
  passa a la següent.
* **Step Into (F11):** si la línia actual crida una funció, "entra" dins d'aquesta funció per veure-la
  executar-se pas a pas.
* **Step Out (Shift+F11):** surt de la funció actual i torna a on l'havies cridat.
* **Continue (F5):** reprèn l'execució normal fins al proper breakpoint (o fins que el programa acabi).
* **Variables:** panell que mostra, en temps real, el valor de totes les variables actives mentre el
  programa està pausat.
* **Watch:** una llista de variables o expressions que tu tries i que es mostren sempre, encara que no
  siguin al panell "Variables" per defecte (útil per vigilar una expressió concreta, p. ex. `len(llista)`).
* **Call Stack (pila de crides):** mostra la cadena de funcions que s'han anat cridant fins arribar al
  punt on estàs aturat (útil quan l'error passa dins d'una funció cridada per una altra).
* **Debug Console:** una consola interactiva que apareix quan el programa està pausat, on pots escriure
  expressions Python i veure el resultat immediatament AMB els valors reals que tenen les variables en
  aquell instant (p. ex. escriure `preu * 2` i veure el resultat sense haver de modificar el codi).

## 2. Posar un breakpoint

1. Obre el fitxer `.py` a VSCode.
2. Clica a l'espai buit **just a l'esquerra del número de línia**, a la línia on vols que el programa
   s'aturi. Hi apareixerà un punt vermell.
3. Per treure'l, torna a clicar sobre el punt vermell.

**On posar el breakpoint?** Posa'l a la primera línia "sospitosa" — normalment just abans d'on
apareix el resultat incorrecte, o a la primera línia d'un bucle si vols veure com canvien les
variables a cada volta.

## 3. Executar en mode depuració

1. Amb el fitxer obert i almenys un breakpoint posat, prem **F5** (o clica la icona de "Run and
   Debug" a la barra lateral esquerra i després "Run and Debug" → "Python File").
2. Si és el primer cop que ho fas en aquest projecte, VSCode et preguntarà quin tipus de configuració
   vols: tria **"Python File"** (l'opció més senzilla, executa el fitxer que tens obert).
3. El programa s'executarà normalment fins arribar a la línia del breakpoint, i s'hi aturarà. La línia
   quedarà ressaltada (normalment en groc/blau).

## 4. Inspeccionar variables mentre el programa està pausat

Amb el programa aturat en un breakpoint:

* Mira el panell **Variables** (barra lateral esquerra, secció "VARIABLES") — hi veuràs totes les
  variables locals amb el seu valor actual.
* Passa el ratolí per sobre de qualsevol variable **dins del codi** — apareixerà un requadre amb el
  seu valor.
* Afegeix una expressió al panell **WATCH** (clica el `+`) si vols vigilar una cosa concreta, com
  `total` o `i < len(llista)`.
* Escriu qualsevol expressió Python vàlida a la **Debug Console** (part inferior) i prem Enter per
  veure'n el resultat immediatament amb els valors reals del moment.

## 5. Avançar pas a pas

* **F10 (Step Over):** avança una línia. Fes-ho servir per anar veient com evolucionen les variables
  línia a línia, sobretot dins de bucles (`while`/`for`).
* **F11 (Step Into):** si la línia crida una funció teva i vols veure què passa exactament a dins.
* **Shift+F11 (Step Out):** quan ja has vist prou d'una funció i vols tornar a fora.
* **F5 (Continue):** si vols saltar fins al proper breakpoint (útil dins d'un bucle llarg: posa el
  breakpoint dins del bucle i prem F5 repetidament per anar "volta a volta").

## 6. Breakpoints condicionals (útils per a bucles llargs)

Si un bucle fa 1000 voltes i el bug només passa a la volta 743, no té sentit prémer F10 mil vegades.

1. Clica amb el botó dret sobre un breakpoint ja posat.
2. Tria **"Edit Breakpoint..."**.
3. Escriu una condició, per exemple `i == 743` o `total < 0`.
4. Ara el programa només s'aturarà quan aquesta condició sigui certa.

## 7. Exemple pas a pas

```python
def mitjana(notes):
    suma = 0
    for n in notes:
        suma = n          # <- posem un breakpoint aquí
    return suma / len(notes)

resultat = mitjana([6, 7, 5, 9])
print(resultat)
```

1. Posa un breakpoint a la línia `suma = n`.
2. Prem F5. El programa s'aturarà la primera vegada que arribi a aquesta línia (`n = 6`).
3. Mira el panell Variables: `suma` encara val `0`, `n` val `6`.
4. Prem F10: ara `suma` val `6`. Torna a passar pel bucle (F5 o F10 repetit) i veuràs que **`suma` no
   s'acumula mai** — a cada volta es SUBSTITUEIX pel valor de `n` en comptes de sumar-s'hi (falta un
   `+=` en comptes de `=`). Sense el depurador, aquest error és fàcil de passar per alt perquè el
   programa no llança cap excepció, simplement dona un resultat incorrecte.
5. Corregeix la línia a `suma += n`, treu el breakpoint (o deixa'l i prem F5 per confirmar) i torna a
   executar per comprovar que ara `resultat` val `6.75`.

Aquest tipus de bug (un error de lògica que no llança cap excepció) és exactament el que trobaràs a
la secció "Depuració amb VSCode" de cada activitat del curs.

## 8. Diferència entre "Run" (Ctrl+F5) i "Debug" (F5)

| | Ctrl+F5 (Run) | F5 (Debug) |
| :---- | :---- | :---- |
| Breakpoints | S'ignoren | S'aturen |
| Velocitat | Més ràpid | Una mica més lent (hi ha un procés extra vigilant) |
| Quan fer-lo servir | Quan el codi ja funciona i només vols veure el resultat final | Quan vols investigar per què el resultat NO és el que esperaves |

## 9. Errors habituals en depurar

| Símptoma | Causa | Solució |
| :---- | :---- | :---- |
| El programa s'executa sencer i no s'atura mai al breakpoint | Estàs executant amb Ctrl+F5 en comptes de F5, o el breakpoint és a una línia que mai s'arriba a executar (p. ex. dins d'un `if` que no es compleix) | Torna a comprovar que has premut F5 i que el breakpoint és dins del camí que realment segueix el codi |
| No apareix el panell de Variables | Estàs mirant la pestanya equivocada de la barra lateral | Clica la icona de "Run and Debug" (triangle amb un bug) a la barra lateral esquerra |
| "Just My Code" amaga el que passa dins de funcions de llibreries | Configuració per defecte de VSCode (normalment és el comportament desitjat) | Si necessites entrar dins del codi d'una llibreria, desactiva `justMyCode` a la configuració de depuració (`launch.json`) — no sol caldre en aquest curs |
| El valor d'una variable al panell Variables no canvia com esperes | Estàs mirant un àmbit (scope) equivocat, p. ex. una variable local d'una funció diferent | Comprova a quina funció estàs aturat (mira el Call Stack) abans de llegir el panell Variables |

A partir d'ara, **totes les activitats del curs inclouran una secció "Depuració amb VSCode"** on
hauràs d'aplicar aquests passos sobre un fragment de codi amb un bug real.
