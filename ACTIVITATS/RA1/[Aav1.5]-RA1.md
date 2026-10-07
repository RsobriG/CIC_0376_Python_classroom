# Activitat 1.5 — Entrada de dades i f-strings

## Fitxa de l'activitat

| | |
| :--- | :--- |
| **Mòdul** | 0376. Implementació d'aplicacions web |
| **Resultat d'aprenentatge** | RA1. Prepara l'entorn de treball Python i coneix els fonaments bàsics del llenguatge. |
| **Tipus** | Activitat d'aprenentatge  |
| **Avaluació** | **Apte/No Apte** |
| **Modalitat** | Individual |

## Objectiu

Practicar `input()`, la conversió del que retorna i el formatatge de sortida amb f-strings.

## Activitat 1: Enunciat

1. Demana per `input()` el nom i l'edat de l'usuari, i mostra amb una f-string: `"<nom> té <edat> anys"`.
2. Demana per `input()` dos números i mostra'n la suma. Compte: recorda que `input()` retorna sempre `str`.
3. Amb l'edat demanada a l'exercici 1, mostra amb una f-string quina edat tindrà l'usuari d'aquí a 10 anys (calculant-ho **dins** de les claus `{}`).
4. Mostra amb una f-string un preu amb només 2 decimals (pista: `f"{valor:.2f}"`).
5. Explica per escrit la diferència entre concatenar amb `+` i fer servir una f-string.
6. Segueix les passes de l'apartat **entregar amb git** abans de continuar amb la següent activitat.

## Activitat 2: Depuració amb VSCode

El següent codi hauria de sumar dos números introduïts per l'usuari, però el resultat és incorrecte
(per exemple, si l'usuari escriu `3` i `4`, el programa mostra `34` en comptes de `7`):

```python
a = input("Primer número: ")
b = input("Segon número: ")
suma = a + b
print(f"La suma és {suma}")
```

1. Posa un breakpoint a la línia `suma = a + b` i executa amb `F5` (introdueix `3` i `4` quan et ho
   demani).
2. Al panell "Variables", comprova el tipus de `a` i `b`.
3. Fes "step over" i observa el valor de `suma`. **Fes una captura de pantalla!**
4. Corregeix el codi perquè `suma` sigui realment `7` i no `"34"`.
5. Explica per escrit (2-3 línies) per què `+` entre dos `str` no suma, sinó que concatena.
6. Segueix les passes de l'apartat **entregar amb git** abans de continuar amb la següent activitat.

## Com entregar-ho

**Enllaç del teu repositori al moodle**. En el repositori ha d'haver-hi el fitxer `.py` amb els exercicis i una captura del panell "Variables" mostrant els tipus de `a` i `b` abans de corregir el bug.

## Entregar amb Git

**NO OBLIDAR** de pujar el/s fitxer/s de l'activitat al Github amb les comandes:

1. git status (per veure el/s fitxer/s en vermell) 
2. git add <nom_fitxer>
3. git status (per veure el/s fitxer/s en verd)
4. git commit -m "Activitat X feta"
5. git push