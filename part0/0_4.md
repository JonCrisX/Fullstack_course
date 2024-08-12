```mermaid

sequenceDiagram
    participant user
    participant browser
    participant server

    user->>browser: User types note and saves it

    browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note with new note
    activate server
    Note right of server: server receives new note and saves it
    server-->> browser: HTTP 302 redirect to /notes
    deactivate server

    Note right of browser: browser follows the redirect and renders in notes page

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/notes
    activate server
    server-->>browser: HTML document
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.css
    activate server
    server-->>browser: the css file
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.js
    activate server
    server-->>browser: the JavaScript file
    deactivate server

    Note right of browser: The browser starts executing the JavaScript code that fetches the JSON from the server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate server
    server-->>browser: [{ "content": "HTML is easy", "date": "2023-1-1" }, ... ]
    deactivate server

    Note right of browser: The browser executes the callback function that renders the notes

