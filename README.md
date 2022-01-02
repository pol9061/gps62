## Explicació CI

Continuous Integration (CI) és una metodologia de desenvolupament que millora la qualitat tant del procés de desenvolupament d’un software com del producte final en què resulta. Més concretament, les practiques que comprenen la metodologia es basen en l’automatització de processos de control de qualitat. Sovint, aquests processos es manifesten en forma de tests automatitzats que s'executen abans de fer efectiva una contribució a una versió existent d'un software. La responsabilitat d'automatitzar aquests processos recau sobre el programari de control de versió (ja sigui GitLab, GitHub, etc.), pel que es minimitza la quantitat de temps invertida per part de l’equip desenvolupador en aquestes tasques. Tanmateix, a aquest, li és possible definir exactament els detalls del fluxe d’execució d’aquests processos per mitjà de fitxers com el que es mostra a continuació:

<img width="1219" alt="Captura de pantalla 2022-01-02 a las 14 22 37" src="https://user-images.githubusercontent.com/28115415/147877182-637c670b-f4e3-45ad-9988-3ebad7531b80.png">

## python-app.yml

Aquest fitxer permet definir la freqüència amb la que s’ha d’executar un conjunt de tests que permeten l’aplicació de la metodologia d’integració continua en un projecte que gestiona el control de versions via GitHub.

La paraula clau ``jobs`` marca l’inici de la llista de processos que s’haurà d’executar per fer possible la integració contínua.

La paraula clau ``build`` defineix les característiques (``runs-on``, ``strategy``, etc.) del sistema sobre el qual es du a terme la contribució al control de versions. 

Finalment, es llista del conjunt de processos que s’executaran. En destaquen els següents:

### Install Dependencies

Aquest job permet que la integració continua sigui independent del entorn de desenvolupament local, i ho fa executant els processos en un entorn virtual. Per tal d’especificar quines dependències necessita aquest entorn virtual, definim les ``install dependencies``. En aquest cas, els requisits es manifesten com a un conjunt de llibreries del llenguatge de programació Python. 

### Lint with flake8

Aquest job s’encarrega d’analitzar el codi de la versió a nivell sintàctic. Permet detectar des de errors de compilació fins a potencials errors d’execució passant per patrons de programació associats a pràctiques obscures o si més no millorables. 

### Tests

Aquest job s’encarrega de l’execució, via la llibreria de Python ``pytest``, del conjunt de tests definits al fitxer especificat, en aquest cas, ``test.py``. Aquest fitxer pot contenir tests unitaris, tests d’integració i fins i tot de sistema. La seva execució mostrarà el resultat dels tests i evitarà la formalització de la contribució en cas de fallada d’un test.

### Test coverage

El concepte de test coverage és una mètrica que mesura la proporció d’un software que s’executa durant l’execució dels tests definits. Per exemple, si tenim definits tests per totes les funcionalitats del sistema, és probable que el test coverage sigui proper a 100%, mentre que si tenim tests definits per la meitat de funcionalitats del sistema, és probable que el coverage sigui proper al 50%. En el cas del fitxer descrit, el test coverage s’obté per mitjà de la llibreria python ``coverage``.
 
