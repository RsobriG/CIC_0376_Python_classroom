# Activitat 5.2 — Mètodes de llistes i còpia vs referència

## Objectiu

Practicar els mètodes principals de les llistes i entendre la diferència entre còpia per referència
i còpia real.

## Avaluació

Aquesta activitat s'avalua amb APTE / NO APTE.

## Enunciat

Crea un fitxer `activitat_5_2.py`:

1. Crea una llista `cistella = ["pa", "llet", "ous"]`.
2. Afegeix `"formatge"` al final amb `.append()` i imprimeix la llista.
3. Insereix `"mantega"` a la posició 1 amb `.insert()` i imprimeix la llista.
4. Elimina `"ous"` amb `.remove()` i imprimeix la llista.
5. Fes `producte = cistella.pop()` i imprimeix tant `producte` com `cistella` — explica en un
   comentari per què `producte` conté el que conté.
6. Ordena la llista amb `.sort()` i imprimeix-la.
7. Escriu `x = cistella.sort()` i imprimeix `x`. Explica en un comentari per què val el que val.
8. Crea `a = [5, 3, 1]`, fes `b = a` i `c = a.copy()`. Modifica `b` amb `.append(9)`. Imprimeix
   `a`, `b` i `c` i explica per escrit per què `a` ha canviat però `c` no.

## Depuració amb VSCode

El fitxer `bug_5_2.py` (crea'l amb aquest contingut) hauria de generar una llista `originals` amb els
valors `[1, 2, 3]` sense modificar, i una llista `modificats` amb els valors multiplicats per 10, però
no funciona com s'espera:

```python
originals = [1, 2, 3]
modificats = originals
modificats.sort(reverse=True)
for i in range(len(modificats)):
    modificats[i] = modificats[i] * 10

print("Originals:", originals)
print("Modificats:", modificats)
```

1. Posa un breakpoint a la línia `modificats = originals` i un altre després del `for`.
2. Executa el depurador i observa, al panell "Variables", si `originals` i `modificats` són el mateix
   objecte o objectes diferents (VSCode mostra el mateix identificador/valor en temps real per a
   tots dos si estan lligats).
3. Corregeix el codi perquè `originals` quedi intacte.
4. Explica per escrit (2-3 línies) la causa del bug.

## Com entregar-ho

Un fitxer `.py` amb els 8 exercicis, el fitxer `bug_5_2.py` corregit, l'explicació, i una captura de
pantalla del depurador mostrant les dues variables durant l'execució.
