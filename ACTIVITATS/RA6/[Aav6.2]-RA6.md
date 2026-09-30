# Activitat 6.2 — Diccionaris

## Objectiu

Practicar la creació, accés, modificació i eliminació de claus d'un diccionari, i l'ús de `.get()`
com a forma segura d'accedir-hi.

## Avaluació

Aquesta activitat s'avalua amb APTE / NO APTE.

## Enunciat

1. Crea un diccionari `producte` amb les claus `"nom"` (`"Teclat mecànic"`), `"preu"` (`45.90`) i
   `"estoc"` (`12`). Imprimeix el nom i el preu en una sola frase.
2. Accedeix a la clau `"categoria"` amb `[]` (que NO existeix al diccionari) i, en un comentari, escriu
   quin error dona i per què.
3. Ara accedeix a `"categoria"` amb `.get("categoria", "Sense categoria")` i imprimeix el resultat.
   Explica en un comentari la diferència de comportament respecte a l'exercici anterior.
4. Modifica l'estoc del producte perquè baixi en 3 unitats (simula una venda de 3 unitats) i afegeix
   una nova clau `"categoria"` amb el valor `"Perifèrics"`.
5. Elimina la clau `"estoc"` amb `.pop()`, guardant el valor eliminat en una variable, i imprimeix
   aquesta variable.
6. Comprova amb `in` si les claus `"preu"` i `"estoc"` existeixen encara al diccionari, i imprimeix
   el resultat de cada comprovació.

## Depuració amb VSCode

Aquest codi hauria d'aplicar un 10% de descompte al preu d'un producte, però el resultat final és
incorrecte:

```python
producte = {"nom": "Ratolí òptic", "preu": 20}

def aplicar_descompte(dades, percentatge):
    nou_preu = dades["preu"] * percentatge / 100
    dades["preu"] = nou_preu

aplicar_descompte(producte, 10)
print(producte["preu"])   # s'esperava 18.0
```

1. Posa un breakpoint a la línia `nou_preu = ...`.
2. Executa el depurador i inspecciona el valor de `nou_preu` just després de calcular-lo.
3. Identifica per què el valor final no és `18.0`.
4. Corregeix la fórmula i torna a executar per confirmar que ara dona `18.0`.
5. Explica en 2-3 línies quina era la causa exacta del bug (fixa't en què calcula la fórmula original,
   no en si hi ha error de sintaxi).

## Com entregar-ho

Un fitxer `.py` amb els 6 exercicis (amb els comentaris de resposta) i un segon fitxer `.py` amb el
codi corregit de la part de depuració, acompanyat d'una captura de pantalla del depurador aturat amb
el valor de `nou_preu` visible a la finestra de variables.
