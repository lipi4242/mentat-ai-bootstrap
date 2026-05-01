# mentat-ai-bootstrap

Állítsd fel a saját személyes AI kollégádat Claude Code + Superpowers plugin segítségével. EN/HU.

> In English: [README.md](README.md)

## Mi ez

Egy bootstrap-csomag. Körülbelül 25 perc irányított beállítás után egy működő AI kollégád lesz, aki:
- Felismeri a hosszú üzeneteket „agy-dumpként", és szó szerint elmenti őket feldolgozás előtt.
- Embereket, teendőket, feltárásokat, specifikációkat, konnektorokat, eljárásokat és projekteket strukturált Markdown fájlokként tart nyilván.
- MBB-tanácsadói stílusban kommunikál (top-down, Pyramid Principle, MECE), és Mentatként gondolkodik a Dűnéből.
- Szótár-és-forma telepítésként indul; a valódi integrációkat (Gmail, TickTick stb.) később kötheted be, amikor kéred.

## Kinek való

Mindenkinek, aki olyan személyes AI asszisztenst szeretne, aki *emlékszik* — nem egyszer használatos chat-eszközt. Nem kell technikusnak lenned, de a telepítésnél terminálban leszel.

## Telepítés

### 1. Claude Code CLI telepítése

- **macOS:** Kövesd a https://docs.claude.com/en/docs/claude-code útmutatót (Homebrew vagy telepítő). Nyisd meg a Terminált (Cmd+Space → „Terminal") vagy az iTerm-et, és ellenőrizd: `claude --version`.
- **Windows:** Először telepítsd a Git for Windows programot (https://git-scm.com/download/win), majd kövesd a Claude Code Windows telepítési útmutatóját. Nyisd meg a PowerShellt (Start menü → „PowerShell"), és ellenőrizd: `claude --version`.

### 2. Hozz létre egy mappát az asszisztensnek + nyiss benne terminált

- **macOS (Terminal vagy iTerm):**
  ```
  mkdir ~/my-assistant && cd ~/my-assistant
  ```
- **Windows (PowerShell):**
  ```
  mkdir $HOME\my-assistant; cd $HOME\my-assistant
  ```

A mappát elnevezheted, ahogy szeretnéd — a `my-assistant` csak egy példa.

### 3. Indítsd a Claude Code-ot

```
claude
```

A Claude minden fájlírás vagy shell-parancs előtt engedélyt kér. Hagyd jóvá mindegyiket — ez a biztonságos alapértelmezés.

> **Haladó (saját felelősségre):** Ha elfáradtál minden műveletet jóváhagyni, van egy alternatív indítási mód:
> ```
> claude --dangerously-skip-permissions
> ```
> Ez széleskörű hozzáférést ad a Claude-nak a rendszeredhez, beleértve a shell-parancsok explicit jóváhagyás nélküli futtatását is. **Olvasd el a Claude Code dokumentációját** arról, mit tesz lehetővé, mielőtt használnád. Csak akkor használd, ha érted és elfogadod a kockázatokat.

### 4. Telepítsd a Superpowers plugint

A Claude Code promptban írd be:

```
Please install the Superpowers plugin from https://github.com/pcvelz/superpowers
```

Várd meg a telepítés befejezését (általában kevesebb mint egy perc).

### 5. Másold be az alábbi agy-promptot

Másold ki az alábbi teljes blokkot (mindent a `<!-- BRAIN PROMPT START -->` és `<!-- BRAIN PROMPT END -->` jelölők között), és illeszd be a Claude Code promptba. Ezután nyomj Entert.

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

## Mi történik ezután

Az ágensed:
1. Letölti az inicializálási eljárást ebből a repóból.
2. Létrehozza az `AGENTS.md` fájlt és az `agy/` mappastruktúrát a mappádban.
3. Elindít egy bemutatkozó beszélgetést — neved, mit csinálsz, miben szeretnél segítséget, az ágens személyisége, végül egy agy-dump demó, ahol elmondasz valamit, amin gondolkozol, és az ágens végig feldolgozza. Ez az aktiváló pillanat.

Ha valami nem sikerül, az ágensed pontosan elmondja, mi romlott el és mit kell tenni.

## Az agy-prompt mint különálló fájl

Ugyanaz a tartalom, mint a fentebb beágyazott: [BRAIN-PROMPT.hu.md](BRAIN-PROMPT.hu.md).

## Kézikönyv

Az ágensed igény szerint mélyebb részleteket tölt le a `reference/` könyvtárból:
- [Inicializálás](reference/initialization.hu.md) — a 4 lépéses bootstrap-eljárás, amelyre az agy-prompt irányítja az ágenst.
- [Bootstrap-szerződés](reference/_index.md) — mi tölthető le és hogyan.
- [Keretrendszerek](reference/frameworks/_index.md) — Pyramid Principle, 80/20, MECE, First Principles, Zelazny „Say It With Charts", Mentat-gondolkodás.
- [Sablonok](reference/templates/_index.md) — kétnyelvű entitás-sablonok.
- [Bemutatkozó beszélgetés](reference/intro-chat/_index.md) — a kérdéssorozat.
