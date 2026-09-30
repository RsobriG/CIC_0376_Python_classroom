# TEORIA — RA1. Prepara l'entorn de treball Python i coneix els fonaments bàsics del llenguatge

Objectiu general: que l'alumnat tingui un entorn de treball (Python + VSCode + Git/GitHub) funcional i
conegui la sintaxi més bàsica de Python (variables, tipus, E/S, operadors) per poder-hi construir la
resta del curs.

---

## Sessió S1 — Configuració de l'entorn Python (14/09/2026)

* **Què és Python:** llenguatge interpretat, multiplataforma i de tipat dinàmic. Què vol dir cada cosa:

  * **Interpretat (no cal compilar):** en un llenguatge *compilat* (C, C++...), abans d'executar el
    programa cal un pas previ (la compilació) que tradueix TOT el codi font a codi màquina d'un cop;
    si hi ha un error en una línia, es detecta en aquest pas encara que el programa no arribi mai a
    executar-la. En Python no hi ha aquest pas separat: l'intèrpret **llegeix i executa les
    instruccions una a una, a mesura que hi arriba**. Conseqüència pràctica important: si una línia
    amb un error mai s'arriba a executar, el programa no falla.

    ```python
    def funcio_amb_bug():
        print(1 / 0)   # ZeroDivisionError

    if False:
        funcio_amb_bug()   # mai es crida

    print("El programa acaba bé")
    # Output: El programa acaba bé   (cap error! la línia del bug mai s'executa)
    ```

    **Com veure-ho amb el depurador (fes-ho ara mateix, no cal esperar a l'activitat):**

    1. Copia aquest codi a un fitxer `prova_interpret.py` a VSCode.
    2. Posa un breakpoint a la línia `print(1 / 0)` (dins de `funcio_amb_bug`) i un altre a la línia
       `if False:`.
    3. Executa amb **F5**. El programa s'atura al primer breakpoint, el de `if False:` — fins aquí,
       normal, és la primera línia amb breakpoint que troba.
    4. Prem **Step Over (F10)** una vegada. Fixa't on salta l'execució (mira la línia ressaltada en
       groc/blau): salta directament a `print("El programa acaba bé")`, **sense entrar mai** dins de
       `funcio_amb_bug()`. El breakpoint que havies posat a `print(1 / 0)` no s'arriba a activar — el
       depurador ho demostra visualment: com que `False` fa que el `if` no s'executi, l'intèrpret ni
       tan sols "toca" aquella línia, i per això el bug que hi ha a dins no té cap efecte.
    5. Ara canvia `if False:` per `if True:` i torna a executar amb F5. Aquesta vegada el breakpoint
       de dins `funcio_amb_bug()` **sí** que s'activa; fes Step Over una última vegada sobre
       `print(1 / 0)` i veuràs com el programa llança `ZeroDivisionError` en aquell instant exacte —
       la mateixa línia de codi, que abans no fallava mai, ara falla perquè aquesta vegada **sí que
       s'executa**.

    Aquest exercici és la millor manera d'entendre "interpretat, línia a línia": el programa no es
    revisa sencer per endavant buscant errors, l'intèrpret només reacciona al que **realment**
    executa, pas a pas — exactament el que acabes de veure amb el depurador.

    *(Nota: internament Python sí que tradueix el codi a "bytecode" abans d'executar-lo, però és un
    pas automàtic i transparent per a qui programa — a efectes pràctics es considera interpretat
    perquè no hi ha cap pas explícit de compilació/build separat.)*

  * **Multiplataforma:** el mateix fitxer `.py`, sense tocar-hi res, s'executa igual a Windows, Linux
    o macOS (sempre que cada sistema tingui Python instal·lat) — no cal "recompilar-lo" per a cada
    sistema operatiu, a diferència d'un executable compilat expressament per a un SO concret.

  * **Tipat dinàmic:** no cal declarar el tipus d'una variable per endavant; el tipus el determina el
    **valor** que té en cada moment, i el mateix nom de variable pot canviar de tipus durant
    l'execució:

    ```python
    x = 5           # ara x és un int
    print(type(x))  # <class 'int'>

    x = "hola"      # el mateix nom ara apunta a un str — Python no s'hi oposa
    print(type(x))  # <class 'str'>
    ```

    En un llenguatge de tipat estàtic (Java, C) caldria declarar `int x = 5;`, i assignar-hi després
    un text seria un error de compilació.
* **L'intèrpret:** el programa `python` (o `python3`) que llegeix el nostre fitxer `.py` i l'executa.
  Es pot fer servir de forma interactiva (REPL, escrivint `python` a la terminal) o executant un
  fitxer (`python programa.py`).
* **Instal·lació:** descarregar Python des de python.org (o gestor de paquets del SO). Comprovar la
  instal·lació amb `python --version` (o `python3 --version`).
* **VSCode:** editor de codi. Cal instal·lar l'extensió oficial **Python** (Microsoft) i, opcionalment,
  **Pylance**. VSCode necessita saber quin intèrpret de Python fer servir (es tria a la cantonada
  inferior dreta o amb `Ctrl+Shift+P` → *Python: Select Interpreter*).
* **Executar codi:** botó "Run" (▶) o `Ctrl+F5` executa sense depurador; `F5` executa **amb** depurador
  (el farem servir a totes les activitats).
* Primer programa:

```python
print("Hola, món")
```

### Exemples addicionals

* Cas normal — un script amb diverses línies s'executa d'una sola tirada, de dalt a baix:

```python
# arxiu suma.py
print("Suma:", 2 + 2)
print("Fi del programa")
# S'executa amb:  python suma.py
# Output:
# Suma: 4
# Fi del programa
```

* Cas especial — el mode interactiu (REPL) executa i mostra el resultat d'una expressió línia a
  línia, sense necessitat de `print()` (això només passa al REPL, no dins d'un fitxer `.py`):

```
>>> 2 + 2
4
>>> print("Hola")
Hola
```

* Error típic — un `SyntaxError` a l'intèrpret (aquí, una cadena de text sense cometa de tancament)
  impedeix que el programa s'arribi a executar; Python indica la línia on ha detectat el problema:

```python
print("Hola)
# SyntaxError: unterminated string literal (detected at line 1)
```

---

## Sessió S2 — GitHub i sistema d'entrega (21/09/2026)

* **Git:** sistema de control de versions. Guarda "fotografies" (commits) de l'estat del codi al llarg
  del temps.
* **GitHub:** servei web que allotja repositoris Git al núvol; el farem servir per entregar activitats.
* **Flux bàsic:**
  * `git clone <url>` — descarrega una còpia local d'un repositori remot.
  * `git add <fitxer>` — marca canvis per incloure'ls al següent commit.
  * `git commit -m "missatge"` — desa una fotografia dels canvis marcats.
  * `git push` — puja els commits locals al repositori remot (GitHub).
  * `git status` — mostra què ha canviat i què està marcat per pujar.
* **`.gitignore`:** fitxer que indica a Git quins fitxers/carpetes NO s'han de pujar mai (p. ex. entorns
  virtuals, fitxers temporals).
* Per entregar una activitat: `add` → `commit` → `push`, i comprovar a la pàgina web de GitHub que els
  fitxers hi apareixen.

### Exemples addicionals

* Cas normal — flux complet d'entrega d'una activitat:

```
git add activitat1.py
git commit -m "Afegeix activitat 1"
git push
```

* Cas especial — `git status` abans de fer `add`, mostrant un fitxer modificat encara no preparat:

```
git status
# On branch main
# Changes not staged for commit:
#   modified: activitat1.py
```

* Error típic — intentar fer `commit` sense haver fet `add` abans: Git no troba res per desar,
  encara que el fitxer s'hagi modificat i es vegi a l'editor:

```
git commit -m "canvis"
# nothing added to commit but untracked files present (use "git add" to track)
```

---

## Sessió S3 — Introducció a Python i print() (28/09/2026)

* **Sintaxi bàsica:** Python no fa servir claus `{}` ni `;` per delimitar blocs; utilitza la
  **indentació** (espais al principi de línia) per saber què pertany a quin bloc. Una indentació
  incorrecta provoca un `IndentationError`.
* **Comentaris:** amb `#` (tot el que hi ha darrere, fins al final de línia, s'ignora).
* **La funció `print()`:** mostra per pantalla el que se li passa com a argument. Pot rebre més d'un
  valor separats per comes (els separa amb un espai per defecte):

```python
print("Hola")          # Hola
print("Suma:", 2 + 3)  # Suma: 5
print(1, 2, 3, sep="-")  # 1-2-3  (paràmetre sep canvia el separador)
```

* **Literal vs. variable:** un *literal* és un valor escrit directament al codi (`5`, `"text"`); una
  *variable* és un nom que referencia un valor guardat a memòria.
* Python distingeix **majúscules de minúscules** (`Nom` i `nom` són variables diferents).

### Exemples addicionals

* Cas normal — un comentari conviu amb codi a la mateixa línia (tot el que va després de `#`
  s'ignora):

```python
edat = 30   # edat és una variable; 30 és un literal
print("Edat:", edat)   # Edat: 30
```

* Cas especial — `print()` cridat sense cap argument simplement escriu una línia buida (no dona
  error):

```python
print("Abans")
print()
print("Després")
# Abans
# (línia buida)
# Després
```

* Error típic — barrejar espais i indentació inconsistent (o oblidar indentar el cos d'un `if`, tema
  que es veurà formalment a RA2) provoca un `IndentationError` abans fins i tot d'executar cap línia:

```python
if True:
print("mal indentat")
# IndentationError: expected an indented block after 'if' statement on line 1
```

---

## Sessió S4 — Variables i tipus de dades (05/10/2026)

* **Declaració de variables:** en Python no cal declarar el tipus; només s'assigna amb `=`:

```python
edat = 25          # int
preu = 4.5         # float
nom = "Joan"       # str
actiu = True       # bool
```

* **Tipus bàsics:** `int` (enter), `float` (decimal), `str` (cadena de text), `bool` (`True`/`False`).
* **`type(valor)`:** funció que retorna el tipus d'un valor/variable. Retorna `<class 'int'>`,
  `<class 'str'>`, etc.
* **Conversió de tipus (*casting*):** `int()`, `float()`, `str()`, `bool()` converteixen un valor a un
  altre tipus.

```python
x = "10"
y = int(x) + 5      # 15  (converteix "10" a enter abans de sumar)
z = str(5) + "10"   # "510"  (converteix 5 a text i concatena, NO suma)
```

* Un error molt habitual: `int("10") + 5` funciona, però `"10" + 5` dona `TypeError` (no es pot sumar
  un `str` i un `int` directament).
* **`bool()` de valors no booleans:** `bool(0)` és `False`, qualsevol altre número és `True`;
  `bool("")` és `False`, qualsevol altra cadena (fins i tot `"False"` com a text!) és `True`.

### Exemples addicionals

* Cas normal — assignació múltiple en una sola línia (assigna cada valor, en ordre, a cada variable):

```python
a, b, c = 1, 2, 3
print(a, b, c)   # 1 2 3
```

* Cas especial — `bool` es comporta com un `int` en operacions aritmètiques (`True` val `1`, `False`
  val `0`):

```python
print(True + True)    # 2
print(True + False)   # 1
print(int(True))      # 1
```

* Error típic — convertir a `int` un text que no és un número enter vàlid llança `ValueError` (no
  `TypeError`, és important distingir-los):

```python
int("abc")
# ValueError: invalid literal for int() with base 10: 'abc'

int("3.5")
# ValueError: invalid literal for int() with base 10: '3.5'  (cal float("3.5") primer)
```

---

## Sessió S5 — Entrada i sortida (12/10/2026)

* **`input(missatge)`:** mostra `missatge` i espera que l'usuari escrigui una línia; **sempre retorna
  un `str`**, encara que l'usuari escrigui números (cal convertir-los amb `int()`/`float()` si calen
  com a números).

```python
nom = input("Com et dius? ")
edat = int(input("Quina edat tens? "))
```

* **Concatenació amb `+`:** només entre `str`; per barrejar tipus cal convertir amb `str()`.
* **f-strings (`f"..."`):** manera moderna de formatar text incrustant variables amb `{}`:

```python
nom = "Anna"
edat = 30
print(f"{nom} té {edat} anys")     # Anna té 30 anys
print(f"L'any que ve en tindrà {edat + 1}")  # es poden posar expressions dins {}
```

* Diferència entre `,` dins `print()` (afegeix espais automàticament) i `+` (concatenació estricta,
  requereix que tot sigui `str`).

### Exemples addicionals

* Cas normal — `input()` cridat sense cap missatge (vàlid, simplement no mostra res abans d'esperar
  l'entrada) i conversió a `float`:

```python
preu = float(input())   # si l'usuari escriu "4.5", preu val 4.5 (float, no str)
print(preu * 2)          # 9.0
```

* Cas especial — les f-strings admeten especificadors de format, com arrodonir un decimal:

```python
preu = 3.14159
print(f"Preu: {preu:.2f} €")   # Preu: 3.14 €
```

* Error típic — intentar concatenar directament un `str` amb un `int` (resultat d'`input()` sense
  convertir prèviament, o qualsevol altra variable numèrica) llança `TypeError`:

```python
edat = 20
print("Tens " + edat + " anys")
# TypeError: can only concatenate str (not "int") to str
```

---

## Sessió S6 — Operadors i expressions (19/10/2026)

* **Aritmètics:** `+ - * /` (divisió sempre retorna `float`), `//` (divisió entera, arrodoneix cap
  avall), `%` (mòdul/residu), `**` (potència).

```python
7 / 2    # 3.5
7 // 2   # 3
7 % 2    # 1
2 ** 3   # 8
```

* **De comparació:** `== != > < >= <=` → sempre retornen un `bool`.
* **Lògics:** `and`, `or`, `not` — combinen expressions booleanes. `and`/`or` fan *short-circuit*: si el
  resultat ja es pot determinar amb el primer operand, el segon no s'avalua.
* **Precedència d'operadors** (de més a menys prioritat, resumit): parèntesis → `**` → `* / // %` →
  `+ -` → comparacions → `not` → `and` → `or`. Els parèntesis sempre es poden fer servir per aclarir.
* Errors habituals: confondre `=` (assignació) amb `==` (comparació); oblidar que `//` amb negatius
  arrodoneix cap a **menys infinit**, no cap a zero (`-7 // 2` és `-4`, no `-3`).

### Exemples addicionals

* Cas normal — Python permet **comparacions encadenades**, que equivalen a combinar-les amb `and`:

```python
x = 7
print(1 < x < 10)          # True   (equival a: 1 < x and x < 10)
print(1 < x and x < 5)     # False  (x val 7, no és menor que 5)
```

* Cas especial — divisió entera i mòdul amb un operand negatiu (el resultat sempre "arrodoneix cap a
  baix", i el residu pren el signe del divisor):

```python
print(-7 // 2)   # -4  (no -3)
print(-7 % 2)    # 1   (el residu té el mateix signe que el divisor, 2)
print(7 // -2)   # -4
print(7 % -2)    # -1
```

* Error típic — fer servir `=` (assignació) allà on tocava `==` (comparació) dins d'una condició no
  és simplement un resultat inesperat: Python ho detecta com un error de sintaxi abans d'executar res:

```python
x = 5
if x = 5:
    print("mal")
# SyntaxError: invalid syntax. Maybe you meant '==' or ':=' instead of '='?
```
