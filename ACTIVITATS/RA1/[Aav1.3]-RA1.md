# Activitat 1.3 — print(), comentaris i indentació

## Fitxa de l'activitat

| | |
| :--- | :--- |
| **Mòdul** | 0376. Implementació d'aplicacions web |
| **Resultat d'aprenentatge** | RA1. Prepara l'entorn de treball Python i coneix els fonaments bàsics del llenguatge. |
| **Tipus** | Activitat d'aprenentatge  |
| **Avaluació** | **Apte/No Apte** |
| **Modalitat** | Individual |

## Objectiu

Practicar la sintaxi bàsica de Python: `print()`, comentaris i la importància de la indentació.

## Activitat 1: Enunciat

1. Crea una carpeta de nom **Activitats** i crea un fitxer de nom **Aav13.py** i escriu un programa que mostri, amb un `print()` per línia, el teu nom, la teva ciutat i la teva edat.
2. Fes servir un únic `print()` amb diversos arguments separats per comes per mostrar "Nom:", el teu nom, "Edat:" i la teva edat en la mateixa línia.
3. Repeteix l'exercici anterior però amb el paràmetre `sep=" | "`.
4. Escriu un `print()` amb el paràmetre `end="---"` seguit d'un altre `print()`, i explica per escrit què provoca `end` en l'output.
5. Afegeix comentaris explicant què fa cadascuna de les línies anteriors.
6. Segueix les passes de l'apartat **entregar amb git** abans de continuar amb la següent activitat.

## Activitat 2: Depuració amb VSCode

El següent codi hauria de mostrar tres línies, però només se'n mostren dues i la consola diu
`IndentationError`:

```python
print("Línia 1")
    print("Línia 2")
print("Línia 3")
```

1. Crea un segon fitxer de nom **Aav13_depura.py** i copia el codi a depurar, posa un breakpoint a la primera línia i executa amb `F5`.
2. Fixa't en el missatge d'error exacte que dona el depurador/la consola i en quina línia assenyala. **Fes una captura de la terminal!!**
3. Corregeix la indentació perquè les tres línies s'executin correctament.
4. Explica per escrit (2-3 línies) per què Python és tan estricte amb la indentació, a diferència d'altres llenguatges.

## Com entregar-ho

**Enllaç del teu repositori al moodle**. En aquest repositori ha d'haver-hi el/s fitxer/s `.py` amb tots els exercicis i l'activitat en format .md amb la captura de pantalla del depurador mostrant l'`IndentationError` abans de corregir-lo.

## Entregar amb Git

**NO OBLIDAR** de pujar el/s fitxer/s de l'activitat al Github amb les comandes:

1. git status (per veure el/s fitxer/s en vermell) 
2. git add <nom_fitxer>
3. git status (per veure el/s fitxer/s en verd)
4. git commit -m "missatge"
5. git push
