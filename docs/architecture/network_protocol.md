# kommunikasjon og protokoll


melding typer
verdi   betydning
0x01    REQ_PRODUCTS
0x02    RSP_PRODUCTS
0x03    REQ_PURCHASE
0x04    RSP_PURHASE
0x05    ERR_PRODUCT
0x06    ERR_PRICE
0x07    ERR_STOCK

pakke format

header

størrelse       betydning
8 bits          type 
24 bits         lengde 

payloaad

produkt
størrelse       betydning
32 bits         pris
32 bits         produkt kvantitet
8 bits          navn lengde 
N bits          navn
16 bits         beskrivelse lengde
N bits          beskrivelse

REQ_PRODUCTS
None

RSP_PRODUCTS
størrelse       betydning
16 bits         antall produkt 

REQ_PURCHASE
størrelse       betydning
16 bits         antall produkt

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


melding beskrivelse

REQ_PRODUCTS
forespørsel til server om å gi informasjon om produkter som er tilgjengelig

RSP_PRODUCTS
respons til REQ_PRODUCTS, informasjon om produkter og deres pris, produkt kvantitet
navn og beskrivelse

REQ_PURCHASE
forespørsel om 

RSP_PURHASE
ERR_PRODUCT
ERR_PRICE
ERR_STOCK