# Activitat 4.7 — Problemes integradors II (for + strings)

## Objectiu

Resoldre problemes que combinen `for` amb strings: comptar caràcters, invertir, detectar palíndroms.

## Avaluació

Aquesta activitat s'avalua amb APTE / NO APTE.

## Enunciat

1. Donada `paraula = "programar"`, compta amb un `for` quantes vocals (`aeiou`) té.
2. Escriu un `for` (sense `[::-1]`) que construeixi el string invertit de `paraula` fent servir `range()` amb `step` negatiu i concatenació.
3. Escriu una comprovació de palíndrom: donat `text = "anilina"`, compara'l amb el seu invertit (obtingut a l'exercici 2 o amb `[::-1]`) i imprimeix `True`/`False`.
4. Donada `frase = "el sol surt cada dia i el sol es pon cada nit"`, compta amb un `for` quantes vegades apareix la paraula `"sol"` (pista: primer separa la frase en paraules amb `.split()`, després recorre la llista resultant amb `for`).
5. Explica per escrit quina diferència hi ha entre comptar ocurrències de `"sol"` amb `frase.count("sol")` directament sobre l'string i fer-ho recorrent `frase.split()` amb un `for` — pensa en el cas d'una paraula que contingui `"sol"` com a part d'una altra paraula més llarga (per exemple `"solitud"`).

## Depuració amb VSCode

El següent codi hauria de dir si `"reconèixer"` (sense accent: `"reconeixer"`) és o no un palíndrom, però sempre diu que sí:

```python
text = "hola"
invertit = ""
for c in text:
    invertit = invertit + c
es_palindrom = (text == invertit)
print(es_palindrom)
```

1. Posa un breakpoint a la línia `invertit = invertit + c` i executa amb F5.
2. Fes "step over" cada volta i observa com es construeix `invertit`.
3. Identifica per què `invertit` acaba sent idèntic a `text` en comptes del seu revés.
4. Corregeix-ho i explica per escrit (2-3 línies) la causa del bug.

## Com entregar-ho

Un fitxer `.py` amb els 5 exercicis i el codi corregit, més una captura de pantalla del depurador mostrant com creix `invertit`.
