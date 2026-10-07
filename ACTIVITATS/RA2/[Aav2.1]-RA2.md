# Activitat 2.1 — Decisions amb if / elif / else

## Fitxa de l'activitat

| | |
| :--- | :--- |
| **Mòdul** | 0376. Implementació d'aplicacions web |
| **Resultat d'aprenentatge** | RA2. Aplica estructures condicionals i treballa amb cadenes de text (strings). |
| **Tipus** | Activitat d'aprenentatge  |
| **Avaluació** | **Apte/No Apte** |
| **Modalitat** | Individual |

## Objectiu

Practicar l'escriptura i la lectura d'estructures condicionals amb operadors de comparació i lògics.

## Activitat 1: Enunciat

1. Escriu un programa que demani l'edat d'una persona (`input()`, convertit a `int`) i imprimeixi:
   - `"Menor d'edat"` si té menys de 18 anys.
   - `"Adult"` si té entre 18 i 64 anys (ambdós inclosos).
   - `"Jubilat"` si té 65 anys o més.

2. Escriu un programa amb dues variables `te_entrada = True` i `te_reserva = False` que imprimeixi `"Pot passar"` si té entrada **o** reserva, i `"No pot passar"` en cas contrari. Fes-ho amb un sol `if`/`else` fent servir `or`.

3. Donada la variable `nota = 7.5`, escriu un `if`/`elif`/`else` que imprimeixi la qualificació textual: `"Excel·lent"` (≥9), `"Notable"` (≥7), `"Aprovat"` (≥5), `"Suspès"` (<5). Comprova que amb `nota = 7.5` s'imprimeix `"Notable"` i raona per escrit (1 línia) per què no s'arriba a comprovar la condició de `"Aprovat"`.

4. Sense executar-ho, escriu en un comentari quin creus que serà l'output d'aquest fragment, i després executa'l per comprovar-ho:
   ```python
   a = 10
   b = "10"
   print(a == b)
   print(a == int(b))
   print(a != b and a == int(b))
   ```

## Activitat 2: Depuració amb VSCode

El següent codi hauria de classificar una nota (variable `nota = 5`) i sempre hauria d'imprimir `"Aprovat"` per a aquest valor, però imprimeix `"Suspès"`:

```python
nota = 5
if nota > 5:
    print("Aprovat")
else:
    print("Suspès")
```

1. Obre el fitxer a VSCode i posa-hi un breakpoint a la línia del `if`.
2. Executa el depurador (F5) i mira, a la finestra de variables, el valor de `nota`.
3. Fes "step over" línia a línia i identifica per què el programa entra a la branca `else` tot i que `nota` és 5, que hauria de comptar com a aprovat.
4. Corregeix el bug i escriu 2-3 línies explicant la causa (pista: mira bé l'operador de comparació).

## Com entregar-ho

**Enllaç del teu repositori al moodle**. En aquest repositori ha d'haver-hi el/s fitxer/s `.py` amb els 4 exercicis resolts i comentats, més una captura de pantalla del depurador de VSCode aturat al breakpoint amb la finestra de variables visible.
