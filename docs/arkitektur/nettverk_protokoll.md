# kommunikasjon og protokoll


melding typer
verdi   betydning
0x01    REQ_PRODUCTS
0x02    RSP_PRODUCTS
0x03    REQ_PURCHASE
0x04    RSP_PURCHASE
0x05    ERR_PURCHASE
0X06    ACK

pakke format

header

størrelse       betydning
8 bits          type 
24 bits         pakke størrelse

payload

produkt
størrelse       betydning
32 bits         pris
32 bits         produkt kvantitet
8 bits          navn lengde 
N bits          navn
16 bits         beskrivelse lengde
N bits          beskrivelse

REQ_PRODUCTS
32 bits         ID

RSP_PRODUCTS
størrelse       betydning
32 bits         ID
16 bits         antall produkt
N bits          produkter

REQ_PURCHASE
størrelse       betydning
32 bits         ID
16 bits         antall produkt
N bits          produkter

RSP_PURCHASE
32 bits         ID

ERR_PURCHASE
størrelse       betydning
32 bits         ID
8 bits          error flagger
8 bits          lengde til error korrigering
0,32,64 bits    korrigering

error flagger
flagg       betydning
b0001       fant ikke produktet
b0010       ikke nok vare i lager
b0100       prisen var ikke korrect

ACK
32 bits         ID

melding beskrivelse

REQ_PRODUCTS
forespørsel til server om å gi informasjon om produkter som er tilgjengelig.

RSP_PRODUCTS
respons til REQ_PRODUCTS, informasjon om produkter og deres pris, produkt kvantitet,
navn og beskrivelse.

REQ_PURCHASE
forespørsel om å kjøpe, antall produkter er alle ulike produkter som ønskes og kjøpes.
Informasjon for hver produkt er antall av produktet som skal kjøpes, pris og navn.

RSP_PURCHASE
kjøpet ble fullført

ERR_PURCHASE
error flagg som forteller hva gikk galt, kan ha flere feil på en gang. Korrigereing 
gir informasjon om riktig antall produkt i lager eller riktig pris. b0010 og b0100
dukker opp samtidig så viser korrigeringen antall produkt og deretter pris.

ACK
returnerer ID til forespørsel og respons for å vise at meldingen var mottat