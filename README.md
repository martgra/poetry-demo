# **Noen grunner til å bruke Poetry**

## **Grunn 1: Kontroll over avhengigheter 🕸️**
* Spesifiser avhengigheter i ```pyproject.toml``` via CLI eller teksteditor
* ```poetry.lock``` produseres av poetry når alle dependencies er resolved. _Bør sjekkes inn i versjonskontroll!_ 
## **Grunn 2: Enklere bygging 🛠️**
* Glem kompliserte setup.py - ```pyproject.toml``` bygger prosjektet for deg!
* Poetry kan også publisere pakker til private speil eller pypi.org
## **Grunn 3: One file to rule them all! 🧙‍♂️**
* Samle all config, avhengigheter og annet snacks i en fil



## **Noen tips&tricks**
* ```pyproject.toml``` kan redigeres gjennom text editor - husk å kjøre ```poetry update``` etterpå
* Dependencies kan spesifiseres med følgende [operatorer](https://python-poetry.org/docs/dependency-specification/#version-constraints)
* Dependencies kan legges til fra [git](https://python-poetry.org/docs/dependency-specification/#git-dependencies), [filstier](https://python-poetry.org/docs/dependency-specification/#git-dependencies) eller [url](https://python-poetry.org/docs/dependency-specification/#url-dependencies)
* pip støttes fortsatt (kan fint kjøre ```pip install .```)
* Legg til skript som kan kjøres fra [kommandolinjen](https://python-poetry.org/docs/pyproject/#scripts)
* Legg til config for verktøy som black, pylint etc i ```pyproject.toml``` . 
* Bruk poetry til å holde styr på [virtuelle miljøer ](python-poetry.org/docs/managing-environments/)
    * Spwan shell med ```poetry shell```
* [Monorepo template](https://github.com/martgra/monorepo) kan kreve litt hack - her er et eksempel
* Ved rare feil - begynn med å slette ```poetry.lock```
* Finnes ikke poetry i path? Ikke fortvil - sørg for at ```~/.local/bin``` ligger i ```$PATH```

# **Kom igang på 1-2-3 🚀**

**Installer poetry**
```bash
curl -sSL https://install.python-poetry.org | python3 -
```

### **Opprett nytt prosjekt!**  

Opprett prosjekt med filstruktur på gitt path.
```bash
poetry new --name my_library .
```
...eller initierer poetry i et eksisterende prosjekt gjennom en interaktiv prompt.
```bash
poetry init
```
Installer prosjektet - avhengigheter installeres i eksisterende eller nytt venv.
```bash
poetry install
```
### **Avhengigheter**
Legg til avhengigheter via CLI eller editere pyproject.toml
```bash
poetry add requests@^2.27
poetry add git+https://github.com/pallets/flask.git@main
```
Dev avhengigheter kan spesifiseres. Prosjektet kan installeres med/uten dev avhengigheter.
```bash
poetry add --dev black pylint flake8 pydocstyle isort pytest-cov pytest pre-commit
```
Oppdater avhengigheter basert på constraints i ```pyproject.toml```
```bash
poetry update
```
Utforsk avhengigheter. 
```bash
poetry show -t
```
Fjern avhengigheter - kan også gjøres direkte i ```pyproject.toml```
```bash
poetry remove flask
```
Bygg prosjektet - produserer både sdist og wheel.
```bash
poetry build
```
### **Poetry venv**
Kjør kommandoer i venv poetry bruker/har opprettet for oss.
```bash
poetry run play
```
Aktiverer det venv poetry bruker
```bash
poetry shell
```
Slett env og opprett nytt
```bash
exit
poetry env remove 3.9
poetry env use 3.9
```
Deaktiver poetry venv
```bash 
exit
```