# TEORIA — RA3. Aplica bucles `while` per repetir instruccions de manera controlada

Objectiu general: entendre com Python repeteix instruccions mentre es compleix una condició, i saber
llegir/predir l'execució d'un bucle `while` (nombre de voltes, valor final de les variables, si arriba
a aturar-se o no).

---

## Sessió S11 — while I: concepte i estructura (23/11/2026)

* Un bucle `while` repeteix un bloc de codi **mentre** una condició sigui `True`. La condició es
  reavalua **abans** de cada iteració (inclosa la primera).
* Estructura:

```python
while condicio:
    # cos del bucle (indentat)
    ...
```

* Si la condició és `False` la primera vegada, el cos **no s'executa mai** (0 voltes).
* El cos del bucle ha de fer, tard o d'hora, que la condició passi a ser `False`; si no, el bucle no
  s'atura mai (**bucle infinit**).

```python
n = 3
while n > 0:
    print(n)
    n = n - 1
print("Enganxats!")
```

  * Output: `3`, `2`, `1`, `Enganxats!` — 3 iteracions. Quan `n` val `0`, `n > 0` és `False` i el bucle
    s'atura sense tornar a executar el cos.

* `while True:` és una condició sempre certa: crea un bucle infinit **a propòsit**. Per sortir-ne cal un
  `break` dins el cos:

```python
comptador = 0
while True:
    comptador += 1
    if comptador == 2:
        break
print(comptador)   # 2
```

* `break` talla el bucle immediatament (surt sense reavaluar la condició); no executa la resta del cos
  d'aquella volta.

### Exemples addicionals

* Cas normal — construir un string lletra a lletra amb un `while` (en comptes de comptar cap avall):

```python
paraula = ""
lletres = ["p", "y", "t", "h", "o", "n"]
i = 0
while i < len(lletres):
    paraula += lletres[i]
    i += 1
print(paraula)   # python
```

* Cas límit — la condició ja és falsa la primera vegada: el cos no s'executa **cap** volta.

```python
x = 5
while x < 5:
    print(x)
    x += 1
print("fi")
# Output: fi     (el while no imprimeix res, x ja val 5 des del principi)
```

* Error típic — actualitzar la variable en la direcció equivocada: la condició mai arriba a ser
  falsa perquè `n` s'allunya del límit en comptes d'apropar-s'hi.

```python
n = 0
while n < 3:
    print(n)
    n -= 1
# BUCLE INFINIT: n hauria d'incrementar-se (n += 1) per arribar a 3;
# en canvi disminueix (0, -1, -2, -3, ...) i mai deixa de ser menor que 3
```

* `while True` + `break` amb una condició diferent (buscar un valor concret comptant cap amunt):

```python
codi_secret = 7
intent = 0
while True:
    intent += 1
    if intent == codi_secret:
        print("Trobat a l'intent", intent)
        break
# Output: Trobat a l'intent 7
```

---

## Sessió S12 — while II: comptadors i acumuladors dins d'un while (30/11/2026)

* Un **comptador** és una variable que compta iteracions (normalment sumant o restant 1 cada volta):
  `i = i + 1` (equivalent a `i += 1`).
* Un **acumulador** és una variable que va acumulant un resultat (suma, producte, concatenació de
  text...) al llarg de les iteracions. Cal **inicialitzar-la abans del bucle** amb el valor neutre
  (`0` per sumes, `1` per productes, `""` per text).

```python
total = 0        # acumulador (valor neutre de la suma: 0)
i = 1             # comptador
while i <= 5:
    total += i    # total = total + i
    i += 1
print(total)      # 15  (1+2+3+4+5)
print(i)          # 6   (el valor amb què la condició es fa False)
```

* Error molt habitual: oblidar `i += 1` → bucle infinit (`i` mai arriba a `6`).
* Error molt habitual: inicialitzar `total = 0` **dins** del bucle → `total` es reinicia cada volta i
  el resultat final és incorrecte.
* Els operadors d'assignació combinada (`+=`, `-=`, `*=`, `/=`) són els que més s'utilitzen dins de
  comptadors/acumuladors. `x += 1` és exactament `x = x + 1`.

```python
producte = 1
n = 1
while n <= 4:
    producte *= n
    n += 1
print(producte)   # 24  (1*1*2*3*4)
```

### Exemples addicionals

* Cas normal — comptador condicional (només compta els valors que compleixen una condició, no tots):

```python
n = 1
parells = 0
while n <= 10:
    if n % 2 == 0:
        parells += 1
    n += 1
print(parells)   # 5   (2, 4, 6, 8, 10)
```

* Cas límit — la condició ja és falsa des del principi: l'acumulador queda exactament amb el valor
  d'inicialització, sense cap volta.

```python
total = 0
i = 10
while i <= 5:
    total += i
    i += 1
print(total)   # 0   (el bucle no s'executa mai)
```

* Error típic, ara amb codi complet (l'acumulador es reinicialitza a dins del bucle): a cada volta
  es perd el que s'havia acumulat fins llavors, i al final només queda l'últim valor sumat.

```python
total = 0
i = 1
while i <= 4:
    total = 0        # ERROR: hauria d'estar ABANS del while, no aquí dins
    total += i
    i += 1
print(total)   # 4   (no 10; a cada volta s'esborra l'acumulat i només queda l'últim "i")
```

---

## Sessió S13 — while III: validacions d'entrada i problemes típics (07/12/2026)

* Patró de **validació d'entrada**: repetir la petició de dades fins que l'usuari introdueixi un valor
  vàlid.

```python
edat = int(input("Edat: "))
while edat < 0:
    print("Edat no vàlida")
    edat = int(input("Edat: "))
print("Edat acceptada:", edat)
```

  * Aquí la condició (`edat < 0`) és la condició per **seguir demanant**; el bucle acaba quan deixa de
    complir-se, és a dir, quan la dada ja és vàlida.

* `continue` salta directament a la reavaluació de la condició, sense executar la resta del cos
  d'aquella volta (a diferència de `break`, que surt del bucle del tot).

```python
i = 0
while i < 5:
    i += 1
    if i == 3:
        continue
    print(i)
# Output: 1 2 4 5   (el 3 no s'imprimeix, però el bucle continua)
```

* Problema típic **off-by-one**: comparar amb `<` quan tocava `<=` (o a l'inrevés), fent que el bucle
  s'executi una volta de més o de menys del que es volia.
* Problema típic de **bucle infinit**: la variable de control no es modifica mai dins el cos, o es
  modifica només dins d'un `if` que no sempre s'executa.

```python
i = 0
while i < 3:
    print(i)
    if i == 5:      # mai és cert (i mai arriba a 5)
        i += 1
# BUCLE INFINIT: i sempre val 0
```

* `while` amb condicions compostes (`and`/`or`) també és habitual: `while intents < 3 and not trobat:`.

### Exemples addicionals

* Validació amb un rang de valors (combina `or` amb la comparació, en comptes d'un simple `< 0`):

```python
opcio = int(input("Tria 1, 2 o 3: "))
while opcio < 1 or opcio > 3:
    print("Opció no vàlida")
    opcio = int(input("Tria 1, 2 o 3: "))
print("Has triat:", opcio)
```

* `continue` saltant-se diversos valors seguits (no només un):

```python
i = 0
while i < 6:
    i += 1
    if i % 2 == 0:
        continue
    print(i)
# Output: 1 3 5   (tots els parells es salten, no només un)
```

* Off-by-one amb codi concret (abans només s'explicava en text): la intenció era imprimir del `1` al
  `5`, però la condició `<` en comptes de `<=` deixa fora l'últim valor.

```python
i = 1
while i < 5:
    print(i)
    i += 1
# Output: 1 2 3 4   (falta el 5; calia "while i <= 5" per incloure'l)
```

* Condició composta amb `and` i `not` treballant plegades:

```python
intents = 0
trobat = False
while intents < 3 and not trobat:
    intents += 1
    if intents == 2:
        trobat = True
print(intents, trobat)   # 2 True
# El bucle s'atura perquè "trobat" ja és True (encara que "intents < 3" seguís sent cert)
```
