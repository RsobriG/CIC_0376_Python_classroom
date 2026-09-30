# Activitat 7.4 — Simulacre parcial cronometrat (repàs de tot el curs)

## Objectiu

Practicar les condicions reals de l'examen PCEP (PE1): preguntes tipus test d'opció única, temps limitat, i contingut que barreja tots els blocs del curs (fonaments, condicionals, bucles, llistes, tuples/diccionaris, funcions, errors).

## Avaluació

Aquesta activitat s'avalua amb APTE / NO APTE (APTE = 10 o més respostes correctes sobre 15).

## Enunciat

Temps: **25 minuts**. Sense llibres, apunts ni ordinador (excepte per llegir l'enunciat). Resposta única per pregunta.

**1.** Quin és l'output d'aquest codi?

    x = 5
    y = "5"
    print(x == y, x == int(y))

    A) True True
    B) False True
    C) False False
    D) True False

**Resposta:____**

**2.** Quantes vegades s'executa el bucle?

    for i in range(2, 10, 3):
        print(i)

    A) 2
    B) 3
    C) 4
    D) 8

**Resposta:____**

**3.** Quin és el valor final de `total`?

    total = 0
    for n in [1, 2, 3, 4]:
        if n % 2 == 0:
            continue
        total += n

    A) 10
    B) 4
    C) 6
    D) 0

**Resposta:____**

**4.** Què imprimeix aquest codi?

    d = {"a": 1, "b": 2}
    print(d.get("c", 0))

    A) `KeyError`
    B) `None`
    C) `0`
    D) `c`

**Resposta:____**

**5.** Quin és el resultat de `llista[1:3]` si `llista = [10, 20, 30, 40, 50]`?

    A) `[20, 30]`
    B) `[20, 30, 40]`
    C) `[10, 20, 30]`
    D) `[30, 40]`

**Resposta:____**

**6.** Quina diferència hi ha entre una llista i una tupla?

    A) Cap, són sinònims
    B) La llista és mutable i la tupla no
    C) La tupla només pot contenir números
    D) La llista no admet índexs negatius

**Resposta:____**

**7.** Quin és l'output?

    def suma(a, b=10):
        return a + b

    print(suma(5))
    print(suma(5, 1))

    A) 15 i 6, en aquest ordre (en línies separades)
    B) 15 i 15
    C) 6 i 15
    D) Error: falta l'argument `b` a la segona crida

**Resposta:____**

**8.** Quina excepció es llança en aquest codi?

    valors = [1, 2, 3]
    print(valors[5])

    A) `ValueError`
    B) `KeyError`
    C) `IndexError`
    D) `TypeError`

**Resposta:____**

**9.** Què imprimeix?

    s = "Python"
    print(s[-1], s[0:2])

    A) `n Py`
    B) `P yt`
    C) `n Pyt`
    D) `P Py`

**Resposta:____**

**10.** Quin és el resultat final de `x`?

    x = 1
    while x < 20:
        x *= 2
    print(x)

    A) 16
    B) 20
    C) 32
    D) 18

**Resposta:____**

**11.** Què fa el mètode `.append()` sobre una llista?

    A) Retorna una nova llista amb l'element afegit, sense modificar l'original
    B) Modifica la llista original afegint l'element al final, i retorna `None`
    C) Afegeix l'element a l'inici de la llista
    D) Només funciona amb números

**Resposta:____**

**12.** Quin és l'output?

    try:
        x = int("abc")
    except ValueError:
        print("A")
    except TypeError:
        print("B")
    finally:
        print("C")

    A) A
    B) A i després C
    C) B i després C
    D) C únicament

**Resposta:____**

**13.** Quin és el valor de `resultat`?

    a = True
    b = False
    resultat = a and not b

    A) True
    B) False
    C) `None`
    D) Error de sintaxi

**Resposta:____**

**14.** Quantes claus té el diccionari després d'executar aquest codi?

    d = {"x": 1, "y": 2}
    d["x"] = 100
    d["z"] = 3

    A) 1
    B) 2
    C) 3
    D) 4

**Resposta:____**

**15.** Quina és la principal diferència pràctica entre `f.read()` i `f.readlines()` sobre un objecte fitxer?

    A) `read()` retorna un `str` amb tot el contingut, `readlines()` retorna una `list` de línies
    B) Són exactament equivalents
    C) `readlines()` només llegeix la primera línia
    D) `read()` només funciona en mode escriptura

**Resposta:____**

## Depuració amb VSCode

Trieu, en parella, un dels programes que heu fet a qualsevol activitat anterior del curs (`Aav1.x` a `Aav7.x`) que recordeu que us va costar de fer funcionar. Torneu-lo a obrir a VSCode, poseu-hi almenys dos breakpoints en punts diferents del programa, executeu-lo amb F5 i expliqueu per escrit (3-4 línies) quina informació nova us dona ara el depurador que no vau fer servir la primera vegada (per exemple: el panell de variables, la pila de crides o el "watch").

## Com entregar-ho

Les respostes de les 15 preguntes (`Resposta:____`) i el text de l'explicació de l'apartat de depuració, en un sol document.
