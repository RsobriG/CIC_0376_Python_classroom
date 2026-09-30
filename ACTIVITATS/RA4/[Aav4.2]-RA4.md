# Activitat 4.2 — Sumatoris i comptadors amb for

## Objectiu

Practicar el patró acumulador (suma, mitjana, comptador condicional) recorrent llistes numèriques amb `for`.

## Avaluació

Aquesta activitat s'avalua amb APTE / NO APTE.

## Enunciat

Donada la llista `vendes = [120, 85, 200, 40, 150, 95]` (vendes en euros de 6 dies):

1. Calcula i imprimeix la suma total de vendes amb un `for`.
2. Calcula i imprimeix la mitjana de vendes (recorda: la divisió amb `/` sempre retorna `float`).
3. Compta i imprimeix quants dies s'ha venut més de 100 €.
4. Calcula, sense fer servir `max()`, el valor més alt de la llista (patró "acumulador amb comparació": guarda el més gran vist fins ara).
5. Explica en un comentari per què `sum(vendes) / len(vendes)` fa exactament el mateix que l'exercici 2 sense necessitat de `for`.

## Depuració amb VSCode

El següent codi hauria de sumar totes les vendes, però dona un error:

```python
vendes = [120, 85, 200, 40, 150, 95]
for v in vendes:
    total += v
print(total)
```

1. Posa un breakpoint a la línia `total += v` i executa amb F5.
2. Mira l'error que apareix a la consola de depuració de VSCode just en arrencar.
3. Identifica quina línia falta i per què el programa no pot arrencar sense ella.
4. Corregeix-ho i explica per escrit (2-3 línies) la causa del bug.

## Com entregar-ho

Un fitxer `.py` amb els 5 exercicis i el codi corregit, més una captura de pantalla de la consola de depuració de VSCode mostrant l'error original.
