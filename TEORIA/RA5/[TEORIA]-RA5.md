# TEORIA — RA5. Utilitza llistes per emmagatzemar i processar col·leccions de dades

Objectiu general: saber crear llistes, accedir-hi i modificar-les amb els seus mètodes, i recórrer-les
amb bucles — sabent en tot moment què fa cada operació i què retorna (o no retorna).

---

## Sessió S22 — Llistes: creació i accés (08/02/2027)

* Una **llista** (`list`) és una seqüència **ordenada** i **mutable** de valors, que poden ser de
  tipus diferents dins de la mateixa llista.

```python
nombres = [3, 1, 4, 1, 5]
mixta = [1, "dos", 3.0, True]
buida = []
```

* **Accés per índex** (comença a 0):

```python
fruites = ["poma", "pera", "kiwi"]
fruites[0]     # 'poma'
fruites[2]     # 'kiwi'
fruites[3]     # IndexError: list index out of range
```

* **Índexs negatius**: `-1` és l'últim element, `-2` el penúltim...

```python
fruites[-1]    # 'kiwi'
```

* **`len()`** retorna el nombre d'elements de la llista (no l'índex més alt).

```python
len(fruites)   # 3
```

* **Slicing** `llista[inici:final:pas]` — el `final` **no s'inclou** (igual que amb strings i `range()`).

```python
n = [10, 20, 30, 40, 50]
n[1:3]     # [20, 30]
n[:2]      # [10, 20]
n[2:]      # [30, 40, 50]
n[::-1]    # [50, 40, 30, 20, 10]  (invertida)
```

* Un slice **sempre retorna una llista nova** (encara que tingui 0 o 1 elements); un índex simple
  retorna l'element (del tipus que sigui).

* **Llistes niuades** (llistes dins de llistes): s'accedeix encadenant índexs.

```python
matriu = [[1, 2], [3, 4]]
matriu[0]      # [1, 2]
matriu[0][1]   # 2
```

* Comprovar pertinença amb `in`:

```python
"pera" in fruites     # True
```

### Exemples addicionals

Cas normal — accedir i fer slicing d'una llista de temperatures:

```python
temperatures = [21, 19, 23, 18, 25]
print(len(temperatures))       # 5
print(temperatures[1:4])       # [19, 23, 18]  (índexs 1, 2 i 3; el 4 no s'inclou)
print(temperatures[-2])        # 18  (penúltim element)
```

Cas límit — una llista buida: `len()` val `0` i el slicing **mai** dona error, però l'accés directe sí:

```python
buida = []
print(len(buida))     # 0
print(buida[0:5])     # []   (un slice fora de rang simplement retorna buit, no error)
buida[0]               # IndexError: list index out of range
```

Error típic — un índex negatiu que se surt de rang per l'altre costat: amb 3 elements, els índexs
vàlids van de `-3` a `2` (o de `0` a `2`); `-4` ja no existeix:

```python
lletres = ["a", "b", "c"]
lletres[-4]     # IndexError: list index out of range
```

Llistes niuades amb un cas real (una llista d'alumnes, cadascun representat com una sub-llista
`[nom, nota]`): cal encadenar dos índexs per arribar a una dada concreta.

```python
notes_per_alumne = [["Ana", 7], ["Bru", 5]]
print(notes_per_alumne[1][0])   # 'Bru'  (nom del segon alumne)
print(notes_per_alumne[1][1])   # 5      (nota del segon alumne)
```

---

## Sessió S23 — Llistes: mètodes i problemes (15/02/2027)

* Mètodes que **modifiquen la llista "in place"** (la muten) i **retornen `None`**:

```python
llista = [3, 1, 2]
resultat = llista.append(9)
print(resultat)   # None  <-- error molt típic pensar que retorna la llista
print(llista)     # [3, 1, 2, 9]
```

| Mètode | Què fa | Retorna |
| :---- | :---- | :---- |
| `.append(x)` | Afegeix `x` al final | `None` |
| `.insert(i, x)` | Insereix `x` a la posició `i` | `None` |
| `.remove(x)` | Elimina la **primera** ocurrència del valor `x` (`ValueError` si no hi és) | `None` |
| `.pop()` / `.pop(i)` | Elimina i **retorna** l'últim element (o el de la posició `i`) | l'element eliminat |
| `.sort()` | Ordena la llista in place (ascendent per defecte; `reverse=True` per descendent) | `None` |
| `.reverse()` | Inverteix l'ordre in place | `None` |
| `.index(x)` | Retorna la posició de la primera ocurrència de `x` (`ValueError` si no hi és) | un `int` |
| `.count(x)` | Compta quantes vegades apareix `x` | un `int` |

* **`sorted(llista)`** (funció, no mètode) **SÍ retorna** una llista nova ordenada i deixa l'original
  intacta — a diferència de `.sort()`.

```python
a = [3, 1, 2]
b = sorted(a)
print(a)   # [3, 1, 2]  (sense canvis)
print(b)   # [1, 2, 3]
```

* **Còpia per referència vs còpia real** — el tema més important d'aquesta sessió:

```python
a = [1, 2, 3]
b = a            # b NO és una còpia: b i a apunten a la MATEIXA llista
b.append(4)
print(a)         # [1, 2, 3, 4]  <-- a també ha canviat!

c = a.copy()     # (o c = a[:])   ara sí és una còpia independent
c.append(99)
print(a)         # [1, 2, 3, 4]  (sense el 99)
```

* Concatenar (`+`) i repetir (`*`) llistes **sí que creen llistes noves**:

```python
[1, 2] + [3, 4]   # [1, 2, 3, 4]
[0] * 3           # [0, 0, 0]
```

### Exemples addicionals

Cas normal — `.pop(i)` amb índex concret (a diferència de `.pop()` sense argument, que treu l'últim):

```python
cistella = ["poma", "pera", "kiwi"]
primer = cistella.pop(0)
print(primer)      # 'poma'
print(cistella)     # ['pera', 'kiwi']
```

Error típic — `.remove()` amb un valor que no hi és:

```python
nums = [1, 2, 3]
nums.remove(9)     # ValueError: list.remove(x): x not in list
```

Cas normal — `.sort()` també funciona amb strings (ordre alfabètic) i accepta `reverse=True`:

```python
noms = ["Bru", "Ana", "Cia"]
noms.sort(reverse=True)
print(noms)        # ['Cia', 'Bru', 'Ana']
```

Cas límit — el parany de la **còpia superficial** (*shallow copy*): `.copy()` només copia el primer
nivell. Si la llista conté altres llistes a dins, aquestes sub-llistes **continuen sent compartides**:

```python
original = [[1, 2], [3, 4]]
copia = original.copy()       # còpia superficial
copia[0].append(99)
print(original)   # [[1, 2, 99], [3, 4]]  <-- la llista interna SÍ que s'ha vist afectada!
```

---

## Sessió S24 — Llistes + bucles (22/02/2027)

* Recórrer una llista amb `for`:

```python
notes = [7, 4, 9, 5]
for n in notes:
    print(n)
```

* Recórrer amb índex quan es necessita la posició, amb `range(len(...))` o amb `enumerate()`:

```python
for i in range(len(notes)):
    print(i, notes[i])

for i, n in enumerate(notes):
    print(i, n)
```

* Patrons habituals: **filtrar** (construir una llista nova amb els elements que compleixen una
  condició) i **transformar** (construir una llista nova aplicant una operació a cada element):

```python
aprovats = []
for n in notes:
    if n >= 5:
        aprovats.append(n)
print(aprovats)   # [7, 9, 5]

dobles = []
for n in notes:
    dobles.append(n * 2)
print(dobles)     # [14, 8, 18, 10]
```

* **List comprehension** (forma abreujada, molt habitual en codi Python real i que apareix al PE1
  a nivell de reconeixement, no cal dominar-la per escriure-la):

```python
aprovats = [n for n in notes if n >= 5]
dobles = [n * 2 for n in notes]
```

* Compte amb modificar una llista **mentre** la recorres amb `for` (pot saltar-se elements o donar
  resultats inesperats); és més segur construir-ne una de nova.

### Exemples addicionals

Cas normal — acumulador amb `for` sobre una llista de preus:

```python
preus = [12.5, 8.0, 20.0]
total = 0
for p in preus:
    total += p
print(total)     # 40.5
```

Cas límit — recórrer una llista buida: el cos del `for` no s'executa **cap** vegada (0 iteracions),
no dona cap error:

```python
buida = []
for x in buida:
    print(x)
print("Bucle acabat")   # només s'imprimeix això
```

Error típic — modificar una llista mentre la recorres amb `for`: eliminar elements desplaça els
índexs interns i el bucle **se salta** elements sense adonar-se'n. Aquí es volien eliminar TOTS els
parells, però en queden dos:

```python
nums = [2, 4, 6, 8]
for n in nums:
    if n % 2 == 0:
        nums.remove(n)
print(nums)   # [4, 8]  <-- en eliminar el 2, tots els elements es desplacen una posició, i el
              #  bucle es "salta" el 4 en la comprovació següent
```

Cas normal — `enumerate()` amb el paràmetre `start`, per començar a comptar des d'un altre número
diferent de `0` (útil, per exemple, per mostrar una llista numerada des d'1):

```python
tasques = ["Comprar", "Cuinar", "Netejar"]
for num, tasca in enumerate(tasques, start=1):
    print(num, tasca)
# 1 Comprar
# 2 Cuinar
# 3 Netejar
```
