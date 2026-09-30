# Activitat 6.3 — Recorreguts de diccionaris

## Objectiu

Practicar el recorregut de diccionaris amb `for` fent servir `.keys()`, `.values()` i `.items()`, i
treballar amb un diccionari niuat senzill.

## Avaluació

Aquesta activitat s'avalua amb APTE / NO APTE.

## Enunciat

Es dona el següent diccionari d'estoc d'una botiga:

```python
estoc = {
    "teclat": 12,
    "ratolí": 30,
    "monitor": 5,
    "auriculars": 0,
}
```

1. Recorre `estoc` amb un `for` senzill (sense `.keys()` ni `.items()`) i imprimeix cada nom de
   producte.
2. Recorre `estoc.values()` i suma tots els valors en una variable `total_unitats`; imprimeix el total.
3. Recorre `estoc.items()` i imprimeix una línia per producte amb el format `"{producte}: {unitats}
   unitats"`.
4. Utilitzant el mateix recorregut amb `.items()`, imprimeix únicament els productes que tenen
   `estoc == 0` (productes exhaurits).
5. Ara es dona aquest diccionari niuat amb dades de tres alumnes:

```python
alumnes = {
    "a1": {"nom": "Pol", "notes": [6, 7, 8]},
    "a2": {"nom": "Aina", "notes": [9, 9, 10]},
    "a3": {"nom": "Iu", "notes": [4, 5, 6]},
}
```

   Recorre `alumnes.items()` i, per a cada alumne, imprimeix el nom i la mitjana de les seves notes
   (fes servir `sum()` i `len()` sobre la llista `"notes"`).

## Depuració amb VSCode

El següent codi hauria d'imprimir quants productes de `estoc` estan exhaurits (`0` unitats), però
sempre dona `0` encara que n'hi ha un:

```python
estoc = {"teclat": 12, "ratolí": 30, "monitor": 5, "auriculars": 0}

exhaurits = 0
for producte in estoc.keys:
    if estoc[producte] == 0:
        exhaurits += 1

print("Productes exhaurits:", exhaurits)
```

1. Posa un breakpoint a la línia del `for`.
2. Executa el depurador: abans de fer *step*, mira si el programa arriba a arrencar-se o dona error
   immediatament (fixa't en el missatge de la consola de depuració).
3. Identifica la línia i el motiu exacte de l'error (relaciona'l amb la diferència entre `.keys` i
   `.keys()` explicada a la teoria).
4. Corregeix el codi i comprova que ara el resultat és `1`.
5. Explica en 2-3 línies la causa del bug.

## Com entregar-ho

Un fitxer `.py` amb els 5 exercicis i un segon fitxer `.py` amb el codi corregit de la part de
depuració, més una captura de pantalla de la consola de depuració de VSCode mostrant l'error abans de
corregir-lo.
