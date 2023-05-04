sequenceDiagram
    participant selain
    participant serveri
    
    selain->>serveri: GET https://studies.cs.helsinki.fi/exampleapp/spa
    activate serveri
    serveri-->>selain: HTML-dokumentti (sivun lataus)
    deactivate serveri

    selain->>serveri: GET https://studies.cs.helsinki.fi/exampleapp/main.css
    activate serveri
    serveri-->>selain: CSS-tiedosto (muotoilu)
    deactivate serveri
    
    selain->>serveri: GET https://studies.cs.helsinki.fi/exampleapp/spa.js
    activate serveri
    serveri-->>selain: JavaScript-tiedosto
    deactivate serveri
    
    Note right of selain: javascriptin suoritus hakee json-tiedoston eli raakadatan
    
    selain->>serveri: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate serveri
    serveri-->>selain: [{ "content": "frogs are people too", "date": "2023-05-04T09:13:28.386Z" }, ... ] 
    deactivate serveri    
    
    Note right of selain: takaisinkutsufunktio > raakadata