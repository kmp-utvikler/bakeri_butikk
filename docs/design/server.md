
Server view

```mermaid
classDiagram
    class VinduManager {
        -produkt_vindu ProduktVindu
        -rediger_vindu RedigerProduktVindu
        -transaksjons_vindu TransaskjonsVindu
        -detalje_vindu DetaljeVindu
    }
    class ProduktVindu {
        -produkt_korter List<Produkter>
        +oppdater_produkter() void
    }
    class ProduktKort {
        -produkt_id int
        -produkt_navn string
        -produkt_pris float
        -produkt_beskrivelse string
        -produkt_antall int
        +rediger_produkt() void
    }
    class RedigerProduktVindu {
        -produkt_id int
        -produkt_navn string
        -produkt_pris float
        -produkt_beskrivelse string
        -produkt_antall int
        +set_endringer() void
    }
    class TransaksjonsVindu {
        -transaksjon_korter List<TransaksjonsKort>
    }
    class TransaksjonKort {
        -transaksjons_id int
        +vis_detalje() void
    }
    class DetaljeVindu {
        -transaksjons_id int
        -produkter List<Produkter>
        -dato datetime
        -status OrdreStatus
    }
    enum OrdreStatus {
        NY
        BEHANDLES
        SENDT
    }

    
```

Server kontroll

```mermaid
classDiagram
    class Kontroll {
        +hent_produkter() Produkter
    }
```

Server modell

```mermaid
classDiagram
    class Server {
        -butikk_socket ButikkSocket
        -produkt_manager ProduktManager
        +lag_socket() ButikkSocket
        +lag_produkt_manager() ProduktManager
        +hent_produkter() Produkter
        +send_produkter(List<Produkt> produkter) void
        +behandle_transaksjon() void
    }
    class ProduktManager {
        -produkter List<Produkt>
        +hent_produkter() Produkter
        +legg_til_produkt(Produkt produkt) void
        +slett_produkt(Produkt produkt) void
        +endre_produkt_navn(string nynavn) void
        +endre_produkt_pris(float nypris) void
        +endre_produkt_beskrivelse(string nybeskrivelse) void
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
    Server "1"--"1" ButikkSocket    
    Server "1"--"1" ProduktManager
    ProduktManager "1"--"0..*" Produkt
```

