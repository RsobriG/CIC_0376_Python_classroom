# Activitat 5.3 — Llistes i bucles

## Objectiu

Practicar el recorregut, filtratge i transformació de llistes amb bucles `for`.

## Avaluació

Aquesta activitat s'avalua amb APTE / NO APTE.

## Enunciat

Crea un fitxer `activitat_5_3.py` amb la llista de partida:

```python
notes = [3, 7, 5, 9, 4, 6, 10, 2]
```

1. Recorre `notes` amb un `for` i imprimeix cada nota.
2. Utilitzant un `for` i un acumulador, calcula i imprimeix la **suma total** de les notes.
3. Utilitzant un `for` i un comptador, calcula i imprimeix **quantes notes són aprovat** (>=5).
4. Crea una llista nova `aprovades` amb un `for` que contingui només les notes >= 5 (filtratge).
5. Crea una llista nova `sobre10` amb un `for` que contingui cada nota multiplicada per 10
   (transformació).
6. Utilitzant `enumerate()`, imprimeix cada nota amb la seva posició en el format
   `"Alumne 0: nota 3"`.
7. Calcula la nota **mitjana** (suma total / nombre de notes) i imprimeix-la.
8. (Opcional, ampliació) Escriu amb una *list comprehension* l'equivalent de l'exercici 4.

## Depuració amb VSCode

El fitxer `bug_5_3.py` (crea'l amb aquest contingut) hauria de calcular quantes notes són aprovat, però
sempre retorna 0:

```python
notes = [3, 7, 5, 9, 4, 6, 10, 2]
comptador = 0

for n in notes:
    comptador = 0
    if n >= 5:
        comptador += 1

print("Aprovats:", comptador)
```

1. Posa un breakpoint dins del `for`, a la línia `comptador = 0`.
2. Executa el depurador i fes "Step Over" repetidament, mirant com evoluciona `comptador` al panell
   "Variables" a cada volta del bucle.
3. Identifica exactament per què `comptador` no arriba mai a acumular-se.
4. Corregeix el bug i explica per escrit (2-3 línies) la causa.

## Com entregar-ho

Un fitxer `.py` amb els exercicis resolts, el fitxer `bug_5_3.py` corregit, l'explicació, i una
captura de pantalla del depurador amb el "watch" de `comptador` visible durant diverses iteracions.
