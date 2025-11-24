# Kasutajalood (User Stories)

## Mis on kasutajalugu?

Kasutajalugu on lühike, lihtne kirjeldus toote funktsionaalsusest, mis on kirjutatud lõppkasutaja vaatenurgast. Kasutajalood aitavad mõista, mida kasutaja tahab saavutada ja miks.

## Kasutajaloo struktuur

```
Kui [kasutajaroll],
tahan ma [eesmärk/soov],
et [põhjus/kasu].
```

### Inglise keeles:

```
As a [user role],
I want to [goal/desire],
so that [benefit/value].
```

---

## Aktsepteerimiskriteeriumid (Acceptance Criteria)

Iga kasutajalugu peaks sisaldama selgeid aktsepteerimiskriteeriumeid, mis määravad, millal lugu on valmis.

### Given-When-Then formaat:

```
Given [eeldus/algolukord]
When [tegevus]
Then [oodatav tulemus]
```

---

## Kasutajalugude hindamine

### INVEST printsiibid:

- **I**ndependent (Sõltumatu) - lugu ei sõltu teistest lugudest
- **N**egotiable (Läbiräägitav) - detailid on paindlikud
- **V**aluable (Väärtuslik) - annab kasutajale väärtust
- **E**stimable (Hinnatav) - saab hinnata ajakulu
- **S**mall (Väike) - mahub ühte sprinditesse
- **T**estable (Testitav) - saab kontrollida valmidust

### Story Points

- **1 punkt** - väga lihtne ülesanne (1-2 tundi)
- **2 punkti** - lihtne ülesanne (2-4 tundi)
- **3 punkti** - keskmine ülesanne (4-8 tundi)
- **5 punkti** - keeruline ülesanne (1-2 päeva)
- **8 punkti** - väga keeruline (3-5 päeva)
- **13+ punkti** - liiga suur, tuleks jagada väiksemateks

---

## Näited

### Näide 1: E-poe kasutajalugu

**Kasutajalugu:**

```
Kui veebipoodi külastav klient,
tahan ma tooteid ostukorvi lisada,
et saaksin hiljem oma valiku üle vaadata ja tellimuse sooritada.
```

**Aktsepteerimiskriteeriumid:**

- Given kasutaja on tooteleheküljel
- When kasutaja klikib "Lisa ostukorvi" nupule
- Then toode lisatakse ostukorvi ja kasutajale kuvatakse kinnitusteade

- Given kasutajal on ostukorvis tooteid
- When kasutaja navigeerib teisele lehele
- Then ostukorvi sisu säilib

**Prioriteet:** Kõrge  
**Story Points:** 3  
**Sprint:** Sprint 2

---

### Näide 2: Mobiilirakenduse kasutajalugu

**Kasutajalugu:**

```
Kui registreeritud kasutaja,
tahan ma oma profiilipilti muuta,
et saaksin oma kontot personaliseerida.
```

**Aktsepteerimiskriteeriumid:**

- Given kasutaja on sisse logitud
- When kasutaja avab profiiliseaded ja valib uue pildi
- Then profiilipilt uuendatakse ja kuvatakse kohe kõikides vaadetes

- Given kasutaja üritab üles laadida liiga suurt faili (>5MB)
- When kasutaja valib pildi
- Then kuvatakse veateade lubatud failisuuruse kohta

**Prioriteet:** Keskmine  
**Story Points:** 2  
**Sprint:** Sprint 3

---

### Näide 3: Administraatori kasutajalugu

**Kasutajalugu:**

```
Kui süsteemi administraator,
tahan ma näha kasutajate aktiivsuse raportit,
et saaksin jälgida platvormi kasutust ja tuvastada probleeme.
```

**Aktsepteerimiskriteeriumid:**

- Given administraator on sisse logitud
- When administraator avab analüütika sektsiooni
- Then kuvatakse viimase 30 päeva kasutajaaktiivsus graafiliselt

- Given administraator valib kuupäevavahemiku
- When administraator klikib "Filtreeri"
- Then raport uuendatakse valitud perioodi andmetega

- Given raportis on andmeid
- When administraator klikib "Ekspordi"
- Then andmed laetakse alla CSV formaadis

**Prioriteet:** Keskmine  
**Story Points:** 5  
**Sprint:** Sprint 4

---

### Näide 4: API integratsioon

**Kasutajalugu:**

```
Kui süsteemi arendaja,
tahan ma kasutada RESTful API-t klientide andmete pärimiseks,
et saaksin integreerida andmed kolmanda osapoole süsteemidega.
```

**Aktsepteerimiskriteeriumid:**

- Given arendajal on API võti
- When arendaja saadab GET päringu /api/customers endpoint'ile
- Then tagastatakse JSON formaadis klientide loend

- Given autentimine ebaõnnestub
- When arendaja saadab päringu ilma kehtiva API võtmeta
- Then tagastatakse 401 Unauthorized vastus

**Prioriteet:** Kõrge  
**Story Points:** 8  
**Sprint:** Sprint 2

---

## Kasutajalugude kirjutamise parimad praktikad

### ✅ Tee nii:

- Kasuta lihtsat ja selget keelt
- Keskendu kasutaja vajadustele, mitte tehnilisele lahendusele
- Hoia lood väikesed ja hallatavad
- Lisa alati aktsepteerimiskriteeriumid
- Kaasa kasutajaid lugude kirjutamisse

### ❌ Väldi seda:

- Tehnilise žargooni kasutamine
- Liiga suured ja keerulised lood
- Ebaselged või mitmetähenduslikud kirjeldused
- Aktsepteerimiskriteeriumide puudumine
- Kasutaja väärtuse ignoreerimine

---

## Mall uue kasutajaloo jaoks

```markdown
### Pealkiri: [Lühike kirjeldav pealkiri]

**Kasutajalugu:**
Kui [kasutajaroll],
tahan ma [eesmärk],
et [põhjus/kasu].

**Aktsepteerimiskriteeriumid:**

- Given [eeldus]
- When [tegevus]
- Then [tulemus]

- Given [eeldus]
- When [tegevus]
- Then [tulemus]

**Prioriteet:** [Kõrge/Keskmine/Madal]
**Story Points:** [1/2/3/5/8/13]
**Sprint:** [Sprint number või Backlog]
**Määratud:** [Meeskonnaliige]
**Staatus:** [Backlog/In Progress/Review/Done]

**Märkused:**
[Lisainformatsioon, tehnilised detailid, lingid]
```

---

## Kasutajalugude haldamine

### Backlog prioritiseerimine

1. **Must Have** - kriitilised funktsioonid
2. **Should Have** - olulised, aga mitte kriitilised
3. **Could Have** - soovitavad funktsioonid
4. **Won't Have** - praegu välistatud

### Definition of Done (DoD)

- [ ] Kood on kirjutatud ja testitud
- [ ] Kõik aktsepteerimiskriteeriumid on täidetud
- [ ] Unit testid on kirjutatud ja läbivad
- [ ] Kood on peer review'd
- [ ] Dokumentatsioon on uuendatud
- [ ] Kasutajaliides on UX/UI nõuetele vastav
- [ ] QA testimine on läbitud

---

## Viited ja ressursid

- Mike Cohn - "User Stories Applied"
- Jeff Patton - "User Story Mapping"
- Scrum.org kasutajalugude juhendid
- Atlassian Agile Coach

---

**Viimati uuendatud:** 24. november 2025
