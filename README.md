# SpillTheTea

SpillTheTea è una piattaforma online dove le persone possono condividere in modo anonimo o semi-anonimo le proprie esperienze di appuntamenti, relazioni e situazioni sociali, mettendo in evidenza **red flags**, momenti imbarazzanti, comportamenti tossici o semplicemente aneddoti memorabili.

L'obiettivo è creare una community che aiuti gli utenti a riconoscere segnali di pericolo, a ridere insieme delle disavventure e a sentirsi meno soli nelle proprie esperienze.

**Live demo** (quando sarà deployata): https://spillthetea.example.com  
**Tipo di applicazione**: Web platform tradizionale (server-side rendering)

## Caratteristiche principali (MVP – 2 mesi)

- Registrazione / Login / Recupero password
- Pubblicazione di post (testo + tag red-flag predefiniti)
- Feed principale (post degli utenti seguiti + trending)
- Like, commenti, repost / quote
- Profilo utente (bio, avatar, lista post)
- Follow / Unfollow
- Ricerca per tag / keyword
- Blocco utente
- Responsive design (mobile-friendly)

**Funzionalità future** (post-MVP):
- Messaggistica privata
- Notifiche
- Moderazione comunitaria / segnalazioni
- Dark mode
- Possibilità di anonimato avanzato

## Tecnologie utilizzate

- **Backend**: Java 21 + Servlet + JSP
- **Database**: SQLite (sviluppo) → PostgreSQL / MySQL (produzione)
- **Frontend**: JSP + Bootstrap 5 + vanilla JS (no framework JS pesante)
- **Build & Dipendenze**: Maven
- **Server**: Apache Tomcat 10
- **Testing**: JUnit 5 + Mockito
- **Deployment**: Heroku / Render / VPS economico (futuro)

## Come avviare localmente

1. Clona il repository
   ```bash
   git clone https://github.com/your-username/SpillTheTea.git
   cd spillthetea
   ```

2. Compila e installa dipendenze
    ```Bash
    mvn clean install
    ```
3. Avvia Tomcat embedded (o deploya il .war su Tomcat locale)
    ```Bash
    mvn tomcat7:run
    ```
3. Apri nel browser:
   ```
   http://localhost:8080/spillthetea
   ```

## Struttura del progetto (principali package)
 ```text
src/main/java/com.spillthetea
├── config
├── persistence (connection, exception)
├── model
├── dao
├── service
└── web
    ├── servlet
    └── filters

src/main/webapp
├── WEB-INF
│   └── web.xml
├── css
├── js
└── views (jsp)
    ├── layout
    └── pages
```
## Contribuire

1. Fork → Branch (feature/nome-funzione)
2. Commit chiari e atomici
3. Pull Request con descrizione + screenshot se modifica UI
4. Almeno un reviewer prima del merge

## Licenza

MIT License

Progetto nato come esercizio universitario con ambizione di diventare una piattaforma reale.

© 2026 SpillTheTea Team
