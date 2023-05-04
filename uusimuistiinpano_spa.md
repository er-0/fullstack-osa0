sequenceDiagram
    participant selain
    participant serveri
    
    selain->>serveri: POST https://studies.cs.helsinki.fi/exampleapp/new_note_spa
    activate serveri
    serveri-->>selain: vain statuskoodi (201 created)
    deactivate serveri

    note left of serveri: muistiinpano lisätään json-tiedostoon, ei uudelleenohjausta tai muita HTTP-pyyntöjä
    