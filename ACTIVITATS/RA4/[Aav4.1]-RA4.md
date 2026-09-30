# Activitat 4.1 — for i range()

## Objectiu

Practicar el bucle `for` amb les tres formes de `range()` i el recorregut de llistes per índex.

## Avaluació

Aquesta activitat s'avalua amb APTE / NO APTE.

## Enunciat

1. Escriu un `for` que imprimeixi els números del `0` al `9` (tots dos inclosos) fent servir `range` amb un sol argument.
2. Escriu un `for` que imprimeixi els números parells entre `10` i `20` (tots dos inclosos) fent servir `range` amb tres arguments.
3. Escriu un `for` que imprimeixi els números del `10` al `1` en ordre descendent, fent servir `range` amb `step` negatiu.
4. Donada la llista `productes = ["pa", "llet", "ous", "formatge"]`, escriu un `for i in range(len(productes))` que imprimeixi cada element precedit de la seva posició, en format `0 - pa`.
5. Sense executar-ho, escriu en un comentari quants valors generarà `range(4, 4)` i quants generarà `range(10, 2, -3)`. Després comprova-ho amb `list(range(...))`.

## Depuració amb VSCode

El següent codi hauria d'imprimir els números del `1` al `5`, però no ho fa:

```python
for i in range(1, 5):
    print(i)
```

1. Obre el fitxer a VSCode i posa un breakpoint a la línia del `print(i)`.
2. Executa amb F5 i fes "step over" cada volta, mirant el valor de `i` a la finestra de variables.
3. Identifica en quina volta `i` deixa de coincidir amb el que esperaves i per què.
4. Corregeix el codi perquè imprimeixi realment del `1` al `5` i explica per escrit (2-3 línies) la causa del bug.

## Com entregar-ho

Un fitxer `.py` amb els 5 exercicis i el codi corregit de la depuració, més una captura de pantalla del depurador de VSCode aturat en un breakpoint amb el panell de variables visible.
