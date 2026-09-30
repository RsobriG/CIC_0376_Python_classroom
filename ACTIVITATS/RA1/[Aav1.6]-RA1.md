# Activitat 1.6 — Operadors i expressions

## Objectiu

Practicar operadors aritmètics, de comparació i lògics, i la precedència entre ells.

## Avaluació

Aquesta activitat s'avalua amb APTE / NO APTE.

## Enunciat

1. Calcula i mostra el resultat de `17 // 5`, `17 % 5` i `17 / 5`. Explica la diferència entre els tres.
2. Calcula `-17 // 5` i `-17 % 5`. Compara amb l'exercici anterior: què canvia amb un operand negatiu?
3. Declara `a = 5`, `b = 10`, `c = 15` i, sense usar `if`, calcula en una sola expressió booleana si `a < b and b < c`. Mostra el resultat i el seu tipus.
4. Calcula el resultat de `2 + 3 * 4 ** 2` sense usar parèntesis, i després reescriu la mateixa expressió (mateixos números i operadors: `2`, `+`, `3`, `*`, `4`, `**`, `2`) afegint-hi parèntesis perquè el resultat sigui `80`.
5. Prova `5 > 3 and 2 > 4 or 1 == 1` i explica per escrit, pas a pas, com s'avalua (precedència: `and` abans que `or`).

## Depuració amb VSCode

El següent codi hauria de calcular la mitjana de tres notes i dir si l'alumne aprova (mitjana >= 5),
però sempre diu que no aprova encara que la mitjana sigui prou alta:

```python
nota1 = 6
nota2 = 7
nota3 = 8
mitjana = nota1 + nota2 + nota3 / 3
aprova = mitjana >= 5
print(f"Mitjana: {mitjana}, aprova: {aprova}")
```

1. Posa un breakpoint a la línia `mitjana = ...` i executa amb `F5`.
2. Fes "step over" i mira, al panell "Variables", quin valor pren `mitjana` (segurament un número molt
   més gran del que esperaves).
3. Identifica quin operador s'està aplicant abans del que tocaria, a causa de la precedència
   d'operadors.
4. Corregeix el codi (amb parèntesis) perquè `mitjana` sigui realment la mitjana de les tres notes.
5. Explica per escrit (2-3 línies) quina regla de precedència provocava el bug.

## Com entregar-ho

Fitxer `.py` amb els exercicis i una captura del panell "Variables" mostrant el valor incorrecte de `mitjana` abans de corregir-lo.
