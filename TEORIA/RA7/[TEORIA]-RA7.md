# TEORIA — RA7. Organitza codi en mòduls, treballa amb fitxers, gestiona errors i es prepara per a la certificació PCEP

Objectiu general: saber organitzar codi en mòduls i utilitzar la biblioteca estàndard bàsica, llegir i escriure fitxers de text, gestionar errors amb `try`/`except`, depurar programes complets amb VSCode, i arribar preparat/da a l'examen de certificació PCEP (PE1).

---

## Sessió S30 — Mòduls + pytest (05/04/2027)

- Un **mòdul** és, simplement, un fitxer `.py`. Tot fitxer Python és importable des d'un altre com a mòdul.
- `import nom_modul` carrega el mòdul sencer; per usar-ne una funció cal escriure `nom_modul.funcio()`.
- `from nom_modul import funcio` importa només un nom concret; ja es pot cridar directament `funcio()` sense prefix.
- `import nom_modul as alies` permet donar un nom curt al mòdul importat (p. ex. `import math as m`).
- La **llibreria estàndard** és el conjunt de mòduls que ja porta Python instal·lats, sense necessitat d'instal·lar res més:

```python
import math
print(math.sqrt(16))      # 4.0  -> arrel quadrada, retorna float
print(math.floor(3.7))    # 3    -> arrodoneix cap avall, retorna int
print(math.pi)            # 3.141592653589793  -> no és una funció, és una constant (sense parèntesis)

import random
print(random.randint(1, 6))     # enter aleatori entre 1 i 6, ambdós inclosos
print(random.choice(['a','b','c']))  # retorna un element aleatori de la llista
```

- `dir(modul)` llista els noms (funcions, constants) que conté un mòdul; `help(funcio)` mostra la seva documentació.
- Cada mòdul té una variable especial `__name__`. Quan s'executa el fitxer directament, `__name__` val `"__main__"`; quan s'importa des d'un altre fitxer, val el nom del mòdul. Per això és habitual veure:

```python
def main():
    print("Programa principal")

if __name__ == "__main__":
    main()
```

Això permet que el fitxer es pugui importar (per reutilitzar-ne funcions) sense que s'executi automàticament tot el codi principal.

- **pytest** és una eina (no ve per defecte amb Python, cal instal·lar-la amb `pip install pytest`) per escriure **proves automàtiques**. Una funció de prova és una funció el nom de la qual comença per `test_`, i que fa servir `assert` per comprovar que un resultat és el que s'espera:

```python
# arxiu suma.py
def suma(a, b):
    return a + b

# arxiu test_suma.py
from suma import suma

def test_suma_positius():
    assert suma(2, 3) == 5

def test_suma_amb_negatiu():
    assert suma(-1, 1) == 0
```

- Es llancen totes les proves d'un projecte amb la comanda `pytest` al terminal (dins la carpeta del projecte). Si un `assert` és fals, la prova falla i pytest ho indica en vermell amb el detall de què s'esperava i què s'ha obtingut.
- `assert condicio` no fa res si `condicio` és `True`; si és `False`, llança un error `AssertionError` i atura l'execució.

### Exemples addicionals

```python
# Cas normal: importar només el que necessitem
from math import sqrt, pi
print(sqrt(25))      # 5.0
print(pi)             # 3.141592653589793
```

```python
# Error típic 1: fer "import math" i després cridar sqrt() sense el prefix
import math
print(sqrt(16))
# NameError: name 'sqrt' is not defined
# (amb "import math" el nom disponible és "math", no "sqrt" directament;
#  cal escriure math.sqrt(16))
```

```python
# Error típic 2: fer "from random import randint" i després escriure "random.randint(...)"
from random import randint
print(random.randint(1, 10))
# NameError: name 'random' is not defined
# ("from X import Y" només deixa disponible el nom Y, NO el nom del mòdul X)
```

```python
# __name__ segons com s'executa el fitxer (no cal executar-ho, és per entendre el concepte)
# fitxer eines.py:
def duplica(x):
    return x * 2

print(__name__)
# Si executes "python eines.py" directament: imprimeix "__main__"
# Si un altre fitxer fa "import eines": imprimeix "eines"
```

---

## Sessió S31 — Fitxers I: lectura (12/04/2027)

- Per treballar amb un fitxer primer s'ha d'**obrir** amb la funció `open(ruta, mode)`, que retorna un **objecte fitxer**.
- Modes principals de lectura:
  - `'r'` (per defecte): lectura de text. Si el fitxer no existeix, llança `FileNotFoundError`.
- La forma recomanada d'obrir un fitxer és amb `with`, perquè **tanca el fitxer automàticament** encara que hi hagi un error dins el bloc:

```python
with open("dades.txt", "r") as f:
    contingut = f.read()   # llegeix TOT el fitxer com un únic string
print(contingut)
```

- Mètodes de lectura sobre l'objecte fitxer:
  - `f.read()` → retorna tot el contingut com un sol `str`.
  - `f.readline()` → retorna només la següent línia (amb el salt de línia `\n` inclòs), o `''` si ja no en queden.
  - `f.readlines()` → retorna una **llista** de strings, una posició per línia (cadascuna amb `\n` inclòs).
- També es pot **iterar directament** l'objecte fitxer línia a línia amb un `for`, sense cridar cap mètode:

```python
with open("dades.txt", "r") as f:
    for linia in f:
        print(linia.strip())   # .strip() treu el '\n' final i espais sobrants
```

- Si s'obre un fitxer **sense** `with`, cal recordar tancar-lo manualment amb `f.close()`; si no es tanca, el fitxer pot quedar "bloquejat" o els canvis no acabar de desar-se — per això `with` és la pràctica recomanada.
- Un cop llegit `f.read()` sencer, l'objecte fitxer queda "al final"; si es torna a cridar `f.read()` sense tornar a obrir, retorna un string buit `''` (no torna a llegir des del principi).

### Exemples addicionals

```python
# Cas normal: llegir línia a línia amb readline()
with open("agenda.txt", "r") as f:
    primera = f.readline()
    segona = f.readline()
print(primera)   # "Dilluns: reunió\n"   (la línia sencera, amb el salt de línia inclòs)
print(segona)    # "Dimarts: lliurament\n"
```

```python
# Cas límit: readlines() sobre un fitxer buit
with open("buit.txt", "r") as f:
    linies = f.readlines()
print(linies)       # []   (llista buida: el fitxer no té cap línia)
print(len(linies))  # 0
```

```python
# Error típic: obrir un fitxer que no existeix
with open("no_existeix.txt", "r") as f:
    contingut = f.read()
# FileNotFoundError: [Errno 2] No such file or directory: 'no_existeix.txt'
```

```python
# Diferència de tipus entre read() i readlines()
with open("colors.txt", "r") as f:
    text = f.read()
print(type(text))          # <class 'str'>   -> tot el fitxer en un sol string

with open("colors.txt", "r") as f:
    linies = f.readlines()
print(type(linies))        # <class 'list'>  -> una entrada de la llista per cada línia
```

---

## Sessió S32 — Fitxers II + gestió d'errors i depuració (19/04/2027)

- Modes d'escriptura de `open()`:
  - `'w'` (write): **crea** el fitxer si no existeix, o **sobreescriu completament** el seu contingut si ja existia.
  - `'a'` (append): **afegeix** contingut al final del fitxer sense esborrar el que ja hi havia; el crea si no existeix.
- `f.write(text)` escriu el string `text` al fitxer (**no** afegeix `\n` automàticament, cal posar-lo explícitament si es vol salt de línia).

```python
with open("sortida.txt", "w") as f:
    f.write("primera línia\n")
    f.write("segona línia\n")
```

- **Gestió d'errors amb `try`/`except`**: permet que el programa no s'aturi de cop quan es produeix un error (una *excepció*) en temps d'execució.

```python
try:
    numero = int(input("Introdueix un número: "))
    resultat = 10 / numero
except ValueError:
    print("Això no és un número vàlid")
except ZeroDivisionError:
    print("No es pot dividir per zero")
else:
    print("Resultat:", resultat)   # només s'executa si NO hi ha hagut excepció
finally:
    print("Fi del programa")       # s'executa SEMPRE, hi hagi error o no
```

- Excepcions habituals que cal reconèixer: `ValueError` (valor del tipus correcte però contingut invàlid, p. ex. `int("hola")`), `TypeError` (operació entre tipus incompatibles, p. ex. `"3" + 3`), `ZeroDivisionError` (divisió per zero), `IndexError` (índex fora de rang en una llista), `KeyError` (clau inexistent en un diccionari), `FileNotFoundError` (obrir un fitxer que no existeix).
- Un `except` sense excepció específica (`except:`) captura **qualsevol** error — s'ha d'evitar en general perquè amaga errors inesperats, però cal saber reconèixer-lo a l'examen.
- **Depuració amb VSCode**: quan un programa dona un resultat inesperat (o una excepció no capturada), la manera professional de trobar la causa NO és afegir `print()` per tot arreu, sinó fer servir el depurador: posar un **breakpoint** (clicant al marge esquerre de la línia), executar amb **F5**, i inspeccionar el valor de les variables al panell "Variables" en el moment exacte on el programa s'atura. Vegeu la guia completa a `00_GUIES/Com_Debugar_amb_VSCode.md`.

### Exemples addicionals

```python
# Mode 'a': afegir sense esborrar el que ja hi havia
with open("log.txt", "a") as f:
    f.write("nova entrada\n")
# Si "log.txt" ja tenia contingut abans, es conserva; la nova línia s'afegeix al final
```

```python
# Ordre dels "except": Python prova cada bloc en ordre fins trobar el tipus que coincideix
dades = [1, 2, 3]
try:
    print(dades[5])
except ValueError:
    print("Valor no vàlid")
except IndexError:
    print("Índex fora de rang")
# Índex fora de rang
# (l'error real és IndexError; el primer "except ValueError" NO hi coincideix i es passa
#  al següent, que sí que hi coincideix)
```

```python
# Cas normal, SENSE error: s'executen else i finally
try:
    numero = int("8")
    resultat = 10 / numero
except ValueError:
    print("Això no és un número vàlid")
except ZeroDivisionError:
    print("No es pot dividir per zero")
else:
    print("Resultat:", resultat)
finally:
    print("Fi del programa")
# Resultat: 1.25
# Fi del programa
```

```python
# except: genèric (sense tipus) capturant un error inesperat
try:
    resultat = 10 / 0
except:
    print("Hi ha hagut un error")
# Hi ha hagut un error
# (captura la ZeroDivisionError igual que capturaria QUALSEVOL altra excepció,
#  fins i tot una que no t'esperaves — per això no és bona pràctica fer-lo servir sempre)
```

---

## Sessió S33 — Preparació certificació (26/04/2027)

Sessió de repàs integrador: no hi ha contingut nou, es revisen els punts que històricament generen més errors als tests fets durant el curs:

- **Tipus i conversions**: `int()`, `float()`, `str()`, `bool()` — què passa quan es converteix un valor "incompatible" (`int("3.5")` dona error, `int(3.5)` trunca a `3`).
- **Bucles**: diferència entre `while` i `for`, efecte exacte de `break` i `continue`, quantes vegades s'executa `range(a, b, pas)`.
- **Strings i llistes**: indexació negativa, *slicing* (`[inici:fi:pas]`), mutabilitat (les llistes es poden modificar «in place», els strings i les tuples no).
- **Diccionaris**: accedir amb `[]` (llança `KeyError` si no existeix) vs. `.get()` (retorna `None` o un valor per defecte si no existeix).
- **Funcions**: pas de paràmetres, valors per defecte, `return` vs. no retornar res (retorna `None` implícitament).
- **Errors**: quin `except` captura quina excepció, ordre d'avaluació de diversos `except`.
- Estratègia d'examen: llegir el codi línia a línia com si es fos l'intèrpret (fer una taula mental de com canvien les variables), no assumir el resultat "a ull"; vigilar amb la indentació (defineix blocs a Python) i amb els paràmetres per defecte "trampa" (mutables com llistes).

### Exemples addicionals

```python
# Tipus i conversions: int() amb strings decimals dona error, float() no
valors = ["10", "3.5", "abc"]
for v in valors:
    try:
        print(int(v))
    except ValueError:
        print(f"'{v}' no es pot convertir a int")
# 10
# '3.5' no es pot convertir a int   (int() no admet punt decimal dins d'un string)
# 'abc' no es pot convertir a int
```

```python
# El "paràmetre per defecte trampa": una llista com a valor per defecte es comparteix
# entre TOTES les crides que no en passin una de pròpia
def afegeix(item, llista=[]):
    llista.append(item)
    return llista

print(afegeix("a"))   # ['a']
print(afegeix("b"))   # ['a', 'b']   <-- inesperat! la llista per defecte NO es reinicialitza cada crida
```

```python
# Traça integradora: bucle + condicional + diccionari, tal com apareixerà al simulacre final
inventari = {"poma": 5, "pera": 0, "kiwi": 3}
disponibles = []
for producte, unitats in inventari.items():
    if unitats > 0:
        disponibles.append(producte)
print(disponibles)   # ['poma', 'kiwi']   ("pera" queda fora perquè unitats val 0)
```
