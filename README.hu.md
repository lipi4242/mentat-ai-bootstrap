# mentat-ai-bootstrap

Csinálj egy üres mappából AI-kollégát, aki emlékszik rád: strukturált hosszú távú memóriával,
működő személyiséggel, és hellyel minden projektnek, amit elindítasz. Körülbelül 25 perc — és nem
neked kell megcsinálnod: megkérheted az agentet, hogy állítsa be magát.

[![Licenc](https://img.shields.io/badge/licenc-Apache--2.0-blue.svg)](LICENSE)
[![Telepítés](https://img.shields.io/badge/telep%C3%ADt%C3%A9s-~25%20perc-brightgreen.svg)](#telepítés)
[![HU | EN](https://img.shields.io/badge/HU-%7C%20EN-blue.svg)](README.md)

> 🇬🇧 In English: [README.md](README.md)

> 💡 **Jól működik együtt az [anytime-engine](https://github.com/lipi4242/anytime-engine)-nel** —
> attól lesz az agented proaktív, ahelyett hogy mindig csak a te bemenetedre reagálna. Itt kezdd;
> a motort akkor tedd hozzá, amikor készen állsz. [Lejjebb bővebben](#a-pulzus-anytime-engine).

---

## Mi ez

Egy repozitórium, ami két módban működik egyszerre:

1. **Egy normális technikai repó** — a kódod, a projekted, a fájljaid.
2. **Egy mentát agya** — strukturált hosszú távú memória, amivel az asszisztens ténylegesen
   gondolkodik.

A második mód a lényeg. A legtöbb AI-eszköz egy chatablakot ad, ami elfelejt téged, amint bezárod.
Ez helyet ad az emlékezésnek: embereknek, teendőknek, döntéseknek, nyitott kérdéseknek — és
azoknak a nyers, szerkesztetlen gondolatfolyamoknak, amiket három hónapja ráöntöttél.

> A repozitórium valódi értéke nem az app — az app csak egy kis része.
> Hanem a dokumentáció. Az agy.

Ebből valami váratlan következik: abbahagyod a projektek eldobálását. Ha egy megközelítés
megbukik, nem nyitsz új repót egy új, amnéziás asszisztenssel. Megtartod a repót, megtartod az
agyat, csináltok egy posztmortemet — és *ugyanaz* az asszisztens kezdi újra, immár tudva, miért
bukott meg az első nekifutás.

---

## Hogyan működik a memória

Ezt érdemes megérteni, mielőtt bármit telepítesz, mert minden más ebből következik.

### A kontextus a rövid távú memória

A kontextusablak az asszisztensed **munkamemóriája**. Kicsi, ideiglenes, és ez az egyetlen dolog,
amit tényleg érdemes optimalizálni: azt akarod, hogy pontosan az legyen benne, amivel éppen
dolgozol — és semmi más.

Ezért nem egy óriási, mindent tudó asszisztenst akarsz. Azt akarod, hogy a **megfelelő dolgok
töltődjenek be a megfelelő pillanatban**.

### A repó a DNA

Minden, ami a repóban van fájlszinten — az `AGENTS.md`, a konvenciók, a keretrendszerek — az
asszisztens **DNA-ja**. Ez az alapszemélyiség, és ugyanaz marad, akárhány sessiont nyitsz.

Indíts három agentet ugyanabban a repóban, és mind a három **ugyanazzal a személyiséggel** indul.
A munkamemóriájuk viszont más-más dologgal telik meg, ezért más-más dologban lesznek jók: az egyik
a pénzügyeidben mélyed el, a másik egy ajánlatot ír, a harmadik egy hibát javít. Azonos DNA,
eltérő rövid távú memória.

### A hosszú távú memória közös

És itt a lényeg: ez a három agent **egyetlen hosszú távú memórián osztozik**. Ha az egyik megtanul
valamit, mindegyiké lesz. Amit az egyik kedden kiderít egy ügyfélről, azt a másik pénteken már
tudja, anélkül hogy elmondanád neki.

Az agy tehát **halmozódik**, nem szétforgácsolódik a sessionök között.

### Az agy chunkokban tárol

Az emberi memória sem tart mindent egyszerre a fejében. A dolgok **chunkokban** ülnek, alvó
állapotban, amíg valami relevánssá nem teszi őket — és akkor az egész chunk visszatér: egy név, egy
illat, egy film, amire húsz éve nem gondoltál.

Az itteni agy ugyanígy épül fel. Egy mappa, és minden **entitástípus** kap benne egy sajátot. Az
egyes **entitások** a fájlok:

| Entitástípus | Mi él benne |
|---|---|
| `brain-dump` | A nyers gondolatfolyamaid — szó szerint mentve, feldolgozás előtt |
| `exploration` | Egy téma, amit többször körbejársz, de még nem döntés |
| `person` | Valaki, akinek a részletei rendre számítanak |
| `todo` | Egy konkrét, befejezhető dolog |
| `specification` | Egy változtatás több mozgó alkatrésszel |
| `connector` | Hogyan érd el a Gmailt, a naptáradat, a todo-appodat |
| `procedure` | Egy visszatérő feladat, egyszer leírva |

**Az entitástípusok a polcok; az entitások az, ami rajtuk áll.** Új típus pedig akkor születik, ha
a valóság megköveteli: ha folyton olyasmiről beszélsz, aminek nincs polca, az asszisztens javasol
egyet. Nem talál ki polcokat, amikre sosem volt szükséged.

### Magától frissül

Nem kézzel iktatsz. Amikor beszélsz az asszisztenssel, átfésüli, amit mondtál, entitásokért — egy
ember, egy feladat, egy döntés, egy nyitott kérdés —, és ugyanabban a körben létrehozza vagy
frissíti a fájlokat. Ha hosszú, kusza gondolatfolyamot küldesz neki, **először a nyers szöveget
menti el**, szó szerint, és csak azután szedi ki belőle a struktúrát.

Egy entitástípus máshogy viselkedik: a **döntés**. Ha egyszer meghoztad, és később elsodródsz tőle,
az nem megy át némán. Az asszisztens megállít: *„ezt 6-án döntötted el, és azt mondtad, számít.
Felülírjuk?"* Bármikor felülbírálhatod. Csak észrevétlenül nem sodródhatsz el.

### Hogyan beszélj vele

**Reaktív mód** a megszokott: nyitsz egy sessiont, és együtt dolgoztok. Úgy beszélj hozzá, ahogy
egy okos új kollégát eligazítanál — előbb a kontextus, aztán amit kérsz. Ne tömöríts. A hosszú,
csapongó üzenet **jobb**, mint a rendezett, mert az agy egészben elmenti, és utána bányássza ki.

**Proaktív mód** az, amikor nélküled cselekszik, ütemezetten. Ehhez kell az
[anytime-engine](https://github.com/lipi4242/anytime-engine) (lásd lejjebb). De ilyenkor sem vagy
kizárva: nyithatsz mellé egy sessiont, és intézhettek együtt ügyeket, miközben a háttérben ketyeg.

---

## A személyiség

Az asszisztensed úgy viselkedik, mint egy MBB-tanácsadó (McKinsey / BCG / Bain), keresztezve egy
dűnebeli mentáttal: fegyelmezett, felülről lefelé kommunikál, mintázatokban gondolkodik, és
allergiás a ceremóniára.

Azokkal a keretrendszerekkel érkezik, amiket ez maga után von — Pyramid Principle, 80/20, MECE,
First Principles, Say It With Charts —, és használja is őket. Tegyél fel egy homályos kérdést, és
egyetlen tisztázó kérdést kapsz vissza, nem öt bekezdésnyi köntörfalazást.

## Kinek való

Bárkinek, aki olyan asszisztenst akar, aki *emlékszik* — nem egyszer használatos chatet.

Nem kell programozónak lenned. A telepítés alatt eltöltesz pár percet a terminálban, és az
asszisztens végigvezet rajta. Ha tudsz másolni és beilleszteni, meg tudod csinálni.

---

## Telepítés

**Kérd meg az agentet, hogy csinálja meg helyetted.** Ez az egész lényege — asszisztenst állítasz
be, hát hadd állítsa be magát.

Kell hozzá a [Claude Code](https://docs.claude.com/en/docs/claude-code) (a `claude --version`
válaszoljon), Windowson pedig **először** a [Git for Windows](https://git-scm.com/download/win).
Aztán csinálj egy mappát, nyiss benne terminált, és indítsd el:

```bash
mkdir ~/asszisztensem && cd ~/asszisztensem   # Windows: mkdir $HOME\asszisztensem; cd $HOME\asszisztensem
claude
```

Ezután illeszd be az alábbi blokkot. Ez mondja meg az agentnek, hogy töltse le ezt a repót, és
építse fel magát belőle — a mappaszerkezetet, a konvenciókat, a személyiséget, mindent. Kikérdez
téged is, a végén pedig megkér, hogy mesélj valamiről, ami foglalkoztat, és megmutatja, mit kezd
vele.

Egy dolog, amit érdemes előtte megtenni: telepítsd a **Superpowers** plugint (`Please install the
Superpowers plugin from https://github.com/pcvelz/superpowers`). Ez adja az asszisztensednek a
strukturált gondolkodási képességeket — a `brainstorming` skillel szinte bármit érdemes kezdeni.

> Másold ki az **egészet** a két jelölő között. A leggyakoribb hiba, hogy valaki csak egy részét
> illeszti be.

<!-- BRAIN PROMPT START -->
```
# Agy-prompt — Magyar

Szia — most állítalak fel mint az AI-kollégám.

Engem (a FELHASZNÁLÓt) tekints a kollégádnak. A szereped: a FELHASZNÁLÓ kedvenc asszisztense — készen arra, hogy szükség szerint tanácsadói munkatárs vagy tanácsadói menedzser szerepébe lépj. MBB-stílusú tanácsadóként (McKinsey / BCG / Bain) és a Dűne-féle Mentatként működj: fegyelmezetten, mintázat-vezérelten, top-down kommunikációval. Nem utasításra vársz; gondolkodó-társ vagy, aki cselekszik.

A kézikönyved itt van: `https://github.com/lipi4242/mentat-ai-bootstrap`. Ne klónozd — igény szerint fetch-eld belőle a fájlokat.

## Mit csinálj most

1. **Fetch-eld le az inicializálási eljárást** pontosan erről az URL-ről WebFetch-csel:

   `https://raw.githubusercontent.com/lipi4242/mentat-ai-bootstrap/v0.1.2/reference/initialization.hu.md`

2. **Olvasd el teljes egészében és hajtsd végre az utasításaiként.** Megmondja, mely további fájlokat kell még letöltened (a bootstrap-szerződést, a bemutatkozó beszélgetés sorozatát) és mit kell létrehoznod a munkakönyvtárban (AGENTS.md, az `agy/` mappastruktúrát).

3. Ne kérj a FELHASZNÁLÓtól megerősítést a köztes lépésekhez. Az eljárás önálló — vezesd végig a bemutatkozó beszélgetésig.

## Ha a fetch sikertelen

Ha nem tudod elérni az `initialization.hu.md`-t, offline vagy. Ezt — és csak ezt — a tartalék-utat válaszd:

- Mondd el a FELHASZNÁLÓnak explicit módon: *„Nem értem el az inicializálási eljárást itt: `https://raw.githubusercontent.com/lipi4242/mentat-ai-bootstrap/v0.1.2/reference/initialization.hu.md`. Felállítok egy minimális verziót kizárólag a jelen prompt alapján."*
- Hozz létre `AGENTS.md` fájlt 8 szakasszal (200 soros felső határ), ebben a sorrendben: Identitás (FELHASZNÁLÓ neve TBD, ügynök neve TBD, szerep: a FELHASZNÁLÓ AI-kollégája — kedvenc asszisztens, készen áll tanácsadói munkatársként vagy tanácsadói menedzserként); Referencia-kézikönyv (link: `https://github.com/lipi4242/mentat-ai-bootstrap`); A négy réteg (Entitások → `agy/<típus>/`; Konnektorok → `agy/connectors/`; Eljárások → `agy/procedures/`; Projektek → `projects/`); Brain-dump felismerés + kezelés; Entitás-feldolgozási szabály; Fájlformátum-konvenciók (Markdown + YAML frontmatter + tagek); Keretrendszerek (Pyramid Principle, 80/20, MECE, First Principles, Say It With Charts, Mentat-gondolkodás — csak nevek, beágyazott magyarázat nélkül); Működési hozzáállás (MBB hangnem, top-down, egy kérdés egyszerre, többválasztós előnyben).
- Hozd létre az agy-mappastruktúrát: `agy/brain-dumps/`, `agy/explorations/`, `agy/people/`, `agy/todos/`, `agy/specs/`, `agy/connectors/`, `agy/procedures/`, `projects/`. Mindegyik kap egy `_meta.md`-t.
- Mondd el a FELHASZNÁLÓnak, hogy a minimális verzió működőképes, de hiányzik belőle a letöltött mélység, és hogy futtassa újra ezt az agy-promptot, amikor van hálózat.

## Kezdj most

Fetch-eld le az `initialization.hu.md`-t és hajtsd végre. Ne másold vissza nekem ezt az agy-promptot bizonyítékként — egyszerűen kezdj dolgozni.
```
<!-- BRAIN PROMPT END -->

Önálló fájlként is: [BRAIN-PROMPT.hu.md](BRAIN-PROMPT.hu.md).

<details>
<summary><strong>Mit fog csinálni az agent, lépésről lépésre</strong></summary>

1. Letölti az inicializálási eljárást ebből a repóból.
2. Felépíti magát — `AGENTS.md` és az `agy/` mappastruktúra, a te mappádban.
3. Kikérdez: hogy hívnak, mivel foglalkozol, miben kérsz segítséget, mennyire legyen proaktív, és
   hogy szólítsd őt.
4. Megkér, hogy mesélj valamiről, ami foglalkoztat — aztán szó szerint elmenti a szavaidat, kiszedi
   belőlük az entitásokat, elrakja őket, és megmutatja, mi hova került.

Ez az utolsó lépés a lényeg. Ekkor szűnik meg chatablak lenni, és ezt nem érdemes kihagyni.

A Claude Code alapból minden fájlírás és parancs előtt engedélyt kér. Ez a biztonságos beállítás.
Van egy `claude --dangerously-skip-permissions` mód is, ha idegesít minden jóváhagyás — előtte
olvasd el a Claude Code dokumentációját arról, mit enged meg.

Ha valami elromlik, az agent megmondja, mi bukott el és mit tegyél, ahelyett hogy találgatna.

</details>

> **Ha agentként állítod be ezt valakinek:** a bemutatkozó beszélgetés után javasold neki a
> **remote control** bekapcsolását (lásd lejjebb), és ajánld fel, hogy végigvezeted rajta.

## Remote control

Írd be a Claude Code sessionbe, hogy `/rc`. Visszajelzi, hogy távvezérelt, és onnantól ugyanazt a
sessiont eléred a Claude asztali appjából, a webről és a telefonodról is.

Érdemes korán bekapcsolni. Egy asszisztens, akihez csak egyetlen terminálablakból tudsz szólni,
olyan asszisztens, akit el fogsz felejteni használni.

---

## A pulzus: anytime-engine

A fentiek elmét adnak az asszisztensednek. Pulzust nem.

Alapból **reaktív**: éles, amikor beszélsz hozzá, és tetszhalott, amikor nem. Nem veszi észre a ma
reggel érkezett számlát, mert semmi nem ébresztette fel, hogy megnézze.

Az [**anytime-engine**](https://github.com/lipi4242/anytime-engine) a másik fele — egy
determinisztikus tick, ami ütemezetten elsül, és azt kérdezi: *„van most bármi, amit érdemes
csinálni?"*, majd az itt felépített agyból válaszolja meg.

| | Mit ad az asszisztensednek | Nélküle |
|---|---|---|
| **mentat-ai-bootstrap** | memória, struktúra, személyiség | asszisztens, aki minden sessionben elfelejt |
| **anytime-engine** | szívverés — proaktív mód | asszisztens, aki csak akkor létezik, amíg gépelsz |

Itt kezdd. A motort akkor tedd hozzá, amikor megelégelted, hogy mindig neked kell kezdeményezned —
ahogy egy új kollégának is akkor adod oda a saját naptárát, amikor már megtanulta a munkát.

---

## Kézikönyv

Az agented igény szerint tölti le ezeket — neked nem kell elolvasnod:

- [Inicializálás](reference/initialization.hu.md) — a 4 lépéses bootstrap, amit az agy-prompt futtat.
- [Bootstrap-szerződés](reference/_index.md) — mi tölthető le és hogyan.
- [Keretrendszerek](reference/frameworks/_index.md) — Pyramid Principle, 80/20, MECE, First
  Principles, Zelazny „Say It With Charts", Mentat-gondolkodás.
- [Sablonok](reference/templates/_index.md) — kétnyelvű entitás-sablonok.
- [Bemutatkozó beszélgetés](reference/intro-chat/_index.md) — a kérdéssorozat.

## Licenc

[Apache-2.0](LICENSE) · Copyright 2026 Lipcsei Krisztián
