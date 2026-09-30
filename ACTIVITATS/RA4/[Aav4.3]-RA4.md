# Activitat 4.3 — Cerca i validació amb for

## Objectiu

Practicar els patrons de cerca amb bandera (*flag*) i de validació de tots els elements d'una seqüència.

## Avaluació

Aquesta activitat s'avalua amb APTE / NO APTE.

## Enunciat

Donada la llista `inventari = ["cable", "carregador", "auriculars", "funda"]`:

1. Demana a l'usuari un nom de producte amb `input()` i, amb un `for` i una variable booleana, comprova si és a l'`inventari`. Imprimeix `"Trobat"` o `"No trobat"`.
2. Fes el mateix exercici, però ara sense `for`, fent servir directament l'operador `in`. Comprova que dona el mateix resultat.
3. Donada `edats = [22, 19, 17, 25, 20]`, escriu un `for` amb una variable `tots_majors` que acabi valent `True` només si totes les edats són `>= 18`.
4. Sobre la mateixa llista `edats`, compta amb un `for` quantes persones són menors de `18`.
5. Calcula el mínim d'`edats` "a mà" amb un `for` (patró acumulador amb comparació, com el màxim de l'activitat anterior però al revés).

## Depuració amb VSCode

El següent codi hauria de dir si `"funda"` és a l'inventari, però sempre diu `"No trobat"` encara que hi sigui:

```python
inventari = ["cable", "carregador", "auriculars", "funda"]
trobat = False
for article in inventari:
    if article == "funda":
        trobat = False
print("Trobat" if trobat else "No trobat")
```

1. Posa un breakpoint dins de l'`if` i executa amb F5.
2. Fes "step over" i mira com canvia (o no) el valor de `trobat` a la finestra de variables quan `article` val `"funda"`.
3. Identifica la línia exacta que impedeix que `trobat` es marqui correctament.
4. Corregeix-ho i explica per escrit (2-3 línies) la causa del bug.

## Com entregar-ho

Un fitxer `.py` amb els 5 exercicis i el codi corregit, més una captura de pantalla del depurador aturat quan `article` val `"funda"`.
