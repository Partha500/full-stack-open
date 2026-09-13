sequenceDiagram
     participant browser
     participant server 

     browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note
     activate server 
     server-->>browser: 302 response  redirecting to https://studies.cs.helsinki.fi/exampleapp/notes
     deactivate server 

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
    server-->>browser: [{ "content": "learn full stack open", "date": "2026-09-13T20:15:23.544Z" }, ... ]
    deactivate server    

    Note right of browser: The browser executes the callback function that renders the notes 