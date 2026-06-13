# oversikt
Bakeri butikk er en desktop applikasjon med fokus på å demonstrere nettverks-, tråd- og gui
programmering i python, og unngår å bruke web teknologier. Fokuset er ikke på database så json
og csv blir brukt for å håndtere dette. Kommunikasjonen foregår over tcp med egen nettverks
protokoll som bruker rå bytes. Som en demonstration blir penger for både klient og server
uendelig.

## mål:
- Ha grafisk interface for både klient og server
- Demonstrere socket kommunikasjon
- Demonstrere håndtering av parallel request med tråd

# komponenter

## klient

klient har ansvar for å:
- vise produkter
- handlevogn håndtering
- ordreplassering
- visning av server respons

## server

server har ansvar for å:
- vise produkt informasjon
- legge til produkter
- fjerene produkter
- akseptere innkommende klient forbindelse
- håndtering av varelager
- håndtere bestillinger
