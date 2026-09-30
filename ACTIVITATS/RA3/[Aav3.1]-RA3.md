# Activitat 3.1 — Comptar i repetir amb `while`

## Objectiu

Practicar l'estructura bàsica d'un bucle `while`, predir quantes vegades s'executa i utilitzar `break`.

## Avaluació

Aquesta activitat s'avalua amb APTE / NO APTE.

## Enunciat

Crea un fitxer `activitat_3_1.py` i resol els apartats següents (cada apartat, un bloc de codi separat
amb un comentari `# Apartat X`):

1. Escriu un `while` que mostri per pantalla els números del `10` al `1` (en ordre descendent), i
   després mostri el missatge `"Compte enrere acabat"`.
2. Sense executar-lo encara, escriu en un comentari quantes vegades creus que s'executarà el cos del
   `while` següent i quin serà l'últim valor que s'imprimeixi. Després, executa'l i comprova si
   encertaves:
   ```python
   x = 0
   while x < 4:
       print(x)
       x += 1
   ```
3. Escriu un `while True:` que vagi demanant un número per teclat (`input`) fins que l'usuari
   introdueixi el número `0`; en aquest cas, fes `break` i mostra `"Fi"`.
4. Modifica l'apartat 1 perquè, en comptes de mostrar tots els números, s'aturi (amb `break`) just quan
   arribi al `5`, mostrant abans un missatge `"Aturat a la meitat"`.

## Depuració amb VSCode

El codi següent hauria de mostrar els números de l'1 al 5, però **no s'atura mai** (bucle infinit):

```python
i = 1
while i <= 5:
    print(i)
```

1. Copia aquest codi a `debug_3_1.py`, posa-hi un breakpoint a la línia del `print(i)`.
2. Executa amb el depurador (F5) i fes "step over" diverses vegades, mirant a la finestra de **Variables**
   com evoluciona (o no) el valor de `i`.
3. Identifica exactament per què `i` no canvia mai de valor.
4. Corregeix el codi i torna a comprovar-ho amb el depurador (has d'arribar a l'estat "programa acabat").
5. Explica per escrit (2-3 línies) quina era la causa del bucle infinit.

## Com entregar-ho

Un fitxer `.py` per apartat (o un de sol ben comentat) més el fitxer `debug_3_1.py` corregit, i una
captura de pantalla del depurador de VSCode aturat en el breakpoint amb la finestra de Variables visible.
