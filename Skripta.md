# Síťová integrace v multiplayerových hrách

## Úvod

Síťová integrace je, jak nám sám název napovídá, využití (integrace) síťových technologií v nečem. K čemu se ale používá v multiplayerových hrách? Používá se například k tomu, aby jste si s kamarády mohli užít zábavu z her společne, když zrovna nejste na stejném místě. Samozřejmě je dost dalších důvodů dělat multiplayerové hry, jako třeba přítomnost lidského protivníka, není totiž lepší protivník než jiný člověk. Také se multiplayerové hry dají skoro nekonečné hrát opakovaně, protože tam často hráči mají veliké množství možností se někde rozhodnout jinak, něco jinak udělat a tak podobně a vzhledem k tomu, že tuhle hraje více hráčů najednou jsou možnosti, že se stane uplně stejná hra mizivé.

## Offline a Online hry

Multiplayerové hry lze rozdělit na dva typy. Offline - hry co se hrají na jednom počítači (ve více lidech), například: Mortal Kombat, F1, Call of Duty, Party Beasts. Online - hry co se hrají na více počítačích, které spolu kominikují, například: League of Legends, VALORANT, GTA V, Stardew Valley. Ty se dále dají rozlišit dle typů připojení.

### Splitscreen/Local Multiplayer

Local multiplayer neboli splitscreen(roždělená obrazovka) je žánr multiplayeru, kde se hráčům dělí obrazovka tak aby mohli ovládat svojí postavu a hrají na různých ovladačích. Zařadil bych je do Offline her. Jsou jednodušší, protože se zajímáte jen o klientskou stranu hry (není potřeba server nebo připojení ke komunikaci). Často ale jako u například Call of Duty se zde nachází Online multiplayer módy s jiným připojením. Zmiňuji tu tento žánr, protože také patří do multiplayer her.

### LAN

![lantopology](https://github.com/ExoniaQ/MultiplayerNetworkingProject/assets/75218536/074bbaa9-8261-4140-af6e-2cf5e1dfa622)

LAN neboli Local Area Network je typ připojení používaný hlavně v minulost, kdy sítě nebyly tak rychlé, aby se na nich něco dalo hrát. Spočívá v tom, že počítače hráčů jsou připojeny k serveru napřímo kabelem. Jeho výhody jsou velmi nízká latence a to a malé zatížení serveru. V dnešní době, a předpokládám že bude i nadále, je používán hlavně v kompetetivních hrách ve velkých nebo malých turnajích.

### Peer to Peer

![peertopeer](https://github.com/ExoniaQ/MultiplayerNetworkingProject/assets/75218536/08c63950-71b1-4ac6-93a3-388ac25b5116)

Peer to peer je typ sítě, kde si všichni klienti posílají informace navzájem. Problém s touto sítí je ten, že se stoupajícím počtem hráčů, stoupá počet připojení a taky tlak na počítač, takže se skoro nedá škálovat. Také tu není žadný server nebo autorita na zabezpečení, která by prověřovala posílané údaje a zamezila v cheatování. Tento typ připojení byl používán u **Age of Empires**, protože v podstatě minimalizoval ztráty pro hráče se špatným připojením.

### Host

![host](https://github.com/ExoniaQ/MultiplayerNetworkingProject/assets/75218536/93b0d4db-4d07-43b0-b0fb-eedfd7fff65b)

Host síť je typ sítě, kde jeden z hráčů je vybrán jako host a zbytek se připojuje k němu a dostává data od něj. Host se chová jako takový server i když je sám hráčem. Oproti peer to peer modelu tak výrazně sníží počet připojení. Další výhoda je malá cena tohoto modelu, protože to moc nestojí, když všechno běží na jednom počítači. Nevýhoda tohoto modelu je takzvaná výhoda hosta, kde host v podstatě nemá latenci a tak se nehodí pro něco moc kompetetivního. Také je tu problém s tím, když se host odpojí od komunikace. Pokud nechceme, aby hra spadla musíme aplikovat nějakou metodu migrace hosta, aby se hostování hry přesunulo na jiného hráče. S tímto typem připojení přece jenom byly úspěšné indie kooperativní hry jako Terraria a Stardew Valley.

### Client to server

![clientserver](https://github.com/ExoniaQ/MultiplayerNetworkingProject/assets/75218536/bc6c7e07-cd19-44d7-8dfd-0eaaa952f432)

Client to server je typ sítě, kde se hráči připojují k jednomu serveru a mezi ním a sebou si posílají data. Jeho výhody jsou zabezpečení, možnost mnoha připojení jako host síť, ale bez toho aby měl host výhodu. Nevýhody jsou, že využívání serveru nebo cloudových služeb může být drahé, takže by hra měla vyděávat aspoň cenu využití toho nebo těch serverů. V dnešní době je u her velice populární. Používají ho hlavně hry od většich firem.

## Posilání dat

Aby mezi sebou mohly počítače komunikovat a posílat si data musí si otevřít socket, který se skládá z IP adresy(adresy počítače nebo routeru) a portu například: 123.123.123.123:80. Porty se využívají abychom rozeznali různé protokoly nebo služby co běží na jednom počítači. Také router pozná podle portu, který počítač v síti si službu vyžádal. Používají se také protokoly k posílání dat, které posílaným datům dávají instrukce jakým způsobem se mají dostat ke klientovi nebo serveru. Nejpoužívanější protokoly jsou TCP a UDP.

### TCP

TCP neboli Transmission Communication Protocol je protokol, který přesune data z jednoho počítače na druhý pomaleji a za trošku větší cenu výpočetního výkonu, ale za to důkladně a ve správném pořadí. TCP se ve hrách používá například k navázání komunikace s uživatelem a k přesouvání dat jako jsou informace o uživateli.

### UDP

UDP neboli User Datagram Protocol je protokol, který narozdíl od TCP přesune data mnohem rychleji, ale často ne ve správném pořadí. UDP se ve hrách používá na věci, které se často mění jako stav objektů.

![TCPvsUDP](https://github.com/ExoniaQ/MultiplayerNetworkingProject/assets/75218536/963d6426-a945-422b-82c4-ce26f9bcdb40)

## Synchronizace Stavu Hry

Stav hry jsou informace, které posíláme v jeden okamžik z jednoho počítače na jiný. Jako například pohyb obketů nebo pohyb figurky v šachách. Multiplayer hry se snaží co nejvíce synchronizovat stav hry u jednotlivých klientů, aby viděli to samé. K tomue je užitečný tick rate. Tick rate je kolikrát za sekundu posílá hra klientovi data například s tick ratem 40 hra pošle update každých 25 milisekund. 

### Buffer

Toto může být použito například i v případě pohybu hráče, kdy hráč pošle data server je prověří a pošle zpátky. Toto by ale fungovalo dobře jen u asynchronních her, kde nejsou potřeba updaty tak často jako u šachů nebo karetních her. Nefungovalo by to dobře, protože většinou se na tuto komunikaci používá UDP a to múže data dát ve špatném pořadí, takže je možné, že hráčova pozice by se lagovala různě podle infa co dostal jako poslední. K opravení tohoto problému se používá buffer. Buffer podzdrží chvíli uživateli nějaké data, aby je mohl dát zase do správného pořadí, jsou to tedy data, které uživatel již přijmul, ale ještě se mu neukazují. Často se používá například ve streamování nebo v aplikacích co pouští videa, aby se video nerozbilo například na youtube je jako tato šedá čárka.

![bufferscreen](https://github.com/ExoniaQ/MultiplayerNetworkingProject/assets/75218536/db5458b5-5c0c-4c85-908c-cb9748ef670b)

### Client-side prediction

Dále můžeme mít problém, když na sekundu ztratíme připojení a pohyb objektů ve hře se nachvíli sekne a poté zase pustí. V těchzo případech používáme Client-side prediction (předvídání ze strany klienta). Je to předvídání kam se objekt pohne pokud nedostaneme jeho pozici od serveru, například, když hráč jde rovně tak předvídáme, že půjde dál rovně. Také se tomu často říká rubber banding, protože při synchronizaci pozice objektu na serveru a u klienta se objekt pohne tam a zpátky jako guma.

### Client authoritative control

Další problém je aby se klient mohl dobře pohybovat a nemusel čekat například sekundu, aby se data poslala tam a zpátky, aby se mohl pohnout, to by nebylo moc příjemné na hraní. Měli bychom u takovýchto akcí zavést Client authoritative control, takzvaně dát klientovi moc vykonávat některé věci jako například pohyb. Bohužel info od klienta k serveru k dalšímu klientu putuje dost dlouhou dobu a může to být rozdíl mezi tím, kdo vystřelil první ve střílečce. Overwatch deverlopers v této situaci mají systém zvaný favor the shooter (dej přednost střelci), což znamená, že když vás někdo střelil na svojí obrazovce, tak většinou nechají tuhle střelu trefit.

## Networking frameworky

Aby vám s tímto pomohli tak existují networking frameworky. Networking frameworky jsou sady nástrojů a knihoven k vyřešení věcí jako jsou sockety, porty, synchronizace a jiných problémů. Tímto se můžete soustředit na vývoj hry místo řešení problémů, co už vyřešil někdo jiný. Příklady populárních networking frameworků jsou Photon, Mirror, FishNet a GameSparks.

## Ukázka

V této ukázce bych chtěl ukázat, jak vytvořit multiplayer hru v Unity s pomocí networking frameworku [Mirror](https://mirror-networking.com) a pluginu [ParrelSync](https://github.com/VeriorPies/ParrelSync). Mirror je networking framework, který je zdarma a pomůže nám s online aspektem projektu. ParrelSync je plugin do Unity, který nám umožní projekt naklonovat a replikovat změny, co provedeme, abychom nemuseli pokaždé buildovat k testování online aspektu. Nejdřív Mirror a Parrelsync nainstalujeme a importujeme do Unity.

![image](https://github.com/ExoniaQ/MultiplayerNetworkingProject/assets/75218536/8f2abf6f-e2cc-47b4-9f88-87816525be59)

![image](https://github.com/ExoniaQ/MultiplayerNetworkingProject/assets/75218536/cdea8c00-74e0-4be2-af24-639f373b6228)

![image](https://github.com/ExoniaQ/MultiplayerNetworkingProject/assets/75218536/64f2c70d-0745-40d5-ab33-5dff80595a21)

![image](https://github.com/ExoniaQ/MultiplayerNetworkingProject/assets/75218536/f93c3f3b-3688-4b91-a62e-80db41a9b19e)

Po importování ParrelSyncu by se měl objevit na horní liště. Klikneme na něj pravým a vytvoříme si nový clone projektu.

![image](https://github.com/ExoniaQ/MultiplayerNetworkingProject/assets/75218536/39ca3ffb-2680-41d0-9f52-0fbd863ab01f)

Poté udělejte novou scénu nebo vyberte Sample Scene a přidejte ji do build settings.

![image](https://github.com/ExoniaQ/MultiplayerNetworkingProject/assets/75218536/50240b51-c839-453d-b108-c7ac9991d94c)

Poté udělejte nový empty GameObject, pojmenujte ho NetworkManager a přidejte k němu tyto scripty.

![image](https://github.com/ExoniaQ/MultiplayerNetworkingProject/assets/75218536/8849bb48-8ec5-4fc9-afc2-bb20e13b3c94)

Poté si vytvořte nějakou plochu. Na plochu si 

![image](https://github.com/ExoniaQ/MultiplayerNetworkingProject/assets/75218536/f3046ba5-01de-48b6-a02f-d03062be2f47)

Poté si vytvořte Capsule, která bude našim hráčem. Přidejte ji NetworkTransfer script. Ve scriptu změňte Sync Direction na Client To Server, aby klient měl autoritu hýbat se svoji postavou. Přidejte Capsuli zatím prázdný PlayerScript, přejmenujte ji na Player. Přitáhněte ji dolu k souborům, aby se vytvořil prefab. Poté ji smažte.

![image](https://github.com/ExoniaQ/MultiplayerNetworkingProject/assets/75218536/95e8aa57-9e06-4db7-a9fd-3c5b4a9dbe23)

![image](https://github.com/ExoniaQ/MultiplayerNetworkingProject/assets/75218536/144e0eb6-efae-4846-96f1-5bfefcafb4dc)

![image](https://github.com/ExoniaQ/MultiplayerNetworkingProject/assets/75218536/5c111e94-5665-4c6d-8271-13f588e2a675)

![image](https://github.com/ExoniaQ/MultiplayerNetworkingProject/assets/75218536/d8b8cf53-24a6-4bad-8a6a-fc3ed6b50d0f)

![image](https://github.com/ExoniaQ/MultiplayerNetworkingProject/assets/75218536/1c1559b5-819b-41f3-9e4c-cb23e961f3f2)

Potom rozklikněte NetworkManager přetáhněte Player prefab z dokumentů do kolonky Player Prefab a změnte Player Spawn Method na Round Robin.

![image](https://github.com/ExoniaQ/MultiplayerNetworkingProject/assets/75218536/af0e6c98-2bbc-4254-9b60-cb54880ff619)

Poté si zkopírujte tento script do PlayerScript.

<code>using Mirror;
using UnityEngine;

namespace QuickStart
{
    public class PlayerScript : NetworkBehaviour
    {
        public override void OnStartLocalPlayer()
        {
            Camera.main.transform.SetParent(transform);
            Camera.main.transform.localPosition = new Vector3(0, 0, 0);
        }
 
        void Update()
        {
            if (!isLocalPlayer) { return; }
 
            float moveX = Input.GetAxis("Horizontal") * Time.deltaTime * 110.0f;
            float moveZ = Input.GetAxis("Vertical") * Time.deltaTime * 4f;
 
            transform.Rotate(0, moveX, 0);
            transform.Translate(0, 0, moveZ);
       }
    }
}</code>

## Shrnutí

Síťová integrace je důležitý proces při vytváření multiplayerových her. Je to cesta k propojení hráčů, aby si spolu mohli zahrát přes internet. Je to těžký a komplexní proces, který zahrnuje kroky jako připojení počítačů ke komunikaci a synchronizaci stavu hry mezi klienty a serverem.
