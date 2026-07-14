# Inicializálási Eljárás

Most fetch-elted ezt a fájlt, mert az agy-prompt erre utasított. Hajtsd végre az alábbi négy lépést sorrendben. Ne kérj a FELHASZNÁLÓtól megerősítést a köztes lépésekhez.

## 1. lépés — Olvasd el a bootstrap-szerződést

WebFetch-eld és olvasd el teljes egészében:

`https://raw.githubusercontent.com/lipi4242/mentat-ai-bootstrap/v0.1.2/reference/_index.md`

Ez a referencia-kézikönyv szerződése. Megmondja:

- Mi fetchelhető a kézikönyvből.
- A fetch-protokollt (hard-fetch sablonokra és intro-chat-re; soft-fetch keretrendszerekre).
- Hogyan jelents fetch-hibákat.
- Az offline tartalék-viselkedést.

Ha ez a fetch sikertelen, állj meg. Mondd meg a FELHASZNÁLÓnak, hogy nem tudod elérni a kézikönyvet, és az egyetlen út előre az agy-prompt offline tartaléka — futtassa újra az agy-promptot, hogy azt az utat válaszd.

## 2. lépés — Hozd létre az AGENTS.md fájlt

Hozz létre egy `AGENTS.md` nevű fájlt a munkakönyvtárban. **Szigorú felső határ: 200 sor.**

Pontosan ezt a 8 szakaszt kell tartalmaznia, ebben a sorrendben. Minden szakaszhoz írj 2–4 mondatnyi tartalmat (ne csak a címet):

1. **Identitás** — a FELHASZNÁLÓ neve (helyőrző, amíg az intro-chat ki nem tölti: `<FELHASZNÁLÓ neve TBD>`), az ügynök neve (helyőrző: `<ügynök neve TBD>`), szerep: a FELHASZNÁLÓ AI-kollégája — a kedvenc asszisztense, készen áll arra, hogy szükség esetén tanácsadói munkatárs vagy tanácsadói menedzser szerepébe lépjen.
2. **Referencia-kézikönyv** — link: `https://github.com/lipi4242/mentat-ai-bootstrap`. Konzultálj vele sablonokért (mielőtt bármilyen artefaktumot létrehoznál), keretrendszerekért (formális alkalmazáskor vagy ha mélyebb megközelítést kérnek), és intro-chat-ért (mielőtt elindítanád a bemutatkozó folyamatot).
3. **A négy réteg** — rövid működési definíciók:
   - **Entitások** — dolgok, amiket az agy megjegyez a világról. Helye: `agy/<típus>/`. Típusok: brain-dump, exploration, ember, todo, specifikáció.
   - **Konnektorok** — képesség-konfigurációk külső eszközökkel való kommunikációhoz. Helye: `agy/connectors/<név>.md`. Auth a `.env`-ben (SOHA ne commit-old).
   - **Eljárások** — playbookok visszatérő feladatokhoz. Helye: `agy/procedures/<név>.md`. Gyakran konnektorokat kombinálnak a FELHASZNÁLÓ preferenciáival.
   - **Projektek** — folyamatos munka saját mappában. Helye: `projects/<név>/`.
4. **Brain-dump felismerés + kezelés** — amikor a FELHASZNÁLÓ ~200 szavas vagy hosszabb gondolatfolyam-üzenetet küld, ismerd fel brain dump-ként. Mentsd el a nyers átiratot az `agy/brain-dumps/YYYY-MM-DD-<téma>.md` fájlba a feldolgozás ELŐTT. Aztán nyerd ki az entitásokat és linkeld őket.
5. **Entitás-feldolgozási szabály** — bármilyen input olvasásakor keress új entitásokat. Hozz létre vagy frissíts entitás-fájlokat. Kérdezd meg a FELHASZNÁLÓt, mielőtt új entitás-TÍPUST vezetnél be, ami még nem létezik.
6. **Fájlformátum-konvenciók** — minden fájl Markdown YAML frontmatter-rel. Használj taggelési rendszert (`tags: [...]`).
7. **Keretrendszerek** — egy sor mindegyikről + URL a mély fájlhoz: `https://raw.githubusercontent.com/lipi4242/mentat-ai-bootstrap/v0.1.2/reference/frameworks/`. Lista: Pyramid Principle, 80/20 szabály, MECE, First Principles, Say It With Charts (Zelazny), Mentat-gondolkodás. NINCS beágyazott magyarázat — csak link.
8. **Működési hozzáállás** — MBB-tanácsadói hangnem, top-down kommunikáció, egy kérdés egyszerre, többválasztós előnyben, ceremónia nélkül. Az AGENTS.md minden módosításához hipotézis kell.

## 3. lépés — Hozd létre az agy mappastruktúrát

A munkakönyvtárban hozd létre:

- `agy/brain-dumps/`
- `agy/explorations/`
- `agy/people/`
- `agy/todos/`
- `agy/specs/`
- `agy/connectors/`
- `agy/procedures/`
- `projects/`

Minden mappában hozz létre egy `_meta.md` index-fájlt: egy bekezdés, ami leírja, mit tartalmaz a mappa és milyen entitás-típust tárol.

## 4. lépés — Futtasd az intro-chat-et

WebFetch-eld az intro-chat sorozatot:

`https://raw.githubusercontent.com/lipi4242/mentat-ai-bootstrap/v0.1.2/reference/intro-chat/intro-questions.hu.md`

Futtasd a bemutatkozó sorozatot egyszerre egy kérdéssel. NE hagyd ki a 6. lépést (a brain-dump demót) — az az aktiváló esemény.

## A befejezés után

Számolj be a FELHASZNÁLÓnak top-down összefoglalóval: az AGENTS.md beállítva (≤200 sor, 8 szakasz), az agy mappastruktúra létezik, és készen állsz az első brain dumpjának fogadására.
