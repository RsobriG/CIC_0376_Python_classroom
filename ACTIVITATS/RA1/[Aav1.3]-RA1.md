# Activitat 1.3 — print(), comentaris i indentació

## Objectiu

Practicar la sintaxi bàsica de Python: `print()`, comentaris i la importància de la indentació.

## Avaluació

Aquesta activitat s'avalua amb APTE / NO APTE.

## Enunciat

1. Escriu un programa que mostri, amb un `print()` per línia, el teu nom, la teva ciutat i la teva edat.
2. Fes servir un únic `print()` amb diversos arguments separats per comes per mostrar "Nom:", el teu nom, "Edat:" i la teva edat en la mateixa línia.
3. Repeteix l'exercici anterior però amb el paràmetre `sep=" | "`.
4. Escriu un `print()` amb el paràmetre `end="---"` seguit d'un altre `print()`, i explica per escrit què provoca `end` en l'output.
5. Afegeix comentaris explicant què fa cadascuna de les línies anteriors.

## Depuració amb VSCode

El següent codi hauria de mostrar tres línies, però només se'n mostren dues i la consola diu
`IndentationError`:

```python
print("Línia 1")
    print("Línia 2")
print("Línia 3")
```

1. Obre el fitxer a VSCode, posa un breakpoint a la primera línia i executa amb `F5`.
2. Fixa't en el missatge d'error exacte que dona el depurador/la consola i en quina línia assenyala. **Fes una captura de la terminal!!**
3. Corregeix la indentació perquè les tres línies s'executin correctament.
4. Explica per escrit (2-3 línies) per què Python és tan estricte amb la indentació, a diferència d'altres llenguatges.

## Com entregar-ho

Enllaç del repositori teu personal. En aquest repositori ha d'haver-hi el fitxer `.py` amb tots els exercicis i una captura de pantalla del depurador mostrant l'`IndentationError` abans de corregir-lo.
