# Activitat 1.2 — Primer commit i entrega per GitHub

## Objectiu

Practicar el flux bàsic de Git (`add`, `commit`, `push`) per entregar activitats durant tot el curs.

## Avaluació

Aquesta activitat s'avalua amb APTE / NO APTE.

## Enunciat

1. Clona el repositori del curs que t'ha indicat el professor (`git clone <url>`).
2. Dins la teva carpeta personal, copia-hi el fitxer `activitat1_1.py` de l'activitat anterior.
3. Crea un fitxer `.gitignore` que exclogui la carpeta `__pycache__/` i els fitxers `.pyc`.
4. Fes `git add`, `git commit -m "..."` i `git push` dels canvis.
5. Comprova a la pàgina web de GitHub que els fitxers hi apareixen correctament.
6. Executa `git log` i anota quantes línies de sortida (commits) hi ha.

## Depuració amb VSCode

En Marc fa `git push` i li surt un error, o bé puja el repositori però quan l'obre a GitHub li falten
fitxers que ell creu que ha pujat.

1. Executa `git status` a la terminal de VSCode abans i després de fer `git add`. Fixa't en quins
   fitxers apareixen en vermell (no seguits/sense afegir) i quins en verd (preparats per al commit).
2. Si un fitxer que hauries d'entregar no apareix mai encara que facis `git add .`, revisa el contingut
   del teu `.gitignore`: és possible que hi hagi una regla massa genèrica (p. ex. `*.py`) que l'exclogui
   per error.
3. Corregeix el `.gitignore` perquè només exclogui el que cal (`__pycache__/`, `*.pyc`) i torna a fer el
   flux `add`/`commit`/`push`.
4. Explica per escrit (2-3 línies) quina regla del `.gitignore` provocava el problema i per què.

## Com entregar-ho

Enllaç al repositori de GitHub amb els commits fets i una captura de `git status`/`git log` mostrant l'historial.
