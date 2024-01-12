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

Peer to peer je typ sítě, kde si všichni klienti posílají informace navzájem. Problém s touto sítí je ten, že se stoupajícím počtem hráčů, stoupá počet připojení a taky tlak na počítač, takže se skoro nedá škálovat. Také tu není žadný server nebo autorita na zabezpečení, která by prověřovala posílané údaje a zamezila v cheatování. Tento typ připojení byl používán u **Age of Empires**, protože v podstatě minimalizoval ztráty pro hráče se špatným připojením.

### Host

Host síť je typ sítě, kde jeden z hráčů je vybrán jako host a zbytek se připojuje k němu a dostává data od něj. Host se chová jako takový server i když je sám hráčem. Oproti peer to peer modelu tak výrazně sníží počet připojení. Další výhoda je malá cena tohoto modelu, protože to moc nestojí, když všechno běží na jednom počítači. Nevýhoda tohoto modelu je takzvaná výhoda hosta, kde host v podstatě nemá latenci a tak se nehodí pro něco moc kompetetivního. Také je tu problém s tím, když se host odpojí od komunikace. Pokud nechceme, aby hra spadla musíme aplikovat nějakou metodu migrace hosta, aby se hostování hry přesunulo na jiného hráče. S tímto typem připojení přece jenom byly úspěšné indie kooperativní hry jako Terraria a Stardew Valley.

### Client to server

Client to server je typ sítě, kde se hráči připojují k jednomu serveru a mezi ním a sebou si posílají data. Jeho výhody jsou zabezpečení, možnost mnoha připojení jako host síť, ale bez toho aby měl host výhodu. Nevýhody jsou, že využívání serveru nebo cloudových služeb může být drahé, takže by hra měla vyděávat aspoň cenu využití toho nebo těch serverů. V dnešní době je u her velice populární. Používají ho hlavně hry od většich firem.

## Posilání dat

Aby mezi sebou mohly počítače komunikovat a posílat si data musí si otevřít socket, který se skládá z IP adresy(adresy počítače nebo routeru) a portu například: 123.123.123.123:80. Porty se využívají abychom rozeznali různé protokoly nebo služby co běží na jednom počítači. Také router pozná podle portu, který počítač v síti si službu vyžádal. Používají se také protokoly k posílání dat, které posílaným datům dávají instrukce jakým způsobem se mají dostat ke klientovi nebo serveru. Nejpoužívanější protokoly jsou TCP a UDP.

### TCP

TCP neboli Transmission Communication Protocol je protokol, který přesune data z jednoho počítače na druhý pomaleji a za trošku větší cenu výpočetního výkonu, ale za to důkladně a ve správném pořadí. TCP se ve hrách používá například k navázání komunikace s uživatelem a k přesouvání dat jako jsou informace o uživateli.

### UDP

UDP neboli User Datagram Protocol je protokol, který narozdíl od TCP přesune data mnohem rychleji, ale často ne ve správném pořadí. UDP se ve hrách používá na věci, které se často mění jako stav objektů.

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
