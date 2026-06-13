klient og server komponentene bruker model-view-control mønsteret for å tilby grafisk
bruker grensesnitt for bruker. Bruker interagerer med komponent via view, klient og
serveren interagerer via modellen. 

høynivå overordnet arkitektur

```mermaid

graph LR
    subgraph Klient[Klient]
        C_View[View] --- C_Kontroll[Kontroll]
        C_Kontroll[Kontroll] --- C_Modell[Modell]
    end
    subgraph Server[Server]
        S_View[View] --- S_Kontroll[Kontroll]
        S_Kontroll[Kontroll] --- S_Modell[Modell]    
    end
    Klient ---|TCP Socket| Server
    C_Bruker[Bruker] --- Klient
    Server --- S_Bruker[Bruker]

```

