# Activitat 1.5 — Entrada de dades i f-strings

## Objectiu

Practicar `input()`, la conversió del que retorna i el formatatge de sortida amb f-strings.

## Avaluació

Aquesta activitat s'avalua amb APTE / NO APTE.

## Enunciat

1. Demana per `input()` el nom i l'edat de l'usuari, i mostra amb una f-string: `"<nom> té <edat> anys"`.
2. Demana per `input()` dos números i mostra'n la suma. Compte: recorda que `input()` retorna sempre `str`.
3. Amb l'edat demanada a l'exercici 1, mostra amb una f-string quina edat tindrà l'usuari d'aquí a 10 anys (calculant-ho **dins** de les claus `{}`).
4. Mostra amb una f-string un preu amb només 2 decimals (pista: `f"{valor:.2f}"`).
5. Explica per escrit la diferència entre concatenar amb `+` i fer servir una f-string.

## Depuració amb VSCode

El següent codi hauria de sumar dos números introduïts per l'usuari, però el resultat és incorrecte
(per exemple, si l'usuari escriu `3` i `4`, el programa mostra `34` en comptes de `7`):

```python
a = input("Primer número: ")
b = input("Segon número: ")
suma = a + b
print(f"La suma és {suma}")
```

1. Posa un breakpoint a la línia `suma = a + b` i executa amb `F5` (introdueix `3` i `4` quan et ho
   demani).
2. Al panell "Variables", comprova el tipus de `a` i `b`.
3. Fes "step over" i observa el valor de `suma`.
4. Corregeix el codi perquè `suma` sigui realment `7` i no `"34"`.
5. Explica per escrit (2-3 línies) per què `+` entre dos `str` no suma, sinó que concatena.

## Com entregar-ho

Fitxer `.py` amb els exercicis i una captura del panell "Variables" mostrant els tipus de `a` i `b` abans de corregir el bug.
