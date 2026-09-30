# Activitat 3.3 — Validacions, `continue` i bucles infinits

## Objectiu

Aplicar `while` per validar dades d'entrada i distingir el comportament de `break` i `continue`.

## Avaluació

Aquesta activitat s'avalua amb APTE / NO APTE.

## Enunciat

Crea un fitxer `activitat_3_3.py`:

1. Escriu un bucle que demani una contrasenya per teclat fins que l'usuari introdueixi exactament
   `"python123"`. Mentre no l'encerti, mostra `"Contrasenya incorrecta"`.
2. Escriu un bucle `while` de l'1 al 10 que **no imprimeixi** els múltiples de 3 (usa `continue`) però
   sí la resta de números.
3. Sense executar-lo, digues quants intents com a màxim permet fer el codi següent abans d'acabar, i
   quin missatge final es mostrarà si l'usuari sempre falla. Comprova-ho executant-lo:
   ```python
   intents = 0
   encertat = False
   while intents < 3 and not encertat:
       resposta = input("Número secret (1-10): ")
       if resposta == "7":
           encertat = True
       intents += 1
   print("Encertat!" if encertat else "S'han acabat els intents")
   ```
4. Explica per escrit per què el codi següent és un bucle infinit i com el corregiries:
   ```python
   i = 0
   while i < 3:
       print(i)
       if i == 5:
           i += 1
   ```

## Depuració amb VSCode

El codi següent hauria de demanar un número entre l'1 i el 5 fins que l'usuari l'encerti, però **no
s'atura mai encara que l'usuari introdueixi el número correcte**:

```python
correcte = False
while not correcte:
    n = int(input("Endevina el número (1-5): "))
    if n == 3:
        correcte == True   
print("Endevinat!")
```

1. Obre'l a VSCode i posa un breakpoint just a la línia de l'`if`.
2. Executa amb el depurador, introdueix `3` quan et ho demani, i fes "step over" pas a pas mirant el
   valor de `correcte` a la finestra de Variables.
3. Comprova que `correcte` **no canvia mai** de valor, encara que la condició de l'`if` s'hagi complert.
4. Localitza l'operador mal escrit que causa el bug i corregeix-lo.
5. Explica en 2-3 línies la diferència entre l'operador que hi havia i el que calia fer servir.

## Com entregar-ho

Fitxer `.py` amb els 4 apartats i el fitxer de depuració corregit, més captura de pantalla del depurador
aturat a l'`if`, mostrant que `correcte` es queda a `False`.
