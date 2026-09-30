# Activitat 1.4 — Variables, tipus i conversió

## Objectiu

Practicar la declaració de variables, els tipus bàsics i la conversió entre tipus (*casting*).

## Avaluació

Aquesta activitat s'avalua amb APTE / NO APTE.

## Enunciat

1. Declara quatre variables: una `int`, una `float`, una `str` i una `bool`. Mostra el valor i el tipus (`type()`) de cadascuna amb `print()`.
2. Declara `preu_text = "12.50"` i calcula `preu_text` més IVA (21%) com a número, mostrant el resultat com a `float`.
3. Declara `edat = 17` i calcula, sense fer servir `if`, si la persona és major d'edat (`edat >= 18`), guardant el resultat en una variable `es_major` i mostrant-ne el tipus.
4. Prova (i explica el resultat) què retorna `bool(0)`, `bool(1)`, `bool("")`, `bool("False")` i `bool("0")`.
5. Prova què passa si fas `"5" + 5` directament (sense convertir) i explica l'error que dona.

## Depuració amb VSCode

El següent codi hauria de calcular el preu total (preu + IVA) però dona un `TypeError`:

```python
preu = "20"
iva = 0.21
total = preu + (preu * iva)
print(f"Total: {total}")
```

1. Posa un breakpoint a la línia `total = ...` i executa amb `F5`.
2. Al panell "Variables", comprova el tipus real de `preu` (fixa't que apareix entre cometes: és un
   `str`, no un número).
3. Fes "step over" i observa l'error exacte que es produeix.
4. Corregeix el codi convertint `preu` al tipus adequat, i torna a executar per comprovar que ara
   funciona.
5. Explica per escrit (2-3 línies) per què el codi original fallava encara que `preu` "sembli" un
   número.

## Com entregar-ho

Fitxer `.py` amb els 5 exercicis i una captura del panell "Variables" de VSCode mostrant el tipus de `preu` abans de corregir el bug.
