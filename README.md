# Bachelor thesis
A web-based software for budget and expense management.

The spring boot backend can be found under "./src" and the angular-frontend under "./frontend". For further information, please refer to the written bachelor thesis and the documentation under “/doc/”. To test this application, please follow the instructions below: 

1. Install and Config PostgreSQL (docker)
    * Install & run Postgres e.g. via docker compose (./doc/docker/postgresql/docker-compose.yml)
        - Windows: <https://www.docker.com/products/docker-desktop/>
        - Linux (Debian): 'sudo apt-get install docker'
        - In directory (./doc/docker/postgresql/) run via command line: 'docker compose up'
2. Install TesseractOCR
    * Linux-Ubuntu: 'sudo apt-get install tesseract-ocr tesseract-ocr-deu'
    * Windows: <https://tesseract-ocr.github.io/tessdoc/Installation.html>
3. Install ollama and install required modells
    * Installation
        - Linux: https://ollama.com/download/linux
        - Windows: https://ollama.com/download/windows
    * Download required Modells via command line:
        - 'ollama run qwen3:8b'
        - 'ollama run deepseek-r1:8b'
4. Edit “./src/main/resources/application.properties”
    * Check Hibernate Config
        - spring.jpa.hibernate.ddl-auto=create
            * (create = create new relations)
            * (update = updating relations by changes)
            * (none = only use exist relations)
    * Check PostgreSQL Config
        - URL to your postgrsql instance with db name and Username + Password
            * spring.datasource.url=jdbc:postgresql://localhost:5532/cashflow
            * spring.datasource.username=test
            * spring.datasource.password=test
    * Check TesseractOCR Config
        - Path to TessData and set Language
            * tesseract.language=deu
            * tesseract.datapath=/usr/share/tesseract-ocr/5/tessdata
5. Pull the required project-dependencies from mavenhub and start the backend over your IDEA
    * 'mvn dependency:resolve'
    * 'mvn spring-boot:run' 
        - Java main in ./src/main/java/cash_flow_recorder/CashFlowRecorderApplication.java
6. Install Node Package Manager and start the Frontend
    * Install NPM for Linux (debian): sudo apt-get install npm
    * Install NPM for Windows: <https://nodejs.org/en/download>
    * Change Directory to frontend (./frondend) and run follow command line
        - 'npm install'
        - 'npm install -g @angular/cli'
        - 'ng serve --ssl true --port 54545'
7. (Alternatively) - Import the Testdata
    * Install Bruno API-Client-Software "Bruno"
        - https://www.usebruno.com/
    * Open and run Post-Collection from ./doc/api-collections/Create_test-environment/