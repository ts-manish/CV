graph TD
    %% --- Participants ---
    User(["&#128100;<br/><b>User</b>"]):::actor
    Backend["<b>System Backend</b>"]
    DB["<b>Database</b>"]
    Scraper["<b>Web Scraper</b>"]
    LLM["<b>LLM Processor</b>"]
    Generator["<b>Newsletter Generator</b>"]
    Delivery["<b>Delivery Service</b>"]

    %% --- Layout structure ---
    subgraph News_Flow[" "]
        Backend --> DB
        Backend --> Scraper
        Scraper --> LLM
        LLM --> Generator
        Generator --> Backend
    end

    %% --- Interaction Flow ---
    User -- "1️⃣ submitPreferences()" --> Backend
    Backend -- "1.1️⃣ storePreferences()" --> DB
    Backend -- "2.1️⃣ fetchNews()" --> Scraper
    Scraper -- "2.2️⃣ rawNews" --> LLM
    LLM -- "2.3️⃣ simplifiedContent" --> Generator
    Generator -- "2.4️⃣ newsletterFiles" --> Backend
    Backend -- "3️⃣ sendNewsletter()" --> Delivery
    Delivery -- "3.1️⃣ deliverViaEmail()" --> User
    Delivery -- "3.2️⃣ deliverViaWhatsApp()" --> User

    %% --- Styling ---
    classDef actor fill:#fff,stroke:#333,stroke-width:2px
    style Backend fill:#fff,stroke:#333,stroke-width:2px
    style DB fill:#fff,stroke:#333,stroke-width:2px
    style Scraper fill:#fff,stroke:#333,stroke-width:2px
    style LLM fill:#fff,stroke:#333,stroke-width:2px
    style Generator fill:#fff,stroke:#333,stroke-width:2px
    style Delivery fill:#fff,stroke:#333,stroke-width:2px
