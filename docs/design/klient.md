
Klient view

```mermaid
classDiagram
    class VinduManager {
        -butikk_vindu
        -vogn_vindu
    }
    class ButikkVindu {
        -produkt_korter
        +legg_til_vogn(Produkt) void
    }
    class ProduktKort {
        -produkt_id
        -produkt_navn
        -produkt_pris
        -produkt_beskrivelse
    }
    class VognVindu {
        -produkt_i_vogn
        +fjern_fra_vogn(Produkt) void
        +kjop_produkter()
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
        +legg_til_vogn(Produkt) void
        +fjern_fra_vogn(Produkt) void
        +kjøp_produkter() void
    }
```

KLient Modell

```mermaid

classDiagram
    class Klient {
        -produkter
        -butikk_socket
        +lag_socket() ButikkSocket
        +last_inn_produkter() Produkter
        +hent_produkter() Produkter
        +hent_vogn
        +kjop_produkter() void
    }
    class VognManager {
        -produkter_i_vogn
        +legg_til_produkt()
        +fjern_produkt()
        +hent_produkter() Produkter
    }
    class Produkt {
        -produktID
        -navn
        -pris
        -beskrivelse
        +hent_info() string
        +hent_id() int
        +hent_navn() string
        +hent_pris() float
        +hent_beskrivelse() string
    }
    class ButikkSocket {
        -port
        -ip_address
        -klient_socket
        +koble_til_server() void
        +les_fra_server() bytes
        +skriv_til_server() void
        +oversett_bytes()
    }
    Klient "1" -- "1" ButikkSocket    
    Klient "1" -- "1" VognManager    
    Klient "1"--"0..*" Produkt

```
