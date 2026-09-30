# Activitat 5.1 — Creació i accés a llistes

## Objectiu

Practicar la creació de llistes, l'accés per índex (positiu/negatiu) i el slicing.

## Avaluació

Aquesta activitat s'avalua amb APTE / NO APTE.

## Enunciat

Crea un fitxer `activitat_5_1.py` i resol els exercicis següents (escriu els resultats amb `print()`):

1. Crea una llista `productes` amb almenys 6 noms de productes d'una botiga (strings).
2. Imprimeix el primer i l'últim producte de la llista, **fent servir índex negatiu** per a l'últim.
3. Imprimeix el nombre total de productes amb `len()`.
4. Imprimeix els **3 primers** productes fent servir slicing.
5. Imprimeix els productes **de l'índex 2 al final** fent servir slicing.
6. Imprimeix la llista **invertida** fent servir slicing amb pas -1 (sense usar `.reverse()`).
7. Crea una llista niuada `inventari` on cada element sigui una llista `[nom, preu]` (mínim 3
   productes) i imprimeix el preu del segon producte accedint amb doble índex (`inventari[1][1]`).
8. Intenta accedir a `productes[10]` (un índex que segur que no existeix) i escriu, en un comentari,
   quin error dona Python.

## Depuració amb VSCode

El fitxer `bug_5_1.py` (crea'l tu amb aquest contingut) té un error:

```python
productes = ["poma", "pera", "kiwi", "maduixa"]

def mostrar_ultim(llista):
    ultim = llista[len(llista)]
    print("L'últim producte és:", ultim)

mostrar_ultim(productes)
```

1. Obre `bug_5_1.py` a VSCode i posa un breakpoint a la línia de `ultim = llista[len(llista)]`.
2. Executa el depurador (F5) i, quan quedi aturat al breakpoint, mira al panell "Variables" el valor
   de `llista` i el que retornaria `len(llista)`.
3. Fes "Step Into"/"Step Over" per veure exactament on salta l'error.
4. Corregeix el bug i explica per escrit (2-3 línies) quina era la causa exacta (relaciona-ho amb el
   fet que els índexs van de 0 a `len(llista)-1`).

## Com entregar-ho

Un fitxer `.py` amb els 8 exercicis resolts, el fitxer `bug_5_1.py` corregit, l'explicació del bug, i
una captura de pantalla del depurador de VSCode aturat al breakpoint amb el panell de variables visible.
