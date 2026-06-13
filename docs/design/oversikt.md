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
og Vindu Manager som kobler til hverandre. Mer beskrivende klassediagram ligger i 
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
