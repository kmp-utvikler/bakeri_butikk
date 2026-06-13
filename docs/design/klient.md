
Klient view

```mermaid
classDiagram
    class VinduManager {
        -butikk_vindu ButikkVindu
        -vogn_vindu VognVindu
    }
    class ButikkVindu {
        -produkt_korter List<Produkt>
        +oppdater_produkter() void
        +legg_til_vogn(Produkt produkt) void
    }
    class ProduktKort {
        -produkt_id int
        -produkt_navn string
        -produkt_pris float
        -produkt_beskrivelse string
    }
    class VognVindu {
        -produkt_i_vogn List<Produkter>
        +fjern_fra_vogn(Produkt produkt) void
        +kjop_produkter(List<Produkt> produkter) void
    }
    VinduManager "1"--"1" ButikkVindu
    VinduManager "1"--"1" VognVindu
    VognVindu "1"--"0..*" ProduktKort

```


Klient kontroll

```mermaid
classDiagram
    class Kontroll {
        +hent_produkter() Produkter
        +hent_vogn() Produkter
        +legg_til_vogn(Produkt produkt) void
        +fjern_fra_vogn(Produkt produkt) void
        +kjøp_produkter(List<Produkt> produkt) void
    }
```

KLient Modell

```mermaid

classDiagram
    class Klient {
        -produkter List<Produkt>
        -butikk_socket ButikkSocket
        +lag_socket() ButikkSocket
        +last_inn_produkter() Produkter
        +hent_produkter() Produkter
        +hent_vogn() List<Produkt>
        +kjop_produkter() void
    }
    class VognManager {
        -produkter_i_vogn List<Produkt>
        +legg_til_produkt(Produkt produkt) void
        +fjern_produkt(Produkt produkt) void
        +hent_produkter() Produkter
    }
    class Produkt {
        -produktID int
        -navn string
        -pris float
        -beskrivelse string
        -antall int
        +hent_info() string
        +hent_id() int
        +hent_navn() string
        +hent_pris() float
        +hent_beskrivelse() string
        +hent_antall() int
    }
    class ButikkSocket {
        -port int
        -ip_address string
        -klient_socket socket.socket
        +koble_til_server() void
        +lytt_etter_forbindelse() void
        +les_fra_server() bytes
        +skriv_til_server() void
        +oversett_bytes() void
    }
    Klient "1" -- "1" ButikkSocket    
    Klient "1" -- "1" VognManager    
    Klient "1"--"0..*" Produkt

```
