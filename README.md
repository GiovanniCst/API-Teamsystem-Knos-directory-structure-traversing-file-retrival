# API Python con Flask per recupero file tramite ID pubblicazione e numero versione compatibile con struttura cartelle/file del DMS Knos™ di Teamsystem™.  

API Python con Flask per recupero file tramite ID pubblicazione e numero versione compatibile con struttura cartelle/file del DMS Knos™ di Teamsystem™.  

Python API with Flask for file retrieval using publication ID and version number. Compatible with the file/directory structure of the Knos™ DMS by Teamsystem™

## Backstory
In azienda avevamo bisogno di consegnare a Salesforce™ documenti (gran parte in formato PDF) prodotti sul gestionale Alyante™ di Teamsystem™ che abbiamo in uso e che vengono pubblicati tramite il sistema DMS, sempre Teamsystem™, chiamato Knos™.  
Avendo difficoltá a far funzionare in tempo utile l'API ufficiale fornita da Teamsystem™, ho sviluppato uno script Python che produce il risultato di cui avevamo bisogno, ovvero consente al middleware di scambio dati con Salesforce™ di recuperare i PDF dei documenti con tecnologia API standard tramite traversing del filesystem del DMS. Lo script quindi non si interfaccia direttamente con il DMS, ma ottenuto l'ID della pubblicazione e la versione del file, lo rintraccia all'interno del filesystem.

Tutti i marchi menzionati sono di proprietá dei rispettivi titolari.

In the company recently we needed to deliver documents (mostly in PDF format) produced on the Alyante™ ERP system by Teamsystem™ which are published through the DMS system, also by Teamsystem™, called Knos™ to the middleware which interacts with our Salesforce™ org.  
Having difficulty getting the official API provided by Teamsystem™ to work in a timely manner, I developed a Python script that produces the result we need, which is to allow the the Salesforce™ middleware to retrieve the documents produced by our ERP and published on the DMS. This happens via a standard API which traverses the DMS filesystem. The script does not directly interact with the DMS, instead - given the publication ID and version of the file - traverses the filesystem and returns the file.

All trademarks mentioned are the property of their respective owners.  


#### Panoramica
Questo progetto consiste in un'API basata su Python che interagisce con un sistema di gestione dei file per localizzare e recuperare file in base all'ID della pubblicazione e al numero di versione. Include autenticazione degli utenti e configurazioni per i percorsi delle directory e le impostazioni del server.

#### Componenti Principali
1. **api.py**: Implementazione principale dell'API utilizzando Flask. Gestisce l'autenticazione degli utenti e le richieste di recupero dei file.
2. **script.py**: Contiene la logica per localizzare il file richiesto all'interno della directory specificata.
3. **hashpasswd.py**: Uno script di utilità per crittografare le password per l'autenticazione degli utenti.
4. **runme.py**: Script per avviare il server API.
5. **config.config**: File di configurazione che memorizza i percorsi delle directory e le impostazioni della porta del server.
6. **user.list**: Memorizza le credenziali degli utenti nel formato `username:hashed_password`.
7. **test_api.py**: Test unitari per la funzionalità dell'API.
8. **test_script.py**: Test unitari per la logica di localizzazione dei file.

#### Funzionalità
- **Autenticazione degli Utenti**: Gli utenti sono autenticati utilizzando l'autenticazione HTTP Basic. Le password sono crittografate usando bcrypt.
- **Recupero File**: L'API consente agli utenti di richiedere file fornendo un ID di pubblicazione e un numero di versione. Il file `script.py` contiene la logica per cercare il file nella directory specificata.
- **Configurazione**: L'API legge le configurazioni da `config.config` per determinare la directory base per l'archiviazione dei file e la porta su cui viene eseguito il server.

#### Utilizzo
1. **Impostazione**:
   - Assicurarsi che Python e le librerie necessarie (`Flask`, `bcrypt`, `Flask-HTTPAuth`) siano installati.
   - Popolare `user.list` con utenti e password crittografate.
   - Configurare `config.config` con la directory base appropriata e la porta che dovrá parimenti essere aperta e configurata sul firewall

2. **Esecuzione dell'API**:
   - Eseguire `runme.py` per avviare il server Flask.
   - Utilizzare endpoint come **`/findfile?publication_id=<id>&version_number=<number>`** per recuperare i file.

3. **Test**:
   - Eseguire `test_api.py` e `test_script.py` per garantire che l'API e la logica di localizzazione dei file funzionino correttamente.
  
### Configurazione come Servizio su Windows (Opzionale)

Lo script puó essere configurato come servizio su Windows Server utilizzando NSSM


### Licenza
Sofware proprietario, disponibile su licenza

### Contatti
Per qualsiasi richiesta, contatta l'autore scrivendo a: g punto costantini chiocciola gmail punto com


### English Description

#### Overview
This project consists of a Python-based API that interacts with a file management system to locate and retrieve files based on publication ID and version number. It includes user authentication and configurations for directory paths and server settings.

#### Main Components
1. **api.py**: This is the main API implementation using Flask. It handles user authentication and file retrieval requests.
2. **script.py**: Contains the logic to locate the requested file within the specified directory.
3. **hashpasswd.py**: A utility script to hash passwords for user authentication.
4. **runme.py**: A script to start the API server.
5. **config.config**: Configuration file that stores directory paths and server port settings.
6. **user.list**: Stores user credentials in the format `username:hashed_password`.
7. **test_api.py**: Unit tests for the API functionality.
8. **test_script.py**: Unit tests for the file locating logic.

#### Functionality
- **User Authentication**: Users are authenticated using HTTP Basic Authentication. Passwords are hashed using bcrypt.
- **File Retrieval**: The API allows users to request files by providing a publication ID and version number. The `script.py` file contains the logic to search for the file in the specified directory.
- **Configuration**: The API reads configurations from `config.config` to determine the base directory for file storage and the port on which the server runs.

#### Usage
1. **Setup**:
   - Ensure Python and necessary libraries (`Flask`, `bcrypt`, `Flask-HTTPAuth`) are installed.
   - Populate `user.list` with users and hashed passwords.
   - Configure `config.config` with the appropriate base directory and port which also needs to be opened and configured on the firewall.

2. **Running the API**:
   - Execute `runme.py` to start the Flask server.
   - Use endpoints like `/findfile?publication_id=<id>&version_number=<number>` to retrieve files.

3. **Testing**:
   - Run `test_api.py` and `test_script.py` to ensure the API and file locating logic are functioning correctly.
  
### Windows Service Setup (Optional)

The script can be configured as a service on Windows Server using NSSM
  
  
### License
Proprietary sofware, available upon licensing

### Contatti
For further information contact the author: g dot costantini at gmail dot com



