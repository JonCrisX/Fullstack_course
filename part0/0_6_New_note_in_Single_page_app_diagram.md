```mermaid

sequenceDiagram
    participant user
    participant browser
    participant server

    user->>browser: user types new note and saves it

    browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note_spa
    activate server
    server-->>browser: [{"content": "this is a new note", "date": "2024-08-13T14:01:06.757Z"}]
    Note right of server: HTTP 201, new note created
    deactivate server

    browser->>browser: render new note without without reloading the page