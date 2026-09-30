# Activitat 4.6 — Problemes integradors I (for + condicionals)

## Objectiu

Resoldre problemes que combinen `for`, `range()`, acumuladors i condicionals, practicant la traça de codi a mà com a l'examen PE1.

## Avaluació

Aquesta activitat s'avalua amb APTE / NO APTE.

## Enunciat

1. Sense executar-ho, fes la traça a mà (taula amb `i`, condició, valor de `total`) i prediu el resultat final:

```python
total = 0
for i in range(1, 10):
    if i % 2 == 0:
        continue
    if i > 7:
        break
    total += i
print(total)
```

   Comprova després el resultat executant-ho.

2. Donada `notes = [3, 7, 9, 2, 6, 8, 5]`, escriu un `for` que compti quants aprovats (`>= 5`) hi ha **però que s'aturi** en trobar el primer suspens (`< 5`) després d'haver comptat almenys 2 aprovats.
3. Classifica els números de l'1 al 30 en `multiples_3`, `multiples_5` i `altres` (tres llistes buides que vas omplint dins un sol `for` amb `if`/`elif`/`else`). Un número que sigui múltiple de tots dos (3 i 5) ha d'anar només a `multiples_3`.
4. Calcula quants números de l'1 al 100 són múltiples de 3 **o** de 5 (fes servir `or` dins l'`if`).
5. Explica per escrit en quin ordre s'han de comprovar les condicions de l'exercici 3 perquè un múltiple de 15 no acabi duplicat ni mal classificat.

## Depuració amb VSCode

El següent codi hauria de comptar quants números de la llista són positius, però dona un resultat incorrecte:

```python
nombres = [5, -3, 8, -1, 0, 6]
positius = 0
for n in nombres:
    if n > 0:
        positius = 1
print(positius)
```

1. Posa un breakpoint a la línia `positius = 1` i executa amb F5.
2. Fes "step over" cada cop que s'hi entri i observa el valor de `positius` a la finestra de variables.
3. Identifica per què `positius` no acumula els comptatges.
4. Corregeix-ho i explica per escrit (2-3 línies) la causa del bug.

## Com entregar-ho

Un fitxer `.py` amb els 5 exercicis (inclosa la taula de traça de l'exercici 1 en comentari) i el codi corregit, més una captura de pantalla del depurador.
