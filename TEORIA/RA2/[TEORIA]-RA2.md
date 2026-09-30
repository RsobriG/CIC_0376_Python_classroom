# TEORIA — RA2. Aplica estructures condicionals i treballa amb cadenes de text (strings)

Objectiu general: saber llegir i entendre codi que pren decisions (`if`/`elif`/`else`) i codi que manipula text (strings), que és la base del Mòdul 2-3 de l'examen PCEP (PE1).

---

## Sessió S7 — Condicionals I: if / elif / else, operadors de comparació i lògics (and/or/not) (26/10/2026)

### `if` / `elif` / `else`

- Un bloc `if` executa el codi indentat **només si** la condició és `True`.
- `elif` (abreviatura de "else if") es comprova **només si** el/els `if`/`elif` anteriors han estat `False`.
- `else` s'executa si **cap** de les condicions anteriors ha estat certa. És opcional.
- Python avalua les condicions **en ordre** i s'atura en la primera que és certa (les següents `elif`/`else` no s'arriben a mirar).

```python
nota = 6
if nota >= 9:
    print("Excel·lent")
elif nota >= 5:
    print("Aprovat")
else:
    print("Suspès")
# Output: Aprovat
```

- La indentació (normalment 4 espais) és **obligatòria** en Python: defineix quin codi pertany al bloc. Un error d'indentació provoca `IndentationError`.

### Operadors de comparació

Retornen sempre un `bool` (`True` o `False`): `==` (igual), `!=` (diferent), `<`, `>`, `<=`, `>=`.

```python
print(5 == 5.0)   # True (compara el valor, no el tipus)
print(5 == "5")   # False (tipus diferents mai són iguals amb ==)
```

### Operadors lògics: `and`, `or`, `not`

- `and`: `True` només si **totes dues** condicions són `True`.
- `or`: `True` si **almenys una** és `True`.
- `not`: inverteix el valor booleà.
- Python fa servir ***short-circuit evaluation***: en `A and B`, si `A` és `False`, ja no avalua `B` (el resultat ja és `False`); en `A or B`, si `A` és `True`, ja no avalua `B`.

```python
edat = 20
te_carnet = False
print(edat >= 18 and te_carnet)   # False
print(edat >= 18 or te_carnet)    # True
```

### Exemples addicionals

- Cas normal, tres branques amb el llindar just al límit (`elif` amb `>=`):

```python
temperatura = 15
if temperatura > 30:
    print("Calor")
elif temperatura >= 15:
    print("Temperat")
else:
    print("Fred")
# Output: Temperat  (15 no és > 30, però sí >= 15: entra per l'elif)
```

- Error típic: confondre `=` (assignació) amb `==` (comparació) dins d'una condició. Python ho detecta
  directament com a error de sintaxi, no com un bug silenciós:

```python
edat = 17
if edat = 18:      # ERROR
    print("Té 18 anys")
# SyntaxError: invalid syntax. Maybe you meant '==' or ':=' instead of '='?
```

- `==` compara **valor**, `is` compara **identitat** (si són literalment el mateix objecte en memòria).
  Dues llistes amb el mateix contingut són `==` però no necessàriament `is`:

```python
a = [1, 2, 3]
b = [1, 2, 3]
c = a
print(a == b)   # True  (mateix contingut)
print(a is b)   # False (objectes diferents en memòria)
print(a is c)   # True  (c és literalment el mateix objecte que a)
```

- El *short-circuit* no és només teoria: es pot demostrar que Python realment **no arriba a executar**
  el segon operand quan ja no cal:

```python
def marca(nom, valor):
    print("avaluant", nom)
    return valor

print(marca("A", False) and marca("B", True))
# avaluant A
# False        <-- "B" mai s'arriba a avaluar, perquè A ja és False

print(marca("C", True) or marca("D", True))
# avaluant C
# True         <-- "D" mai s'arriba a avaluar, perquè C ja és True
```

- Precedència entre `and` i `or`: `and` té **més prioritat** que `or` (com `*` respecte `+`). Sense
  parèntesis, es pot llegir malament:

```python
print(True or False and False)     # True  (equival a: True or (False and False))
print((True or False) and False)   # False (aquí els parèntesis canvien el resultat)
```

---

## Sessió S8 — Condicionals II: condicionals niuats; introducció a strings: indexació i slicing (02/11/2026)

### Condicionals niuats

Un `if` pot contenir un altre `if` a dins. Cada nivell d'indentació és un nivell de niuament.

```python
x = 15
if x > 10:
    if x % 2 == 0:
        print("Major que 10 i parell")
    else:
        print("Major que 10 i senar")
# Output: Major que 10 i senar
```

Sovint un condicional niuat es pot simplificar amb `and`: l'exemple anterior equival a `if x > 10 and x % 2 == 0:`.

### Strings: indexació

- Un string és una seqüència de caràcters. Cada caràcter té una **posició (índex)**, començant per `0`.
- `text[i]` retorna el caràcter a la posició `i`.
- Els índexs **negatius** compten des del final: `text[-1]` és l'últim caràcter.
- Accedir a un índex fora de rang llança `IndexError`.

```python
paraula = "Python"
print(paraula[0])    # P
print(paraula[-1])   # n
print(paraula[10])   # IndexError
```

### Strings: slicing (`[inici:final:pas]`)

- `text[a:b]` retorna un **nou string** amb els caràcters des de l'índex `a` (inclòs) fins a `b` (**exclòs**).
- Si s'omet `a`, comença des del principi; si s'omet `b`, arriba fins al final.
- `text[::pas]` permet saltar caràcters; `text[::-1]` inverteix el string.
- El slicing **mai** llança `IndexError` encara que els límits se surtin de rang.

```python
paraula = "Python"
print(paraula[0:3])   # Pyt
print(paraula[2:])    # thon
print(paraula[:2])    # Py
print(paraula[::-1])  # nohtyP
print(paraula[0:100]) # Python (no dona error)
```

- Els strings són **immutables**: `paraula[0] = "J"` llança `TypeError`. Per "canviar" un string cal crear-ne un de nou.

### Exemples addicionals

- Condicional niuat de 3 nivells (cas normal): un patró habitual quan cal comprovar diverses
  condicions en cadena abans de decidir:

```python
edat = 20
te_carnet = True
te_cotxe = False
if edat >= 18:
    if te_carnet:
        if te_cotxe:
            print("Pot conduir el seu cotxe")
        else:
            print("Pot conduir, però no en té")
    else:
        print("Necessita carnet")
else:
    print("Massa jove")
# Output: Pot conduir, però no en té
```

- Condicional niuat combinat amb `!=` (cas amb valor negatiu, per veure que l'ordre de comprovació
  importa):

```python
n = -3
if n != 0:
    if n > 0:
        print("Positiu")
    else:
        print("Negatiu")
else:
    print("Zero")
# Output: Negatiu
```

- Slicing amb límits fora de rang o buits — casos que confonen molt a l'examen perquè **mai** donen
  error, a diferència de la indexació simple:

```python
paraula = "gat"
print(paraula[5:10])   # ''   (fora de rang -> string buit, NO IndexError)
print(paraula[3:])     # ''   (comença just després de l'últim caràcter -> buit)
print(paraula[-2:])    # 'at' (els dos últims caràcters)
print(paraula[::2])    # 'gt' (un de cada dos caràcters)
print(paraula[1:1])    # ''   (inici == final -> sempre buit)
```

---

## Sessió S9 — Condicionals III: mètodes de strings combinats amb condicionals (09/11/2026)

Tots aquests mètodes **retornen un valor nou** (els strings són immutables: mai modifiquen l'original).

| Mètode | Què fa | Què retorna |
|---|---|---|
| `.upper()` | Converteix tot a majúscules | Un nou `str` |
| `.lower()` | Converteix tot a minúscules | Un nou `str` |
| `.strip()` | Elimina espais (i salts de línia) al principi i al final | Un nou `str` |
| `.split(sep)` | Divideix el string pel separador indicat (per defecte, espais) | Una `list` de `str` |
| `.replace(a, b)` | Substitueix totes les aparicions de `a` per `b` | Un nou `str` |
| `.find(sub)` | Cerca la subcadena `sub` | L'índex de la primera aparició, o `-1` si no la troba |
| `len(text)` | Compta caràcters (és una funció, no un mètode) | Un `int` |
| `sub in text` | Comprova si `sub` apareix dins `text` | Un `bool` |

```python
frase = "  Hola Món  "
print(frase.strip())          # "Hola Món"
print(frase.strip().upper())  # "HOLA MÓN"
print(frase.strip().split())  # ['Hola', 'Món']
print("Món" in frase)         # True
print(frase.find("Món"))      # 7 (índex on comença "Món" dins l'string original)
print(frase.find("xyz"))      # -1
```

### Combinant strings amb condicionals

```python
paraula = "casa"
if paraula == paraula.lower():
    print("Ja estava en minúscules")

text = "usuari@exemple.com"
if "@" in text and text.count("@") == 1:
    print("Sembla un email vàlid")
```

- Compte: `.upper()` i `.lower()` **no modifiquen** la variable original; si vols "actualitzar-la" cal reassignar-la: `paraula = paraula.upper()`.

### Exemples addicionals

- `.split()` amb separador explícit i amb límit de divisions (paràmetre `maxsplit`), un detall que
  sovint es pregunta a l'examen:

```python
frase = "un,dos,tres,quatre"
print(frase.split(","))       # ['un', 'dos', 'tres', 'quatre']
print(frase.split(",", 2))    # ['un', 'dos', 'tres,quatre']  <- només fa 2 talls
```

- `.count()` i `.replace()` amb el paràmetre opcional que limita quantes vegades es reemplaça:

```python
text = "abcabcabc"
print(text.count("abc"))          # 3
print(text.replace("a", "X"))     # XbcXbcXbc     (totes les "a")
print(text.replace("a", "X", 1))  # Xbcabcabc     (només la primera)
```

- `.startswith()` / `.endswith()`, útils per validacions, combinats amb `and` en una condició:

```python
s = "Hola"
print(s.startswith("Ho"))   # True
print(s.endswith("la"))     # True

contrasenya = "abc123"
if len(contrasenya) >= 6 and contrasenya.isalnum():
    print("Format bàsic correcte")
# Output: Format bàsic correcte
```

- Error típic: intentar concatenar un string amb un `int` directament amb `+` (recordatori del RA1,
  però és un dels errors més freqüents quan es combinen strings amb dades numèriques):

```python
n = 5
resultat = "Valor: " + n
# TypeError: can only concatenate str (not "int") to str
# Correcte: "Valor: " + str(n)
```
