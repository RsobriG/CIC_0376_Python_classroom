# Configuració de VSCode per treballar amb Python

Aquesta guia s'ha de seguir **abans de la sessió 1** (o durant-la) perquè tot l'alumnat tingui un
entorn que executi codi Python sense errors de configuració. Segueix els passos en ordre; no saltis
cap pas encara que creguis que ja ho tens instal·lat.

## 1. Instal·lar Python

### Windows

1. Ves a https://www.python.org/downloads/ i descarrega l'última versió estable de Python 3 (3.11 o superior).
2. Executa l'instal·lador. **Molt important**: marca la casella **"Add python.exe to PATH"** a la primera pantalla de l'instal·lador. Si no la marques, Windows no trobarà la comanda `python` des de la terminal i hauràs de reinstal·lar.
3. Un cop instal·lat, obre una terminal (PowerShell o CMD) i comprova la instal·lació:
   ```
   python --version
   ```
   Ha de mostrar alguna cosa com `Python 3.12.4`.

### Linux (Debian/Ubuntu i derivats)

Python 3 sol venir ja instal·lat. Comprova'n la versió i instal·la `pip` i `venv` si falten:

```bash
python3 --version
sudo apt update
sudo apt install python3-pip python3-venv
```

### macOS

Instal·la Python 3 amb [Homebrew](https://brew.sh/):

```bash
brew install python
python3 --version
```

## 2. Instal·lar VSCode

Descarrega'l de https://code.visualstudio.com/ i instal·la'l amb les opcions per defecte.

## 3. Instal·lar l'extensió de Python

1. Obre VSCode.
2. Clica la icona d'extensions a la barra lateral esquerra (icona de quadrats, o `Ctrl+Shift+X`).
3. Cerca **"Python"** (l'extensió oficial de Microsoft, autor "Microsoft", icona blava/groga).
4. Clica **Install**.
5. Instal·la també l'extensió **"Pylance"** (normalment s'instal·la automàticament amb la de Python) — dona autocompletat i detecció d'errors en temps real.

## 4. Obrir la carpeta de treball correcta

**Regla d'or: sempre obre a VSCode la CARPETA del projecte/activitat (`File > Open Folder...`), mai un fitxer solt.** Si obres només el fitxer `.py`, el depurador i les rutes relatives no funcionaran bé.

## 5. Seleccionar l'intèrpret de Python (la causa #1 d'errors de configuració)

Quan VSCode "no troba Python" o executa una versió diferent de la que t'esperes, gairebé sempre és
perquè **té seleccionat l'intèrpret equivocat**. Per comprovar-ho i arreglar-ho:

1. Prem `Ctrl+Shift+P` (Windows/Linux) o `Cmd+Shift+P` (macOS) per obrir la paleta de comandes.
2. Escriu **"Python: Select Interpreter"** i prem Enter.
3. Tria l'intèrpret de Python 3 que vas instal·lar al pas 1 (ha d'aparèixer amb la seva versió, p. ex. `Python 3.12.4 ('venv': venv)` o `Python 3.12.4 64-bit`).
4. A la barra inferior de VSCode (a la dreta) ha d'aparèixer ara el número de versió de Python seleccionat. Si hi posa "Select Interpreter" en vermell/groc, encara no n'has triat cap.

## 6. Crear un entorn virtual (venv) — recomanat des de la primera activitat

Un entorn virtual aïlla les llibreries de cada projecte perquè no interfereixin entre activitats.

1. Obre un terminal dins VSCode: `Terminal > New Terminal` (o ``Ctrl+ ` ``).
2. Crea l'entorn:
   ```bash
   # Windows
   python -m venv venv

   # Linux / macOS
   python3 -m venv venv
   ```
3. Activa'l:
   ```bash
   # Windows (PowerShell)
   .\venv\Scripts\Activate.ps1

   # Windows (CMD)
   venv\Scripts\activate.bat

   # Linux / macOS
   source venv/bin/activate
   ```
   Quan estigui actiu, veuràs `(venv)` al davant de la línia del terminal.
4. Torna a fer **"Python: Select Interpreter"** (pas 5) i tria ara l'intèrpret que diu `('venv': venv)` — ha d'apuntar dins la carpeta `venv` del teu projecte.

**Si `Activate.ps1` dona un error de "no se puede cargar... scripts está deshabilitada" a Windows:**
Obre PowerShell com a administrador i executa una única vegada:
```powershell
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
```
Torna a intentar activar l'entorn.

## 7. Executar un fitxer Python

Amb un fitxer `.py` obert:

* Botó **▶ (Run Python File)** a la cantonada superior dreta, **o**
* `Ctrl+F5` (executar sense depurador), **o**
* Des del terminal: `python nom_fitxer.py` (Windows) / `python3 nom_fitxer.py` (Linux/macOS).

Si tot està ben configurat, hauries de veure el resultat directament al panell "TERMINAL" de la part inferior.

## 8. Comprovació final (fes-ho abans de la Sessió 1)

Crea un fitxer `prova.py` amb aquest contingut:

```python
print("Configuració correcta")
```

Executa'l (`Ctrl+F5`). Si al terminal apareix exactament `Configuració correcta` sense cap error,
la configuració és correcta i pots continuar amb el curs.

## 9. Errors habituals i com solucionar-los

| Símptoma | Causa més probable | Solució |
| :---- | :---- | :---- |
| `'python' no se reconoce como un comando...` (Windows) | Python no es va afegir al PATH durant la instal·lació | Reinstal·la Python marcant "Add python.exe to PATH", o afegeix-lo manualment al PATH del sistema |
| VSCode diu "No interpreter selected" o executa una versió antiga | No s'ha seleccionat l'intèrpret correcte | Repeteix el pas 5 ("Python: Select Interpreter") |
| `ModuleNotFoundError: No module named 'X'` | El paquet no està instal·lat a l'entorn actiu, o tens l'entorn virtual equivocat seleccionat | Activa el venv correcte i fes `pip install X`; comprova amb "Python: Select Interpreter" que apunta al venv |
| El botó ▶ executa el fitxer però no veus cap `print()` | Estàs mirant una consola equivocada (Debug Console en comptes de Terminal) | Mira sempre el panell **TERMINAL**, no el "DEBUG CONSOLE", quan executes amb `Ctrl+F5` |
| `Activate.ps1... no se puede cargar` (Windows) | Política d'execució de PowerShell restrictiva | Executa `Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser` (veure pas 6) |
| El codi sembla no actualitzar-se quan l'executes | Tens desat un altre fitxer amb el mateix nom en una altra carpeta, o no has desat (`Ctrl+S`) els canvis | Desa sempre abans d'executar; comprova la ruta del fitxer a la pestanya de dalt |

A partir d'aquí, per aprendre a **aturar l'execució i inspeccionar variables pas a pas**, consulta
`00_GUIES/Com_Debugar_amb_VSCode.md` — és una eina que farem servir a **totes** les activitats del curs.
