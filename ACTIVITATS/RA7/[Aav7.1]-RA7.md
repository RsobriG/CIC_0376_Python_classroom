# Activitat 7.1 — Mòduls propis i pytest

## Objectiu

Crear un mòdul propi, importar-lo de diverses maneres i escriure proves bàsiques amb `pytest`.

## Avaluació

Aquesta activitat s'avalua amb APTE / NO APTE.

## Enunciat

1. Crea un fitxer `botiga.py` amb aquestes tres funcions:
   - `preu_amb_iva(preu)`: retorna el preu amb un 21% d'IVA afegit.
   - `aplicar_descompte(preu, percentatge)`: retorna el preu després d'aplicar un descompte del `percentatge` indicat.
   - `es_car(preu, llindar=50)`: retorna `True` si `preu` és més gran que `llindar`, `False` en cas contrari.

2. Crea un fitxer `principal.py` que:
   - importi `botiga` sencer (`import botiga`) i cridi `botiga.preu_amb_iva(100)`,
   - importi només `aplicar_descompte` amb `from botiga import aplicar_descompte` i el cridi directament,
   - imprimeixi els resultats.

3. Afegeix a `botiga.py` el bloc `if __name__ == "__main__":` amb un `print("Mòdul botiga carregat com a principal")`. Executa primer `botiga.py` directament i després `principal.py`, i explica per escrit (2-3 línies) per què el missatge només apareix en un dels dos casos.

4. Crea un fitxer `test_botiga.py` amb almenys 3 funcions `test_...` que facin servir `assert` per comprovar `preu_amb_iva`, `aplicar_descompte` i `es_car` amb valors que ja saps que han de donar. Executa `pytest` i comprova que totes passen.

5. Modifica a propòsit `preu_amb_iva` perquè apliqui un 25% en comptes d'un 21%, torna a executar `pytest` i copia el missatge d'error que mostra la prova que falla.

## Depuració amb VSCode

El següent codi hauria de calcular el preu final (amb IVA i després amb descompte aplicat), però sempre retorna un resultat incorrecte:

```python
def preu_final(preu, percentatge_descompte):
    amb_iva = preu_amb_iva(preu)
    descompte = amb_iva * percentatge_descompte / 100
    return amb_iva - percentatge_descompte   # <- aquí hi ha el problema

print(preu_final(100, 10))
```

1. Obre el fitxer a VSCode i posa un breakpoint a la línia del `return`.
2. Executa amb F5 i, quan s'aturi, mira al panell "Variables" els valors de `amb_iva`, `descompte` i `percentatge_descompte`.
3. Identifica quina variable s'hauria d'haver fet servir al `return` en comptes de la que hi ha.
4. Corregeix el bug i explica per escrit (2-3 línies) quina era la causa.

## Com entregar-ho

Un fitxer `.zip` o repositori amb `botiga.py`, `principal.py`, `test_botiga.py`, les respostes escrites de l'apartat 3 i 5, i una captura de pantalla del depurador aturat al breakpoint amb el panell de variables visible.
