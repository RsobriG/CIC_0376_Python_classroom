# Activitat 7.3 — Escriptura de fitxers i gestió d'errors

## Objectiu

Escriure i afegir contingut a fitxers de text, i protegir un programa amb `try`/`except`/`else`/`finally`.

## Avaluació

Aquesta activitat s'avalua amb APTE / NO APTE.

## Enunciat

1. Escriu un programa que demani per teclat (`input()`) el nom i la nota de 3 alumnes (un a un) i els vagi escrivint, un per línia amb el format `nom,nota`, a un fitxer `nous_alumnes.txt` obert en mode `'w'`.
2. Executa el programa una segona vegada amb 2 alumnes diferents, però ara obrint el fitxer en mode `'a'`. Comprova que el fitxer final té 5 línies (les 3 primeres no s'han perdut).
3. Torna a executar-lo una tercera vegada, ara en mode `'w'` altre cop, i explica per escrit (1-2 línies) què ha passat amb el contingut anterior del fitxer.
4. Embolcalla la conversió de la nota (`float(...)`) dins un `try`/`except ValueError` que, si l'usuari escriu una nota no numèrica, mostri `"Nota no vàlida, es descarta aquest alumne"` i continuï demanant el següent, sense aturar el programa.
5. Afegeix un bloc `finally` que imprimeixi sempre `"Procés d'entrada de dades finalitzat"`, independentment de si hi ha hagut algun error o no.
6. Prova el programa introduint una nota com `"set"` (paraula, no número) per comprovar que el `except` la captura correctament.

## Depuració amb VSCode

El següent codi hauria de gestionar l'error si el fitxer d'alumnes no existeix, però el missatge d'error que dona no és l'esperat (captura un tipus d'excepció equivocat):

```python
def carregar_alumnes(ruta):
    try:
        with open(ruta, "r") as f:
            return f.readlines()
    except ValueError:                      # <- aquí hi ha el problema
        print("El fitxer no existeix")
        return []

dades = carregar_alumnes("alumnes_que_no_existeix.txt")
print(dades)
```

1. Posa un breakpoint a la línia del `except ValueError:`.
2. Executa amb F5. Com que l'excepció real llançada NO coincideix amb `ValueError`, el depurador s'aturarà mostrant un error no capturat (o el programa fallarà abans de passar pel breakpoint) — observa a la finestra d'excepció/consola quin és el **nom real** de l'excepció.
3. Corregeix el `except` perquè capturi el tipus d'excepció correcte.
4. Explica per escrit (2-3 línies) la diferència entre `ValueError` i l'excepció que realment calia capturar aquí.

## Com entregar-ho

Els fitxers `.py`, el fitxer `nous_alumnes.txt` resultant, les respostes escrites dels apartats 3 i la de depuració, i una captura de pantalla del missatge d'excepció real vist a VSCode.
