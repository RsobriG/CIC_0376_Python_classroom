# Activitat 1.4 — Variables, tipus i conversió

## Fitxa de l'activitat

| | |
| :--- | :--- |
| **Mòdul** | 0376. Implementació d'aplicacions web |
| **Resultat d'aprenentatge** | RA1. Prepara l'entorn de treball Python i coneix els fonaments bàsics del llenguatge. |
| **Tipus** | Activitat d'aprenentatge  |
| **Avaluació** | **Apte/No Apte** |
| **Modalitat** | Individual |

## Objectiu

Practicar la declaració de variables, els tipus bàsics i la conversió entre tipus (*casting*).

## Activitat 1: Enunciat

1. Declara quatre variables: una `int`, una `float`, una `str` i una `bool`. Mostra el valor i el tipus (`type()`) de cadascuna amb `print()`.
2. Declara `preu_text = "12.50"` i calcula `preu_text` més IVA (21%) com a número, mostrant el resultat com a `float`.
3. Declara `edat = 17` i calcula, fent servir comparadors (<, =, >, >= o <=), si la persona és major d'edat (`edat >= 18`), guardant el resultat en una variable `es_major` i mostrant-ne el tipus.
4. Prova (i explica el resultat) què retorna `bool(0)`, `bool(1)`, `bool("")`, `bool("False")` i `bool("0")`.
5. Prova què passa si fas `"5" + 5` directament (sense convertir) i explica l'error que dona.
6. Segueix les passes de l'apartat **entregar amb git** abans de continuar amb la següent activitat.

## Activitat 2: Depuració amb VSCode

El següent codi hauria de calcular el preu total (preu + IVA) però dona un `TypeError`:

```python
preu = "20"
iva = 0.21
total = preu + (preu * iva)
print(f"Total: {total}")
```

1. Posa un breakpoint a la línia `total = ...` i executa amb `F5`.
2. Al panell "Variables", comprova el tipus real de `preu` (fixa't que apareix entre cometes: és un
   `str`, no un número).
3. Fes "step over" i observa l'error exacte que es produeix. **Fes una captura de pantalla!**
4. Corregeix el codi convertint `preu` al tipus adequat, i torna a executar per comprovar que ara
   funciona.
5. Explica per escrit (2-3 línies) per què el codi original fallava encara que `preu` "sembli" un
   número.
6. Segueix les passes de l'apartat **entregar amb git** abans de continuar amb la següent activitat.

## Com entregar-ho

**Enllaç del teu repositori al moodle**. En el repositori ha d'haver-hi el fitxer `.py` amb els 5 exercicis i una captura del panell "Variables" de VSCode mostrant el tipus de `preu` abans de corregir el bug.

## Entregar amb Git

**NO OBLIDAR** de pujar el/s fitxer/s de l'activitat al Github amb les comandes:

1. git status (per veure el/s fitxer/s en vermell) 
2. git add <nom_fitxer>
3. git status (per veure el/s fitxer/s en verd)
4. git commit -m "Activitat X feta"
5. git push