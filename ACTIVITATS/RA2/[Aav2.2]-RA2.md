# Activitat 2.2 — Condicionals niuats i primers passos amb strings

## Objectiu

Practicar condicionals niuats i les operacions bàsiques d'indexació i slicing sobre strings.

## Avaluació

Aquesta activitat s'avalua amb APTE / NO APTE.

## Enunciat

1. Escriu un condicional **niuat** que, donat un número enter `x`, imprimeixi:
   - `"Positiu i parell"` si és positiu i parell.
   - `"Positiu i senar"` si és positiu i senar.
   - `"Zero"` si és 0.
   - `"Negatiu"` si és negatiu.
   Prova-ho amb `x = 8`, `x = 7`, `x = 0` i `x = -3`.

2. Reescriu l'apartat 1 (només el cas "positiu") **sense niuar**, utilitzant `and` en una sola condició `if`. Comprova que dona el mateix resultat.

3. Donat `paraula = "programacio"`:
   - Imprimeix el primer i l'últim caràcter (amb índex negatiu).
   - Imprimeix els 4 primers caràcters amb slicing.
   - Imprimeix la paraula al revés amb slicing (`[::-1]`).
   - Imprimeix els caràcters de dos en dos (`paraula[::2]`).

4. Sense executar-ho, indica què creus que passarà amb `paraula[0] = "P"` (canviar el primer caràcter). Executa-ho per comprovar-ho i explica per escrit (1 línia) per què passa això.

## Depuració amb VSCode

Aquest codi hauria d'imprimir la primera lletra de `nom` en majúscules, però llança un error:

```python
nom = "marta"
inicial = nom[1].upper()
print(f"Inicial: {inicial}")
```

1. Posa un breakpoint a la línia de `inicial = ...`.
2. Executa el depurador i, amb "step into" o mirant la finestra de variables, comprova quin caràcter conté realment `nom[1]`.
3. Identifica per què el resultat no és la inicial correcta (no és un error que Python aturi amb excepció, és un error de lògica).
4. Corregeix-lo i explica en 2-3 línies quina era la confusió (pista: recorda per quin número comencen els índexs).

## Com entregar-ho

Un fitxer `.py` amb els 4 exercicis i el codi corregit de la depuració, més una captura del depurador amb la finestra de variables oberta mostrant el valor de `nom[1]`.
