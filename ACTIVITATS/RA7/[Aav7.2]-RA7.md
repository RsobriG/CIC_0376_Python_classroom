# Activitat 7.2 — Lectura de fitxers

## Objectiu

Llegir dades d'un fitxer de text de diverses maneres i processar-ne el contingut.

## Avaluació

Aquesta activitat s'avalua amb APTE / NO APTE.

## Enunciat

1. Crea un fitxer `alumnes.txt` amb aquest contingut (una línia per alumne, nom i nota separats per una coma):
   ```
   Marta,7.5
   Jordi,4.2
   Anna,9.1
   Pau,5.0
   Laia,3.8
   ```
2. Escriu un programa `llegir_v1.py` que obri el fitxer amb `with open(...) as f:` i faci `f.read()` per mostrar tot el contingut d'un cop.
3. Escriu un programa `llegir_v2.py` que obri el mateix fitxer i faci `f.readlines()`, i imprimeixi quantes línies té la llista resultant.
4. Escriu un programa `llegir_v3.py` que iteri el fitxer línia a línia amb un `for linia in f:`, i per a cada línia:
   - faci `.strip()` i `.split(",")` per separar nom i nota,
   - converteixi la nota a `float`,
   - imprimeixi `"<nom>: APROVAT"` si la nota és `>= 5`, o `"<nom>: SUSPÈS"` en cas contrari.
5. Amb el mateix bucle de l'apartat 4, calcula i imprimeix la nota mitjana de la classe.
6. Intenta obrir un fitxer que no existeix (`open("no_existeix.txt", "r")`) sense capturar l'error i copia el nom exacte de l'excepció que es llança al terminal.

## Depuració amb VSCode

Aquest codi hauria d'imprimir la nota mitjana, però el resultat que dona és clarament incorrecte:

```python
def nota_mitjana(ruta):
    total = 0
    comptador = 0
    with open(ruta, "r") as f:
        for linia in f:
            nom, nota = linia.strip().split(",")
            total = total + nota      # <- aquí hi ha el problema
            comptador += 1
    return total / comptador

print(nota_mitjana("alumnes.txt"))
```

1. Posa un breakpoint dins el `for`, a la línia del `total = total + nota`.
2. Executa amb F5 i observa al panell "Variables" de quin **tipus** és `nota` (fixa't com la mostra VSCode: entre cometes vol dir que encara és `str`).
3. Fes "step over" un parell d'iteracions i comprova que `total` no s'està sumant com un número.
4. Corregeix el bug (falta una conversió de tipus) i explica per escrit (2-3 línies) per què Python no dona un error de seguida tot i que la suma és incorrecta.

## Com entregar-ho

Els quatre fitxers `.py`, el fitxer `alumnes.txt`, les respostes escrites dels apartats 4 i 6, i una captura del depurador aturat mostrant el tipus de la variable `nota`.
