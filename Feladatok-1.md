## Világ(modell) kialakítás a leíró XML beolvasásával

* Input: generált világot leíró XML
* Output: Modellezett világ; Mozgó/álló, áthajtható, ütközhető, tömeggel, mérettel rendelkező objektumok, koordináta-rendszerben
* Challenge: „mindenki erre vár”, az interfésznek mielőbb stabilnak kell lennie, akkor is, ha az implementáció még nincs meg
* Assignee: [Team1](https://github.com/orgs/SzFMV2018-Osz/teams/team1/members)


### Definition of Done

- [ ] Útelemek, fák, táblák egyéb XML-ben leírt objektumot felismerése, parse-olása
- [ ] Minden feldolgozott objektum rendelkezzen pozíció, orientáció, típusadatokkal
- [ ] Heterogén kollekció lehetőségének biztosítása
- [ ] Hierarchikus objektummodell a világ leírására
- [ ] A modell legyen felkészítve az XML-ből kiolvasott „statikus” objektumokon túl mozgó („dinamikus”) objektumok kezelésére is
- [ ] A modell tegyen különbséget azon objektumok között amelyeknek egy jármű nekimehet és amelyeknek nem (fa vs. útelem)

### Megjegyzések

* A kimenetként előállított objektumok lista akár lehet egy XmlObject lista, ahol az objektumok típusától függetlenül minden ilyenekben van tárolva, és majd a világ kialakításáért felelős csapat létrehozza belőlük a hierarchikus objektummodellt.
* Teljesen járható út, hogy a modell, az XML-ben található koordinátarendszerrel dolgozik, ebből adódóan minden számolás abban történik, csak a megjelenítés skálázza át. Vagy már beolvasáskor megtörténik egy koordinátatranszformáció és onnantól kezdve minden azon történik. Utóbbi hátránya, hogy a megjelenítéstől (felbontás szinten) teszi függővé a szimulációt.
* Vonatkozó [wikioldal](https://github.com/SzFMV2018-Osz/documentation/A-virtu%C3%A1lis-vil%C3%A1g)

## Vizualizáció

* Input: Objektummodel (modellezett világ)
* Output: Illeszkedő, résmentes "puzzle" megjelenítése, 24 FPS-el frissülő, folyamatos mozgás
* Challenge: Az objektumtranszformációk megfelelő végrehajtása, az objektummodellért felelős csapattal egyeztetés az objektumok elérését illetően
* Assignee: [Team2](https://github.com/orgs/SzFMV2018-Osz/teams/team2/members)

### Definition of Done

- [ ] A világ méretarányos megjelenítése egy arra alkalmas koordináta-rendszer bevezetésével
- [ ] XML-ből beolvasott objektumlista pozícióhelyes kirajzolása és illesztése a rendelkezésre álló építőelemekből
- [ ] mozgó objektumok helyes kirajzolása

### Megjegyzések

* Teljesen járható út, hogy a modell, az XML-ben található koordináta-rendszerrel dolgozik, ebből adódóan minden számolás abban történik, csak a megjelenítés számolja át.
* A programlaknak az alábbi módon kell kinéznie. A kezdeti kód ezt a felosztást már támogatja, tartalmaz két JPanel-t, ebből a `CourseDisplay`re kell a világ objektumait kirajzolni.
    ![gui_plan](https://raw.githubusercontent.com/SzFMV2018-Osz/documentation/master/images/gui_plan.png)
* Az IntelliJ IDEA GUI Designer-e *nem* használható!


## Irányítás

* Input: a billentyűzet
* Output: PRND váltó(fel-le), gáz és fék 0-100 skála, kormányállás tetszőlegesen választott skála index, billentyűleütés alapján
* Assignee: [Team3](https://github.com/orgs/SzFMV2018-Osz/teams/team3/members)

### Definition of Done

- [ ] a fék- és gázpedál állapota szabályozható
- [ ] fék- és gázpedál valamint a kormány sem binárisan működik, a billentyű nyomva tartás idejétől függ az input intenzitása
- [ ] fék- és gázpedál valamint a kormány is fokozatosan áll vissza alaphelyzetbe a billentyű felengedésével
- [ ] az automata váltó 4 „fokozata” szabályozható
- [ ] ACC: Állítható céltávolság (T jelű gombbal, körkörösen 0.8/1/1.2/1.4 másodperc)
- [ ] ACC: Állítható célsebesség (+/- gombbal, 30-160, 5-ös lépésközzel), és kijelzése
- [ ] Lane Keeping bekapcsolás
- [ ] Parkig pilot bekapcsolás
- [ ] irányjelző kapcsolható

### Megjegyzések

* A billentyűzet kezelése elvben kétféle lehet: pedálállás léptetése föl/le, kormányszög léptetése föl/le; tehát diszkrét események. Vagy folyamatos „additív hatású”. pl. W billentyű gáz adás, ha hosszabban van lenyomva, akkor nagyobb mértékben, tehát adott idő alatt fokozatosan éri el a 100%-os lenyomást. Utóbbi lényegesen játszhatóbb eredményt ad, nem szükséges 12 ujj az autó vezérléséhez. Preferált.
* Későbbi sprintekben egyéb vezérlőelemek is szükségessé válnak (tempomat beállítása, parking pilot aktiválása)


## Műszerfal

* Input: az Ego objektum mozgásállapota, hozzá kapcsolódó adatok
* Output: Fordulatszám, sebesség, kormány, gáz, fék, sebességváltó állása, irányjelző visszajelző, kocsi pozíció megjelenítése (x, y koordináta, az autó rajzolását a vizualizáció végzi, ez egy debug funkció)
* Challenge: egyeztetés a fordulatszámról, pozícióról, vizualizációról a komponens beépítéséről
* Assignee: [Team4](https://github.com/orgs/SzFMV2018-Osz/teams/team4/members)

### Definition of Done

- [ ] Megjelenik a fordulatszám mint „analóg óra”
- [ ] Megjelenik a sebesség mint „analóg óra”
- [ ] Megjelenik a kormányállás
- [ ] Megjelenik a gáz, fék állapota (progressbar)
- [ ] Megjelenik a sebességváltó állása (szövegesen)
- [ ] Irányjelző visszajelző (egy-egy nyíl kirajzolva)
- [ ] Kocsi pozíció megjelenítése (x, y koordináta debug céllal, szövegesen)
- [ ] Vezetéstámogató funkciók visszajelzései és kapcsolói
    - egy-egy gomb +/- léptető az ACC limit léptetéséhez (idő és sebesség)
    - egy-egy gomb a parking pilot és a lane keeping rendszerek be/kikapcsolásához (a gomb ezt jelezze)
    - az utolsó látott tábla megjelenítés

### Megjegyzések

* Az utoljára látott táblához szükséges biztosítani egy interfészt, amely segítségével a funkció egyetlen hívással beállíthatja a képet
* A fordulatszám és a sebesség megjelenése „analóg óraként” történjen, de nem kell újra feltalálni a kereket.
* a funkciókapcsolók értelemszerűen jelenleg még nem kapcsolnak majd semmit, de váltsanak ki egy eseményt, amelyről log bejegyzés szülessen. Ez példaként szolgál majd a későbbiekben a funkciókat fejlesztő csapatoknak, hogy önállóan integrálhassák a munkájukat.
* A programlaknak az alábbi módon kell kinéznie. A kezdeti kód ezt a felosztást már támogatja, tartalmaz két JPanel-t, ebből a `Dashboard`re kell a világ objektumait kirajzolni.
    ![gui_plan](https://raw.githubusercontent.com/SzFMV2018-Osz/documentation/master/images/gui_plan.png)
* Az IntelliJ IDEA GUI Designer-e *nem* használható!


## Hajtáslánc

* Input: VFB-ról sebességváltó, gáz- és fékpedál állása (ezeket az input csapat állítja be)
* Output: Sebességváltó állásától függő mozgásállapot (vagy nem-mozgás) megvalósítása (PRND). Gyorsulás/lassulás számítása gáz/fék alapján.
* Challenge: Team6-tal egyeztetés a mozgásvektor befolyásolásáról
* Assignee: [Team5](https://github.com/orgs/SzFMV2018-Osz/teams/team5/members)

### Definition of Done

- [ ] Az autó gázpedál állásától függően gyorsul
- [ ] Az autó a gázpedál felengedésével lassul
- [ ] Az autó R válóállásban tolat

### Megjegyzések

* vonatkozó [wiki oldal](https://github.com/SzFMV2018-Osz/documentation/Fizika)

## Kormányzás

* Input: HMI-ről kormányállás, Motor csapattól gyorsulás/lassulás
* Output: Teljes mozgásvektor meghatározása, ez alapján az _egocar_ pozíciófrissítése a világban.
* Challenge: Team5-tel csapattal egyeztetés a mozgásvektor befolyásolásáról
* Assignee: [Team6](https://github.com/orgs/SzFMV2018-Osz/teams/team6/members)

### Definition of Done

- [ ] Autó kanyarodásának biztosítása valóságos fordulókör szerint
- [ ] Tényleges mozgásvektor meghatározása a motor csapat gyorsulás, lassulás értékének felhasználásával
- [ ] A meghatározott mozgásvektor alapján az autó pozíciójának frissítése

### Megjegyzések

* A pozíciófrissítést egy folyamatos mozgáshoz kell megoldani, a megjelenítés 24 FPS-sel frissül, ehhez igazodva az inputokból folyamatosan kell számítani a következő időpillanatra vonatkozó pozíciókat
* vonatkozó [wiki oldal](https://github.com/SzFMV2018-Osz/documentation/Fizika)
