# Activitat 4.5 — break, continue i bucles niuats

## Objectiu

Practicar l'ús de `break` i `continue` i el comportament dels bucles `for` niuats.

## Avaluació

Aquesta activitat s'avalua amb APTE / NO APTE.

## Enunciat

1. Escriu un `for` sobre `range(1, 21)` que s'aturi (amb `break`) just quan trobi el primer múltiple de `7`, i que imprimeixi aquest número.
2. Escriu un `for` sobre `range(1, 21)` que imprimeixi tots els números **excepte** els múltiples de `3` (fent servir `continue`).
3. Escriu dos bucles `for` niuats que imprimeixin totes les combinacions `(fila, columna)` per a `fila` de `0` a `2` i `columna` de `0` a `1` (6 combinacions en total).
4. Sobre el mateix bucle niuat de l'exercici 3, afegeix un `break` dins del bucle intern quan `columna == 1`, i explica per escrit què canvia respecte al resultat de l'exercici 3 (quantes combinacions s'imprimeixen ara).
5. Sense executar-ho, prediu per escrit què imprimeix aquest fragment i després comprova-ho:

```python
for i in range(3):
    for j in range(3):
        if j == i:
            break
        print(i, j)
```

## Depuració amb VSCode

El següent codi hauria d'aturar-se completament en trobar el primer número negatiu de la llista, però continua processant la resta:

```python
dades = [4, 8, -2, 6, -5, 3]
for n in dades:
    if n < 0:
        continue
    print("Processant:", n)
```

1. Posa un breakpoint a la línia de l'`if` i executa amb F5.
2. Fes "step over" i observa què fa el programa quan `n` val `-2`.
3. Identifica quina paraula clau s'hauria d'utilitzar en comptes de la que hi ha.
4. Corregeix-ho i explica per escrit (2-3 línies) la diferència de comportament entre les dues paraules clau.

## Com entregar-ho

Un fitxer `.py` amb els 5 exercicis i el codi corregit, més una captura de pantalla del depurador aturat quan `n` val `-2`.
