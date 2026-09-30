# Activitat 4.4 — Transformació de strings i llistes amb for

## Objectiu

Practicar la construcció d'un nou string o d'una nova llista recorrent-ne un altre amb `for`.

## Avaluació

Aquesta activitat s'avalua amb APTE / NO APTE.

## Enunciat

1. Donat `text = "Institut CIC"`, construeix amb un `for` un nou string amb totes les lletres en majúscules, sense fer servir `.upper()` sobre tot el string (fes-ho lletra a lletra amb `.upper()` sobre cada caràcter).
2. Donada `paraules = ["sol", "cotxe", "mar", "bicicleta", "flor"]`, construeix una nova llista `llargues` amb només les paraules de més de 3 lletres.
3. Donada la mateixa llista, construeix una nova llista `longituds` amb la longitud de cada paraula (en el mateix ordre).
4. Donat `frase = "el sol surt cada dia"`, compta amb un `for` quants caràcters `"a"` hi ha (fixa't que `.count("a")` fa el mateix; fes-ho igualment "a mà" per practicar).
5. Intenta fer `text[0] = "i"` i explica en un comentari quin error dona i per què.

## Depuració amb VSCode

El següent codi hauria de retornar el string `"NOHTYP"` (Python en majúscules i invertit), però no ho fa bé:

```python
text = "python"
resultat = ""
for c in text:
    resultat = c.upper() + resultat
print(resultat)
```

1. Posa un breakpoint dins del `for` i executa amb F5.
2. Fes "step over" a cada volta i mira com creix `resultat` a la finestra de variables.
3. Identifica si el resultat s'assembla al que es demana o no, i per què.
4. Si cal, corregeix el codi i explica per escrit (2-3 línies) què fa realment aquesta construcció.

## Com entregar-ho

Un fitxer `.py` amb els 5 exercicis i l'anàlisi/correcció de la depuració, més una captura de pantalla del depurador mostrant l'evolució de `resultat`.
