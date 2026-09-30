# Activitat 3.2 — Comptadors i acumuladors

## Objectiu

Construir i interpretar comptadors i acumuladors dins de bucles `while`.

## Avaluació

Aquesta activitat s'avalua amb APTE / NO APTE.

## Enunciat

Crea un fitxer `activitat_3_2.py`:

1. Demana a l'usuari, amb un `while`, que introdueixi números (un per un amb `input`) fins que
   introdueixi la paraula `"fi"`. Mentrestant, vés acumulant la **suma** de tots els números introduïts
   i, al final, mostra el total.
2. Sense executar-lo, indica en un comentari el valor final de `total` i de `i` del codi següent; després
   comprova-ho executant:
   ```python
   total = 0
   i = 1
   while i <= 6:
       total += i * 2
       i += 1
   ```
3. Escriu un bucle `while` que calculi el **factorial** d'un número introduït per l'usuari (producte
   acumulat des d'1 fins al número).
4. Explica per escrit, en un comentari, per què el codi següent **no** dona el resultat esperat i com ho
   arreglaries:
   ```python
   i = 1
   while i <= 5:
       total = 0
       total += i
       i += 1
   print(total)
   ```

## Depuració amb VSCode

El codi següent hauria de calcular la suma dels números de l'1 al 10, però dona un resultat incorrecte:

```python
total = 0
i = 1
while i < 10:
    total += i
    i += 1
print(total)
```

1. Obre'l a VSCode, posa un breakpoint a la línia `total += i`.
2. Executa el depurador i, amb "step over", observa a la finestra de Variables els valors de `total`
   i `i` a cada volta. Anota quin és l'últim valor de `i` amb què s'executa el cos.
3. Compara aquest valor amb el que faria falta perquè la suma arribés fins al 10.
4. Corregeix el bug (canvia el que calgui perquè la suma sigui correcta, de l'1 al 10) i torna-ho a
   comprovar amb el depurador.
5. Escriu 2-3 línies explicant la causa exacta de l'error (té a veure amb l'operador de comparació).

## Com entregar-ho

Fitxer `.py` amb els 4 apartats i el fitxer de depuració corregit, més captura de pantalla del depurador
aturat mostrant els valors de `total` i `i`.
