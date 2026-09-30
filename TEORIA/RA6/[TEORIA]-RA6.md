# TEORIA — RA6. Utilitza tuples, sets i diccionaris per organitzar dades

Objectiu general: conèixer les estructures de dades restants de Python (tuples, sets i diccionaris),
saber quan fer servir cadascuna i recórrer-les correctament amb bucles `for`.

---

## Sessió S25 — Tuples i sets (01/03/2027)

### Tuples

- Una **tupla** és una seqüència ordenada d'elements, com una llista, però **immutable**: un cop creada
  no es pot afegir, eliminar ni canviar cap element.
- Es creen amb parèntesis `()` (opcionals) separant els elements amb comes:

```python
punt = (3, 4)
colors = "vermell", "verd", "blau"   # els parèntesis són opcionals: també és una tupla
```

- S'accedeix als elements igual que a les llistes, per índex (`punt[0]` val `3`) i es poden recórrer
  amb `for`.
- **Intentar modificar-la llança `TypeError`:**

```python
punt = (3, 4)
punt[0] = 10   # TypeError: 'tuple' object does not support item assignment
```

- **Tupla d'un sol element**: cal la coma final, si no és un `int` (o el tipus que sigui) entre parèntesis:

```python
a = (5,)     # tupla d'un element
b = (5)      # això és un int, NO una tupla
```

- **Packing i unpacking**: es pot "empaquetar" diversos valors en una tupla i "desempaquetar-la" en
  diverses variables alhora:

```python
persona = ("Anna", 28)       # packing
nom, edat = persona          # unpacking
print(nom, edat)             # Anna 28
```

- Per què serveixen: per agrupar dades que no han de canviar (coordenades, dates, valors de retorn
  múltiples d'una funció) i perquè, en ser immutables, es poden fer servir com a claus de diccionari
  (les llistes no es poden fer servir com a claus, perquè són mutables).

  Per què la mutabilitat importa aquí: un diccionari, per trobar una clau ràpidament (sense haver de
  mirar-les totes una a una), calcula per a cada clau un número fix anomenat **hash** i el fa servir
  per decidir on "desar-la" internament. Si la clau pogués canviar de valor després (com una llista),
  el seu hash canviaria i el diccionari ja no la trobaria on l'havia desat — perdria la clau. Com que
  una tupla mai canvia un cop creada, el seu hash és sempre el mateix, i per això és una clau vàlida:

  ```python
  d = {(0, 0): "origen", (1, 1): "diagonal"}
  print(d[(0, 0)])      # origen  (una tupla SÍ es pot fer servir com a clau)

  d2 = {[0, 0]: "origen"}
  # TypeError: unhashable type: 'list'  (una llista NO es pot fer servir, és mutable)
  ```

### Sets

- Un **set** és una col·lecció **no ordenada** d'elements **únics** (no permet duplicats).
- Es crea amb claus `{}` o amb `set()`:

```python
fruites = {"poma", "pera", "poma", "kiwi"}
print(fruites)          # {'poma', 'pera', 'kiwi'}  -> el duplicat "poma" desapareix
buit = set()            # {} SOL crea un diccionari buit, no un set!
```

- No té índexs (no es pot fer `fruites[0]`, dona `TypeError`), perquè no té ordre garantit.
- Operacions de conjunts més habituals:

| Operació | Símbol | Mètode equivalent |
| :---- | :---: | :---- |
| Unió | `a \| b` | `a.union(b)` |
| Intersecció | `a & b` | `a.intersection(b)` |
| Diferència | `a - b` | `a.difference(b)` |
| Pertinença | `"poma" in fruites` | — |

```python
a = {1, 2, 3}
b = {2, 3, 4}
print(a | b)   # {1, 2, 3, 4}
print(a & b)   # {2, 3}
print(a - b)   # {1}
```

- `add(x)` afegeix un element; `remove(x)` l'elimina (llança `KeyError` si no hi és); `discard(x)`
  també l'elimina però **no** dona error si no hi és.

### Exemples addicionals

**Tuples — cas normal (accés i longitud):**

```python
coordenades = (10, 20, 30)
print(coordenades[1])       # 20
print(len(coordenades))     # 3
```

**Tuples — error típic (desempaquetar amb el nombre equivocat de variables):**

```python
punt = (5, 6)
x, y, z = punt
# ValueError: not enough values to unpack (expected 3, got 2)
```

**Tuples — cas normal (concatenar i repetir creen tuples noves, no modifiquen les originals):**

```python
a = (1, 2)
b = (3, 4)
print(a + b)     # (1, 2, 3, 4)
print(a * 2)     # (1, 2, 1, 2)
```

**Sets — cas normal (eliminar duplicats d'una llista):**

```python
notes = [5, 7, 5, 9, 7, 10]
notes_uniques = set(notes)
print(len(notes_uniques))       # 4  (els duplicats 5 i 7 s'eliminen)
print(sorted(notes_uniques))    # [5, 7, 9, 10]  (sorted() per veure-ho en ordre)
```

**Sets — cas límit (la diferència `a - b` NO és el mateix que `b - a`):**

```python
a = {1, 2, 3}
b = {2, 3, 4}
print(a - b)     # {1}   (el que hi ha a `a` i no a `b`)
print(b - a)     # {4}   (el que hi ha a `b` i no a `a`) — resultat diferent!
```

**Sets — error típic (`remove` vs `discard` amb un element que no hi és):**

```python
fruites = {"poma", "pera"}
fruites.discard("kiwi")   # no fa res, no dona error (kiwi no hi era)
fruites.remove("kiwi")    # KeyError: 'kiwi'
```

---

## Sessió S26 — Diccionaris (08/03/2027)

- Un **diccionari** (`dict`) emmagatzema parelles **clau: valor**. Les claus han de ser úniques i
  d'un tipus immutable (string, número, tupla...); els valors poden ser de qualsevol tipus.

```python
alumne = {"nom": "Marc", "nota": 7.5, "aprovat": True}
```

- **Accés**: `alumne["nom"]` retorna `"Marc"`. Si la clau no existeix, llança `KeyError`.
- **`.get(clau, per_defecte)`**: retorna el valor de la clau, o `None` (o el valor per defecte indicat)
  si la clau no existeix, **sense** llançar error. És la forma segura d'accedir-hi:

```python
print(alumne.get("nota"))          # 7.5
print(alumne.get("edat"))          # None (no hi ha "edat")
print(alumne.get("edat", 0))       # 0 (valor per defecte indicat)
```

- **Afegir o modificar** una clau: `alumne["edat"] = 20` (si la clau no existia, l'afegeix; si existia,
  la sobreescriu).
- **Eliminar una clau**: `del alumne["aprovat"]`, o `alumne.pop("aprovat")` (que a més retorna el valor
  eliminat).
- **Comprovar si una clau existeix**: `"nom" in alumne` (comprova les CLAUS, no els valors).

```python
d = {"a": 1, "b": 2}
print("a" in d)      # True  (mira les claus)
print(1 in d)        # False (1 és un valor, no una clau)
```

### Exemples addicionals

**Cas normal (construir un diccionari afegint claus una a una):**

```python
inventari = {}
inventari["poma"] = 10
inventari["pera"] = 5
print(inventari)     # {'poma': 10, 'pera': 5}
```

**Cas límit (assignar una clau que ja existeix NO crea una entrada nova, la sobreescriu):**

```python
d = {"x": 1}
d["x"] = 99
print(d)         # {'x': 99}
print(len(d))    # 1  (segueix havent-hi només una clau, no dues)
```

**Error típic (accedir amb `[]` a una clau que no existeix, en comptes de fer servir `.get()`):**

```python
d = {"a": 1}
print(d["b"])
# KeyError: 'b'
```

**Cas normal (crear un diccionari a partir d'una llista de parelles amb `dict()`):**

```python
parells = [("a", 1), ("b", 2)]
d = dict(parells)
print(d)     # {'a': 1, 'b': 2}
```

---

## Sessió S28 — Recorreguts de diccionaris (22/03/2027)

- Recórrer NOMÉS les claus (comportament per defecte d'un `for` sobre un diccionari):

```python
alumne = {"nom": "Marc", "nota": 7.5}
for clau in alumne:
    print(clau)          # nom / nota
```

- **`.keys()`**: retorna una vista amb totes les claus (equivalent a l'anterior, però explícit).
- **`.values()`**: retorna una vista amb tots els valors:

```python
for valor in alumne.values():
    print(valor)          # Marc / 7.5
```

- **`.items()`**: retorna una vista de **parelles (clau, valor)**, la forma més habitual de recórrer
  un diccionari quan es necessiten totes dues coses alhora:

```python
for clau, valor in alumne.items():
    print(clau, "->", valor)
# nom -> Marc
# nota -> 7.5
```

- **Diccionaris niuats**: un valor d'un diccionari pot ser un altre diccionari (o una llista):

```python
alumnes = {
    "a1": {"nom": "Marc", "nota": 7.5},
    "a2": {"nom": "Laia", "nota": 9},
}
print(alumnes["a2"]["nom"])     # Laia

for id_alumne, dades in alumnes.items():
    print(id_alumne, dades["nom"])
```

### Exemples addicionals

**Cas normal (acumular sobre `.values()`):**

```python
preus = {"poma": 2, "pera": 3, "kiwi": 4}
total = 0
for valor in preus.values():
    total += valor
print(total)     # 9
```

**Cas límit (recórrer un diccionari buit: 0 voltes, no dona error):**

```python
buit = {}
for clau in buit:
    print(clau)
print("bucle acabat")
# bucle acabat   <- és l'única línia que s'imprimeix: el for no fa cap volta
```

**Error típic (oblidar els parèntesis de `.items()`):**

```python
d = {"a": 1}
for clau, valor in d.items:
    print(clau, valor)
# TypeError: 'builtin_function_or_method' object is not iterable
# (d.items sense parèntesis és el mètode en si, no el resultat de cridar-lo)
```

**Cas normal (filtrar un diccionari niuat i construir una llista amb el resultat):**

```python
alumnes = {
    "a1": {"nom": "Marc", "nota": 7.5},
    "a2": {"nom": "Laia", "nota": 9},
}
aprovats = []
for id_alumne, dades in alumnes.items():
    if dades["nota"] >= 5:
        aprovats.append(dades["nom"])
print(aprovats)     # ['Marc', 'Laia']
```
