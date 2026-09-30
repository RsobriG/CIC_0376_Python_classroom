# Activitat 6.1 — Tuples i sets

## Objectiu

Practicar la creació i ús de tuples (immutabilitat, packing/unpacking) i sets (elements únics,
operacions de conjunt).

## Avaluació

Aquesta activitat s'avalua amb APTE / NO APTE.

## Enunciat

1. Crea una tupla `coordenada` amb els valors `(2, 5)`. Escriu una línia de codi que intenti canviar
   el primer element per `10` i, en un comentari, escriu quin error dona Python.
2. Crea una tupla `persona = ("Júlia", 24, "Girona")` i fes-ne l'*unpacking* en tres variables
   `nom`, `edat`, `ciutat`. Imprimeix una frase amb els tres valors combinats.
3. Crea dos sets: `assignatures_alba = {"Python", "Bases de dades", "Xarxes"}` i
   `assignatures_martí = {"Python", "Sistemes", "Xarxes"}`.
   - Imprimeix les assignatures que **comparteixen** els dos (intersecció).
   - Imprimeix totes les assignatures diferents entre els dos, sense repetir-ne cap (unió).
   - Imprimeix les assignatures que fa l'Alba i **no** fa en Martí (diferència).
4. Crea un set `nums = {1, 2, 2, 3, 3, 3}` i imprimeix-lo. Explica en un comentari per què el resultat
   no té 6 elements.
5. Afegeix el valor `4` al set `nums` amb `.add()` i, després, intenta eliminar el valor `10` amb
   `.remove()`. Explica en un comentari què passa i com ho hauries fet amb `.discard()` per evitar
   l'error.

## Depuració amb VSCode

El següent codi hauria de calcular el "punt mitjà" entre dues coordenades i mostrar-lo, però té un bug:

```python
def punt_mig(p1, p2):
    p1[0] = (p1[0] + p2[0]) / 2
    p1[1] = (p1[1] + p2[1]) / 2
    return p1

a = (0, 0)
b = (4, 8)
mig = punt_mig(a, b)
print(mig)
```

1. Copia el codi a un fitxer `.py` dins VSCode.
2. Posa un breakpoint a la primera línia de dins de la funció `punt_mig`.
3. Executa amb F5 i fes *step over* línia a línia, mirant la finestra de variables (`p1`, `p2`).
4. Identifica exactament a quina línia salta l'error i quin tipus d'error és.
5. Corregeix el codi (sense canviar que `a` i `b` siguin tuples) i explica en 2-3 línies per què fallava.

## Com entregar-ho

Un fitxer `.py` amb els 5 exercicis resolts (amb comentaris de resposta a les preguntes) més un segon
fitxer `.py` amb el codi de depuració corregit, i una captura de pantalla del depurador de VSCode aturat
al breakpoint amb la finestra de variables visible.
