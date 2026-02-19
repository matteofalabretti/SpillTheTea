## CONTRIBUTING.md - Guida alle convenzioni e good practices per SpillTheTea

Questa guida definisce le regole coerenti per contribuire al progetto SpillTheTea, un'applicazione web per condividere esperienze di appuntamenti con focus su red flags. L'obiettivo è mantenere il codice pulito, leggibile, testabile e scalabile, rispettando le best practices per un team universitario che simula una startup.

La guida è divisa in sezioni: convenzioni Git (inclusi "flags" come prefissi per branch e commit), naming conventions per il codice Java, good practices generali e regole per la documentazione.

Seguire queste regole è obbligatorio per tutte le PR. In caso di dubbi, discuti nel gruppo Discord o apri una issue con label "docs".

### 1. Convenzioni Git (branch, commit, push)

#### Flags / Prefissi per branch e commit
Usiamo "flags" (prefissi) per categorizzare branch e commit. Questo rende il repository organizzato e facile da navigare.

- **Prefissi per branch** (tipo/breve-descrizione-minuscola-con-trattini):
  - `feature/` : Nuova funzionalità (es. `feature/registrazione-utente`)
  - `fix/` : Correzione bug (es. `fix/login-sessione-non-funziona`)
  - `refactor/` : Miglioramento codice senza cambiare funzionalità (es. `refactor/base-dao-ottimizzazione`)
  - `test/` : Aggiunta/modifica test (es. `test/integration-post-dao`)
  - `docs/` : Documentazione (es. `docs/aggiornamento-readme`)
  - `chore/` : Manutenzione (es. `chore/pom-dipendenze-update`)
  - `perf/` : Miglioramento performance (es. `perf/feed-query-indici`)

- **Regole per branch**:
  - Sempre partire da `main` o `develop`: `git checkout main && git pull`
  - Crea branch: `git checkout -b feature/nome-descrizione`
  - Descrizione breve (max 50 char), minuscola, trattini invece di spazi
  - Linka all'issue: `git checkout -b feature/#12-registrazione-utente`

- **Prefissi per commit message** (tipo(scope): descrizione imperativo presente):
  - `feat` : Nuova feature (es. `feat(auth): aggiunta registrazione utente`)
  - `fix` : Bug fix (es. `fix(feed): corretto ordinamento post`)
  - `refactor` : Refactoring (es. `refactor(dao): ottimizzata query findById`)
  - `test` : Test (es. `test(post): aggiunti test integrazione`)
  - `docs` : Docs (es. `docs: aggiornato schema database`)
  - `chore` : Manutenzione (es. `chore: aggiornato dipendenze pom.xml`)
  - `perf` : Performance (es. `perf(db): aggiunto indice su creato_il`)
  - `style` : Formattazione (es. `style(jsp): uniformata indentazione`)

- **Regole per commit**:
  - Commit frequenti e atomici (un cambiamento per commit)
  - Titolo max 72 char, corpo opzionale dopo riga vuota (spiega "perché")
  - Usa imperativo: "aggiunge" non "aggiunto"
  - Scope opzionale tra parentesi: `(auth)`, `(post)`, `(dao)`
  - Riferisci all'issue: "Closes #12"

- **Regole per push**:
  - Pusha spesso sul tuo branch: `git push origin feature/nome-branch`
  - Mai pushare direttamente su `main` – solo tramite PR approvata
  - Prima di push: `git pull --rebase origin main` per aggiornare

#### Esempio flusso completo
1. `git checkout main && git pull`
2. `git checkout -b feature/#15-feed-personalizzato`
3. Lavora → `git add .` → `git commit -m "feat(feed): aggiunta query post seguiti"`
4. `git push origin feature/#15-feed-personalizzato`
5. Apri PR su GitHub

### 2. Naming conventions per il codice Java

Seguiamo le convenzioni standard Java (Oracle) con alcuni adattamenti per il nostro stack (Servlet + JSP + JDBC).

- **Classi**:
  - UpperCamelCase
  - Nomi descrittivi: `UtenteDAO`, `PostServiceImpl`, `LoginServlet`
  - Per interfacce: `UtenteDAO` (no IUtenteDAO)
  - Impl: `UtenteDAOImpl`

- **Metodi**:
  - lowerCamelCase
  - Verbi imperativi: `findById`, `insertUtente`, `toggleLike`
  - Getter/Setter: `getUsername`, `setPasswordHash`

- **Variabili / Campi**:
  - lowerCamelCase
  - Costanti: UPPER_SNAKE_CASE (es. `MAX_PASSWORD_LENGTH = 8`)
  - Variabili locali brevi: `conn`, `rs`, `ps`

- **Package**:
  - Tutto minuscolo, trattini no
  - Struttura: `com.spillthetea.persistence.connection`, `com.spillthetea.dao`, `com.spillthetea.model`, `com.spillthetea.service`, `com.spillthetea.web.servlet`
  - Evita package profondi >3 livelli

- **JSP / HTML / CSS**:
  - JSP: lower-kebab-case.jsp (es. `post-create.jsp`, `profile.jsp`)
  - ID/class CSS: lower-kebab-case (es. `post-card`, `like-button`)
  - Evita inline style → usa css esterni

- **SQL**:
  - Tabella: singular minuscolo (es. `utente`, `post`)
  - Colonne: snake_case (es. `utente_id`, `creato_il`)

- **Eccezioni**:
  - End with Exception: `DataAccessException`, `BusinessException`

### 3. Good practices generali

#### Codice e struttura
- **Layering**: model (POJO) → dao (accesso DB) → service (logica business) → servlet (controller) → jsp (view)
- **Dependency Injection manuale**: passa dipendenze nei costruttori (es. DAO al Service, ConnectionProvider al DAO)
- **Error handling**: usa eccezioni custom (DataAccessException per DB, BusinessException per logica), logga errori con System.err o SLF4J se aggiunto
- **Validazione**: client-side (JS) + server-side sempre (no trust input utente)
- **Sicurezza**: hash password, escape output in JSP (c:out), CSRF token in form POST
- **Formattazione**: usa Eclipse/IntelliJ formatter (indent 4 spazi, no tab, line max 120 char)
- **Javadoc**: solo su metodi pubblici / classi principali – breve e utile
- **Evita**: codice duplicato → usa helper/util
- **Versioni**: Java 21, Servlet 6.0+, JSP 3.1+

#### Test
- Scrivi test per ogni feature nuova (JUnit 5)
- Tipi: unit (DAO, Service), integrazione (con DB in-memory)
- Copertura minima: 70% per DAO/Service
- Usa @BeforeEach per setup DB test

#### PR e review
- Ogni branch → PR con descrizione + acceptance criteria
- Almeno 1 approvazione prima del merge
- Squash commit se branch ha molti commit sporchi

#### Documentazione
- Aggiorna README per ogni milestone (aggiungi sezioni "Come usare" dopo ogni feature)
- Usa docs/ per file md: architettura.md, schema-db.md, endpoints.md
- Commenti codice: solo dove non ovvio (spiega "perché", non "cosa")

#### Altre regole
- **Dipendenze**: aggiungi solo se necessari (no over-engineering)
- **Deploy locale**: sempre testabile con mvn tomcat:run
- **Ambiente test/prod**: usa DatabaseConfig.testMode per switch
- **Codice morto**: rimuovilo subito
- **Aggiornamenti**: pull main giornaliero

Se non segui una regola, spiega nella PR il perché (es. "eccezione per urgenza").

Grazie per contribuire a SpillTheTea! 🚀