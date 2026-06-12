# kommunikasjon og protokoll

pakke format

header

størrelse       betydning
8 bits          type 
24 bits         lengde 

melding typer
verdi   betydning
0x01    REQ_PRODUCTS
0x02    RSP_PRODUCTS
0x03    REQ_PURCHASE
0x04    RSP_PURHASE
0x05    ERR_PRODUCT
0x06    ERR_PRICE
0x07    ERR_STOCK

payloaad

REQ_PRODUCTS
None

RSP_PRODUCTS
størrelse       betydning
16 bits         antall produkt 

produkt
størrelse       betydning
32 bits         pris
8 bits          navn lengde 
N bits          navn
16 bits         beskrivelse lengde
N bits          beskrivelse

REQ_PURCHASE
størrelse       betydning
32 bits         pris
8 bits          navn lengde 
N bits          navn

RSP_PURHASE
None


ERR_PRODUCT
None

ERR_PRICE
størrelse       betydning
32 bits         pris

ERR_STOCK
størrelse       betydning
32 bits         mengde i lager