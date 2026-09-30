# TEORIA — RA4. Aplica bucles `for` per recórrer seqüències i resoldre problemes iteratius

Objectiu general: dominar el bucle `for` sobre `range()` i sobre seqüències (strings, llistes), combinar-lo amb acumuladors, `break`/`continue` i bucles niuats, i saber llegir/predir l'execució de codi amb `for` — l'habilitat més preguntada al Mòdul 3 de l'examen PCEP (PE1).

---

## Sessió S14 — for I: concepte i range() (14/12/2026)

* Un bucle `for` recorre, **un per un i en ordre**, els elements d'una seqüència (o d'un objecte iterable). A diferència de `while`, **no cal portar tu mateix el comptador**: Python el gestiona internament.

```python
for lletra in "casa":
    print(lletra)
# c
# a
# s
# a
```

* `range()` no és una llista: és un **generador de nombres enters** que es crea sota demanda (és eficient en memòria). Té tres formes:
  * `range(stop)` → de `0` a `stop-1`. `range(5)` → `0,1,2,3,4` (5 valors, **mai inclou `stop`**).
  * `range(start, stop)` → de `start` a `stop-1`. `range(2, 6)` → `2,3,4,5`.
  * `range(start, stop, step)` → salta de `step` en `step`. `range(0, 10, 2)` → `0,2,4,6,8`. Si `step` és negatiu, compta cap enrere: `range(5, 0, -1)` → `5,4,3,2,1`.
* Nombre d'elements que genera `range(start, stop, step)`: `max(0, ceil((stop-start)/step))`. Detall clau del PE1: `range(3, 3)` i `range(5, 2)` (sense step negatiu) **no generen cap valor** (0 iteracions), no donen error.
* `for i in range(len(llista))` és el patró clàssic per recórrer una llista **amb accés a l'índex** alhora:

```python
noms = ["Ana", "Bru", "Cia"]
for i in range(len(noms)):
    print(i, noms[i])
# 0 Ana
# 1 Bru
# 2 Cia
```

* `for...else`: la clàusula `else` d'un `for` s'executa **només si el bucle acaba sense `break`**. És poc habitual però apareix al PE1.

### Exemples addicionals

```python
# Cas normal: range amb els tres arguments i pas negatiu
for i in range(10, 0, -3):
    print(i)
# 10
# 7
# 4
# 1
```

```python
# Cas límit: range(3, 3) no genera cap valor -> el cos del for no s'executa mai
for i in range(3, 3):
    print(i)
print("bucle acabat")
# bucle acabat   (no s'imprimeix res més: 0 iteracions, però no és cap error)
```

```python
# Error típic: pensar que range(5) arriba fins al 5
for i in range(5):
    print(i)
# 0
# 1
# 2
# 3
# 4
# (mai apareix el 5! "stop" no s'inclou)
```

```python
# for...else: l'else s'executa perquè el bucle acaba SENSE break
for n in [2, 4, 6, 8]:
    if n % 2 != 0:
        print("Hi ha un senar!")
        break
else:
    print("Tots són parells")
# Tots són parells
```

---

## Sessió S15 — for II (a): sumatoris i comptadors sobre seqüències numèriques (21/12/2026)

* Patró **acumulador**: una variable que es va actualitzant a cada volta del bucle. Cal **inicialitzar-la abans** del `for`.

```python
notes = [6, 8, 4, 9, 7]
suma = 0
for n in notes:
    suma = suma + n   # equivalent a: suma += n
print(suma)      # 34
print(suma / len(notes))   # mitjana: 6.8
```

* Patró **comptador condicional**: acumular només quan es compleix una condició.

```python
aprovats = 0
for n in notes:
    if n >= 5:
        aprovats += 1
print(aprovats)   # 4
```

* Diferència clau que examina el PE1: `suma += n` **modifica** la variable `suma` que ja existia; si t'obliden inicialitzar-la abans del `for`, Python llança `NameError` a la primera volta.
* `+=`, `-=`, `*=`, `/=` són operadors d'assignació augmentada: `x += 1` és exactament `x = x + 1`, s'executa en cada volta, no és una expressió especial de `for`.
* Vigila el **tipus** del resultat: `suma / len(notes)` amb `/` sempre dona `float`, encara que la divisió sigui exacta (`10 / 2` → `5.0`, no `5`).

### Exemples addicionals

```python
# Cas normal: acumulador amb una altra operació (producte, no suma)
notes = [2, 3, 4]
producte = 1
for n in notes:
    producte *= n
print(producte)   # 24
```

```python
# Cas límit: acumulador sobre una llista buida -> es queda amb el valor inicial
buida = []
suma = 0
for n in buida:
    suma += n
print(suma)   # 0  (la llista és buida: el cos del bucle no s'executa cap vegada)
```

```python
# Error típic: oblidar inicialitzar l'acumulador abans del for
for n in [1, 2, 3]:
    total += n   # NameError: name 'total' is not defined
print(total)
```

```python
# L'acumulador no ha de ser sempre numèric: també es pot acumular un string
paraules = ["Hola", "món", "!"]
frase = ""
for p in paraules:
    frase += p + " "
print(frase)   # 'Hola món ! '
```

---

## Sessió S16 — for II (b): cerca i validació de dades dins d'una seqüència (28/12/2026)

* Patró **cerca amb bandera (flag)**: recórrer fins trobar (o no) un element.

```python
stock = ["teclat", "ratolí", "monitor"]
producte = "monitor"
trobat = False
for article in stock:
    if article == producte:
        trobat = True
print(trobat)   # True
```

* El mateix es pot fer de manera més directa amb l'operador `in`, que retorna directament `True`/`False` sense necessitat de bucle explícit: `producte in stock`. El PE1 pregunta sovint per la **equivalència** entre el patró manual amb `for`+flag i l'ús directe de `in`.
* Patró **validació**: comprovar que TOTS els elements compleixen una condició (comptant els que NO la compleixen).

```python
edats = [18, 20, 16, 22]
tots_majors = True
for e in edats:
    if e < 18:
        tots_majors = False
print(tots_majors)   # False
```

* Diferència important amb `while`: un `for` sobre una seqüència ja coneguda **sempre acaba** (nombre finit d'elements); no hi ha risc de bucle infinit com amb `while` (tema de RA3).
* `min()`, `max()` i `sum()` són funcions integrades que fan directament el que faríem "a mà" amb un `for` (buscar el mínim/màxim, sumar). Cal saber-les reconèixer com a alternativa més curta al mateix patró de cerca/acumulació.

### Exemples addicionals

```python
# Cas normal: cerca amb bandera quan l'element NO hi és
stock = ["teclat", "ratolí", "monitor"]
producte = "impressora"
trobat = False
for article in stock:
    if article == producte:
        trobat = True
print(trobat)   # False
```

```python
# Cas límit: validació sobre una llista buida -> es queda amb el valor inicial (True)
edats = []
tots_majors = True
for e in edats:
    if e < 18:
        tots_majors = False
print(tots_majors)   # True  (cap element incompleix la condició perquè no n'hi ha cap)
```

```python
# L'operador "in" fa exactament el mateix que el patró manual de dalt, en una línia
stock = ["teclat", "ratolí", "monitor"]
print("monitor" in stock)   # True
```

```python
# min(), max() i sum() estalvien escriure el bucle manual de cerca/acumulació
notes = [6, 8, 4, 9, 7]
print(min(notes), max(notes), sum(notes))   # 4 9 34
```

---

## Sessió S17 — for II (c): transformació de strings i llistes recorrent-les amb for (04/01/2027)

* Recórrer un **string** amb `for` dona, un per un, cada **caràcter** (un string d'1 sola lletra), en ordre:

```python
text = "Python"
majuscules = ""
for c in text:
    majuscules = majuscules + c.upper()
print(majuscules)   # PYTHON
```

* Patró **filtratge/transformació**: construir un nou resultat (string o llista buida) i anar-hi afegint elements que compleixen (o transformant) els originals.

```python
paraules = ["sol", "cotxe", "mar", "casa"]
llargues = []
for p in paraules:
    if len(p) > 3:
        llargues.append(p)
print(llargues)   # ['cotxe', 'casa']
```

* Els **strings són immutables**: `text[0] = "p"` dona `TypeError`. Per "modificar" un string cal construir-ne un de nou (com a l'exemple de `majuscules` amunt), concatenant amb `+` o amb `.join()`.
* `"".join(llista)` uneix els elements d'una llista de strings en un sol string, sense necessitat de bucle manual — és el patró contrari a recórrer caràcter a caràcter.
* Diferència clau que confon a l'examen: `for c in "abc"` itera sobre **caràcters**, mentre que `for x in [1,2,3]` itera sobre els **elements** de la llista (que poden ser de qualsevol tipus, fins i tot altres llistes).

### Exemples addicionals

```python
# Cas normal: transformar una llista de strings en una llista d'un altre tipus (int)
paraules = ["sol", "cotxe", "mar"]
longituds = []
for p in paraules:
    longituds.append(len(p))
print(longituds)   # [3, 5, 3]
```

```python
# Cas límit: recórrer un string buit -> el cos del for no s'executa mai
compte = 0
for c in "":
    compte += 1
print(compte)   # 0
```

```python
# Error típic: intentar "modificar" un string per índex (els strings són immutables)
text = "gat"
text[0] = "m"
# TypeError: 'str' object does not support item assignment
```

```python
# .join() és el patró invers a recórrer caràcter a caràcter: uneix una llista en un string
lletres = ["p", "y", "t", "h", "o", "n"]
print("".join(lletres))    # python
print("-".join(lletres))   # p-y-t-h-o-n
```

---

## Sessió S18 — for III: break, continue i bucles for niuats (11/01/2027)

* `break` **atura completament** el bucle (surt immediatament, ni acaba la volta actual del cos que queda per sota ni fa cap volta més).
* `continue` **salta només la resta del cos** d'aquesta volta i passa directament a la següent iteració (no atura el bucle).

```python
for n in range(1, 6):
    if n == 3:
        continue
    if n == 5:
        break
    print(n)
# 1
# 2
# 4
```

* Explicació línia a línia (típic exercici PE1): amb `n=3`, el `continue` fa saltar el `print(n)` d'aquella volta (per això no surt el 3); amb `n=5`, el `break` para el bucle abans d'arribar al `print` (per això tampoc surt el 5, ni res després).
* **Bucles niuats**: un `for` dins d'un altre `for`. El bucle intern fa **totes** les seves voltes per cada volta del bucle extern.

```python
for i in range(2):
    for j in range(3):
        print(i, j)
# 0 0
# 0 1
# 0 2
# 1 0
# 1 1
# 1 2
```
Total de voltes del bucle intern: 2 × 3 = 6.

* `break` (o `continue`) dins d'un bucle niuat **només afecta el bucle més intern** en el qual es troba escrit; el bucle extern continua normalment. És un dels punts on més s'equivoca l'alumnat i on el PE1 insisteix molt.

### Exemples addicionals

```python
# break dins d'un bucle niuat: només atura el bucle INTERN, l'extern continua
for i in range(3):
    for j in range(3):
        if j == 1:
            break
        print(i, j)
# 0 0
# 1 0
# 2 0
```

```python
# continue dins d'un bucle niuat: només salta la volta del bucle INTERN
for i in range(2):
    for j in range(3):
        if j == 1:
            continue
        print(i, j)
# 0 0
# 0 2
# 1 0
# 1 2
```

```python
# Cas límit: bucle sense cap "if" que es compleixi mai -> continue no afecta res
for n in range(4):
    if n == 99:
        continue
    print(n)
# 0
# 1
# 2
# 3
```

```python
# Error típic: creure que UN "break" atura els dos bucles niuats
# (per aturar-los tots dos cal una bandera addicional, com aquí)
trobat = False
for i in range(3):
    for j in range(3):
        if i == 1 and j == 1:
            trobat = True
            break
    if trobat:
        break
print(i, j)   # 1 1
```

---

## Sessió S19 — Problemes I: exercicis integradors for + condicionals (18/01/2027)

* Sessió de consolidació: no hi ha concepte nou, es combinen `for`, `range()`, acumuladors, `if`/`elif`/`else` (RA2) i `break`/`continue` en problemes de diverses línies, tal com apareixen a l'examen real (fragments de 8-12 línies).
* Exemple de "lectura de codi" típica del PE1, combinant tot el vist fins ara:

```python
total = 0
for i in range(1, 10):
    if i % 2 == 0:
        continue
    if i > 7:
        break
    total += i
print(total)
```
Traça: `i` recorre 1..9. Parells (`continue`): 2,4,6,8 es salten. Quan `i=9` (imparell) es compleix `i>7` → `break` abans de sumar. Es sumen només 1+3+5+7 = **16**.

* Tècnica recomanada per al PE1: fer una **taula de traça** a mà (columnes: `i`, condicions que es compleixen, valor acumulat) quan el fragment té més de 4-5 línies dins el bucle — evita errors per "llegir per sobre".
* Repàs ràpid d'errors freqüents: oblidar inicialitzar l'acumulador; confondre `break` amb `continue`; oblidar que `range(stop)` no inclou `stop`; oblidar que `/` sempre retorna `float`.

### Exemples addicionals

```python
# Problema 2: construir una llista amb els múltiples de 3
resultat = []
for n in range(1, 8):
    if n % 3 == 0:
        resultat.append(n)
print(resultat)   # [3, 6]
```

```python
# Problema 3: trobar el primer element que compleix una condició
primer_parell = None
for n in [7, 9, 4, 11, 2]:
    if n % 2 == 0:
        primer_parell = n
        break
print(primer_parell)   # 4
```

```python
# Cas límit: si cap element compleix la condició, la variable manté el valor inicial
primer_negatiu = None
for n in [3, 5, 8, 1]:
    if n < 0:
        primer_negatiu = n
        break
print(primer_negatiu)   # None
```

---

## Sessió S20 — Problemes II: exercicis integradors for + strings (25/01/2027)

* Continuació de la consolidació, centrada ara en combinar `for` amb strings: comptar vocals, invertir un string, comprovar palíndroms, comptar ocurrències d'un caràcter.

```python
paraula = "programar"
vocals = "aeiou"
compte = 0
for lletra in paraula:
    if lletra in vocals:
        compte += 1
print(compte)   # 3  (o, a, a)
```

* Mètode `.count()` d'un string fa directament el que sovint es fa "a mà" amb un `for`+comptador: `paraula.count("a")` retorna `3` sense necessitat de bucle. Cal reconèixer quan un fragment amb `for` és equivalent a un mètode integrat més curt (pregunta molt típica del PE1: "quin d'aquests dos fragments fa el mateix que `.count()`?").
* Recordatori: `paraula[::-1]` inverteix un string sense `for` (slicing complet amb pas -1); un `for` que recorre `range(len(paraula)-1, -1, -1)` i va concatenant caràcters fa el mateix "a mà" — és un exercici clàssic per practicar `range()` amb `step` negatiu (S14) juntament amb strings.
* Tanca el bloc de `for`: a partir d'aquí (RA5) el mateix bucle `for` s'aplicarà de manera intensiva sobre llistes com a estructura de dades pròpiament dita.

### Exemples addicionals

```python
# Comprovar si un string és un palíndrom, fent servir slicing (S14/S17)
paraula = "radar"
invertida = paraula[::-1]
print(paraula == invertida)   # True
```

```python
# Cas límit: comptar un caràcter que no apareix mai al string
paraula = "python"
print(paraula.count("z"))   # 0
```

```python
# Error típic: no tenir en compte les majúscules/minúscules en comparar caràcters
paraula = "Elefant"
vocals = "aeiou"
compte = 0
for lletra in paraula:
    if lletra in vocals:
        compte += 1
print(compte)   # 2  ("E" NO compta perquè és majúscula i "aeiou" només té minúscules; només compten "e" i "a"
```

```python
# .count() fa en una línia el mateix que el for+comptador de dalt
paraula = "banana"
print(paraula.count("a"))   # 3
```
