# Síťová integrace v multiplayerových hrách

## Úvod

Síťová integrace je, jak nám sám název napovídá, využití (integrace) síťových technologií v nečem. K čemu se ale používá v multiplayerových hrách? Používá se například k tomu, aby jste si s kamarády mohli užít zábavu z her společne, když zrovna nejste na stejném místě. Samozřejmě je dost dalších důvodů dělat multiplayerové hry, jako třeba přítomnost lidského protivníka, není totiž lepší protivník než jiný člověk. Také se multiplayerové hry dají skoro nekonečné hrát opakovaně, protože tam často hráči mají veliké množství možností se někde rozhodnout jinak, něco jinak udělat a tak podobně a vzhledem k tomu, že tuhle hraje více hráčů najednou jsou možnosti, že se stane uplně stejná hra mizivé.

## Offline a Online hry

Multiplayerové hry lze rozdělit na dva typy. Offline - hry co se hrají na jednom počítači (ve více lidech), například: Mortal Kombat, F1, Call of Duty, Party Beasts. Online - hry co se hrají na více počítačích, které spolu kominikují, například: League of Legends, VALORANT, GTA V, Stardew Valley. Ty se dále dají rozlišit dle typů připojení.

### Splitscreen/Local Multiplayer

Local multiplayer neboli splitscreen(roždělená obrazovka) je žánr multiplayeru, kde se hráčům dělí obrazovka tak aby mohli ovládat svojí postavu a hrají na různých ovladačích. Zařadil bych je do Offline her. Jsou jednodušší, protože se zajímáte jen o klientskou stranu hry (není potřeba server nebo připojení ke komunikaci). Často ale jako u například Call of Duty se zde nachází Online multiplayer módy s jiným připojením. Zmiňuji tu tento žánr, protože také patří do multiplayer her.

### LAN

LAN neboli Local Area Network je typ připojení používaný hlavně v minulost, kdy sítě nebyly tak rychlé, aby se na nich něco dalo hrát. Spočívá v tom, že počítače hráčů jsou připojeny k serveru napřímo kabelem. Jeho výhody jsou velmi nízká latence a to a malé zatížení serveru. V dnešní době, a předpokládám že bude i nadále, je používán hlavně v kompetetivních hrách ve velkých nebo malých turnajích.

### Peer to Peer

Peer to peer je typ sítě, kde si všichni klienti posílají informace navzájem. Problém s touto sítí je ten, že se stoupajícím počtem hráčů, stoupá počet připojení a taky tlak na počítač, takže se skoro nedá škálovat. Také tu není žadný server nebo autorita na zabezpečení, která by prověřovala posílané údaje a zamezila v cheatování. Tento typ připojení byl používán hlavně u Age of Empires, protože v podstatě minimalizoval ztráty pro hráče se špatným připojením.

### Host (Host advantage)



### Client to server

## Jak funguje posílání dat? (TCP UDP sockety porty)

## Synchronizace Stavu Hry

Stav hry jsou informace, které posíláme v jeden okamžik z jednoho počítače na jiný

## Tick rate

## Asynchronní hry

## Buffer (data, které uživatel již přijmul, ale ještě se mu neukazují)

## Client-side prediction (Rubber banding)

## Client authoritative control (Favor the shooter systém)

## Networking frameworky

## Shrnutí

Síťová integrace je důležitý proces při vytváření multiplayerových her. Je to cesta k propojení hráčů, aby si spolu mohli zahrát přes internet. Je to těžký a komplexní proces, který zahrnuje kroky jako připojení počítačů ke komunikaci a synchronizaci stavu hry mezi klienty a serverem. Proto existují i frameworky co udělají některé z těchto věcí za nás.
