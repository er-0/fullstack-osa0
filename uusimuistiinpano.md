sequenceDiagram
    participant selain
    participant serveri
    
    selain->>serveri: POST https://studies.cs.helsinki.fi/exampleapp/new_note
    activate serveri
    serveri-->>selain: HTML-dokumentti
    deactivate serveri

    note left of serveri: muistiinpano lisätään json-tiedostoon, takaisin uudelleenohjauspyyntö (osoite seuraavalle GET:ille)
    
    selain->>serveri: GET https://studies.cs.helsinki.fi/exampleapp/notes
    activate serveri
    serveri-->>selain: HTML-dokumentti (sivun uudelleenlataus)
    deactivate serveri

    selain->>serveri: GET https://studies.cs.helsinki.fi/exampleapp/main.css
    activate serveri
    serveri-->>selain: CSS-tiedosto (muotoilun uudelleenlataus)
    deactivate serveri
    
    selain->>serveri: GET https://studies.cs.helsinki.fi/exampleapp/main.js
    activate serveri
    serveri-->>selain: JavaScript-tiedosto (uudelleenlataus)
    deactivate serveri
    
    Note right of selain: javascriptin suoritus hakee json-tiedoston eli raakadatan
    
    selain->>serveri: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate serveri
    serveri-->>selain: [{ "content": "HTML is easy", "date": "2023-1-1" }, ... ] (uudelleenlataus)
    deactivate serveri    

    Note right of selain: takaisinkutsufunktio > raakadata