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

Domene modell for hele klient system. Hoved komponentene i modellen er Klient, Kontroll 
og VinduManager som kobler til hverandre. Mer beskrivende klassediagram ligger i 
klient.md

```mermaid

%% Klient View

classDiagram

    class VinduManager
    class ButikkVindu
    class ProduktKort
    class VognVindu

%% Klient view klasse forbindelse

    VinduManager "1"--"1" ButikkVindu
    VinduManager "1"--"1" VognVindu
    VognVindu "1"--"0..*" ProduktKort

%% Klient Kontroll

    class Kontroll

%% Klient Model

    class Klient 
    class VognManager 
    class Produkt
    class ButikkSocket 
    
%% Klient modell klasse forbindelse

    Klient "1" -- "1" ButikkSocket    
    Klient "1" -- "1" VognManager    
    Klient "1"--"0..*" Produkt

%% Klient modell view og kontroll forbindelse

    Klient "1"--"1" Kontroll
    Kontroll "1"--"1" VinduManager
    VognManager "1"--"0..*" Produkt
```

Domene modell for hele server system. Hoved komponentene i modellen er Server, Kontroll 
og VinduManager som kobler til hverandre. Mer beskrivende klassediagram ligger i 
server.md

```mermaid

%% Server View

classDiagram
    class VinduManager {}
    class ProduktVindu {}
    class ProduktKort {}
    class RedigerProduktVindu {}
    class TransaksjonsVindu {}
    class TransaksjonsKort {}
    class DetaljeVindu {}
    class OrdreStatus {}

    VinduManager "1"--"1" ProduktVindu
    VinduManager "1"--"1" RedigerProduktVindu
    VinduManager "1"--"1" DetaljeVindu
    VinduManager "1"--"1" TransaksjonsVindu 
    ProduktVindu "1"--"0..*" ProduktKort
    TransaksjonsVindu  "1"--"0..*" TransaksjonsKort
    DetaljeVindu --> OrdreStatus

%% Server Kontroll

    class Kontroll {}

%% Server Modell

    class Server {}
    class ProduktManager {}
    class Produkt {}
    class ButikkSocket {}
    Server "1"--"1" ButikkSocket    
    Server "1"--"1" ProduktManager
    ProduktManager "1"--"0..*" Produkt

    VinduManager "1"--"1" Kontroll
    Kontroll "1"--"1" Server

```


