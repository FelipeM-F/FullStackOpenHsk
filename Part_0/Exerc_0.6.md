sequenceDiagram
    participant browser
    participant server

    Note right of browser: The user types the new note's text and clicks 'Save'.
    Note right of browser: The JavaScript (form.onsubmit) prevents the default form behavior.

    browser->>browser: Adds the new note locally to the 'notes' array.
    browser->>browser: Calls redrawNotes() to update the UI immediately.

    browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note_spa
    activate server
    Note left of server: The server receives the new note's JSON and stores it.
    server-->>browser: 201 Created
    deactivate server

    Note right of browser: The browser does not need to reload the page or fetch all data again, as it has already updated the UI locally.