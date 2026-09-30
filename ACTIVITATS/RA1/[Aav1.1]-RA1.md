# Activitat 1.1 — Primer programa i entorn de treball

## Objectiu

Comprovar que l'entorn (Python + VSCode) funciona correctament i escriure els primers programes amb `print()`.

## Avaluació

Aquesta activitat s'avalua amb APTE / NO APTE.

## Enunciat

1. Comprova, des de la terminal de VSCode, la versió de Python instal·lada (`python --version` o `python3 --version`). Anota-la.
2. Crea un fitxer `activitat1_1.py` i escriu un programa que mostri el teu nom, el nom del curs ("Python") i l'any actual, en tres línies separades, fent servir tres `print()`.
3. Modifica el programa perquè les tres dades es mostrin en una **única línia**, separades per ` - `, fent servir un sol `print()` amb el paràmetre `sep`.
4. Afegeix un comentari a dalt de tot del fitxer amb el teu nom i la data d'avui.

## Depuració amb VSCode

En Marc ha escrit aquest programa però, en prémer `F5`, VSCode li diu que no troba l'intèrpret de Python
o li dona un error estrany en executar (per exemple, li funciona `print` d'una versió de Python molt
antiga que no reconeix `sep`).

1. Obre VSCode i comprova, a la cantonada inferior dreta (o amb `Ctrl+Shift+P` → *Python: Select Interpreter*), quin intèrpret de Python té seleccionat el teu projecte.
2. Posa un breakpoint a la primera línia del teu `activitat1_1.py` i executa amb `F5`.
3. Comprova, al panell "Variables" del depurador, que el programa s'atura efectivament al breakpoint (senyal que l'intèrpret sí que funciona).
4. Explica per escrit (2-3 línies): què passaria si VSCode tingués seleccionat un intèrpret de Python que no existeix o d'una versió molt antiga (< 3.6)? Quin símptoma donaria?

## Com entregar-ho

Puja `activitat1_1.py` al repositori i afegeix una captura de pantalla de VSCode amb el depurador aturat al breakpoint (panell "Variables" visible).
