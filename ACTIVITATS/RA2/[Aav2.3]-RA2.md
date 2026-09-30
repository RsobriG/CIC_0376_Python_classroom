# Activitat 2.3 — Mètodes de strings i validacions

## Objectiu

Practicar els mètodes bàsics de strings (`upper`, `lower`, `strip`, `split`, `replace`, `find`, `in`) combinats amb condicionals per fer petites validacions de text.

## Avaluació

Aquesta activitat s'avalua amb APTE / NO APTE.

## Enunciat

1. Donat `email = "  Usuari@Exemple.COM  "`:
   - Neteja els espais sobrants i converteix-lo tot a minúscules en una variable nova `email_net`.
   - Comprova si conté el caràcter `"@"` i imprimeix `"Format probablement vàlid"` o `"Format invàlid"` en conseqüència.
   - Compta quantes vegades apareix `"@"` amb `.count("@")` i imprimeix `"Vàlid"` només si n'hi ha exactament 1.

2. Donada la frase `frase = "El gat menja peix i el gos menja pinso"`:
   - Divideix-la en paraules amb `.split()` i imprimeix quantes paraules té amb `len()`.
   - Substitueix totes les aparicions de `"menja"` per `"mengen"` amb `.replace()` i imprimeix el resultat.
   - Troba la posició (índex) on comença la paraula `"peix"` amb `.find()`.

3. Escriu un programa que demani a l'usuari una paraula (`input()`) i imprimeixi `"És un palíndrom"` si la paraula (en minúscules) és igual al seu revers, o `"No és un palíndrom"` en cas contrari. Prova-ho amb `"reconeixer"` i amb `"anilina"`.

4. Sense executar-ho, digues què retorna `"Hola Món".find("xyz")` i per què **no** és un bon costum fer `if "Hola".find("x"):` per comprovar si `"x"` hi és (pista: pensa en quin valor booleà té `-1`).

## Depuració amb VSCode

Aquest codi hauria de comprovar si una contrasenya conté un espai i, si no en té cap, dir que és vàlida, però sempre diu que és invàlida encara que la contrasenya no tingui cap espai:

```python
password = "Contrasenya123"
if password.find(" "):
    print("Vàlida: no conté espais")
else:
    print("Invàlida: conté espais")
```

1. Posa un breakpoint a la línia del `if` i executa el depurador.
2. Mira, a la finestra de variables (o al "Debug Console" escrivint `password.find(" ")`), quin valor retorna realment `.find(" ")` quan no troba l'espai.
3. Identifica per què aquest valor es comporta com a "veritat" (`True`) dins de l'`if`, tot i que sembla que "no ha trobat res".
4. Corregeix el codi (canviant la condició per una comparació explícita, p. ex. amb `-1` o amb `in`) i explica en 2-3 línies la causa del bug.

## Com entregar-ho

Un fitxer `.py` amb els 4 exercicis i el codi corregit, més una captura del "Debug Console" de VSCode mostrant el valor retornat per `password.find(" ")`.
