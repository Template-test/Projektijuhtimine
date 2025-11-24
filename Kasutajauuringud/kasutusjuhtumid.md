# Kasutusjuhtumid (Use Cases)

## Mis on kasutusjuhtum?

Kasutusjuhtum (Use Case) on detailne kirjeldus sellest, kuidas kasutaja (või süsteem) suhtleb süsteemiga konkreetse eesmärgi saavutamiseks. See keskendub funktsionaalsusele ja kasutaja-süsteemi interaktsioonile.

## Miks kasutada kasutusjuhtumeid?

- **Nõuete määratlemine** - Aitab mõista, mida süsteem peab tegema
- **Funktsionaalsuse kirjeldamine** - Detailne kirjeldus iga funktsiooni kohta
- **Testimise planeerimine** - Annab aluse testistsenaariumidele
- **Arenduse suunamine** - Juhib arendusprotsessi
- **Kommunikatsioon** - Loob ühise keele sidusrühmade vahel

---

## Kasutusjuhtumi elemendid

### 1. Põhiinfo

- **Kasutusjuhtumi ID** - Unikaalne identifikaator
- **Nimi** - Lühike, kirjeldav nimetus
- **Kirjeldus** - Üldine ülevaade
- **Aktor(id)** - Kes süsteemiga suhtleb?
- **Eeltingimused** - Mis peab olema täidetud enne?
- **Järeltingimused** - Mis on tulemus pärast?

### 2. Peamine voog (Main Flow)

- Samm-sammult kirjeldus tüüpilisest tegevusest
- Numbrites järjestatud sammud
- Selge ja konkreetne

### 3. Alternatiivsed vood (Alternative Flows)

- Erinevad teed sama eesmärgi saavutamiseks
- Valikulised toimingud

### 4. Erandid (Exceptions)

- Veaolukorrad
- Ebaõnnestumised
- Kuidas süsteem reageerib?

---

## Kasutusjuhtumi mall 1: E-kaubandus

### UC-001: Toote ostmine

#### Põhiinfo

- **Kasutusjuhtumi ID:** UC-001
- **Nimi:** Toote ostmine
- **Kirjeldus:** Klient soovib osta toote veebipoes
- **Aktorid:**
  - Esmane: Registreeritud klient
  - Sekundaarne: Maksesüsteem, Laosüsteem
- **Prioriteet:** Kõrge
- **Keerukus:** Keskmine
- **Eeltingimused:**
  - Klient on sisse loginud
  - Toode on laos olemas
  - Kliendil on kehtiv makseviis
- **Järeltingimused:**
  - Tellimus on loodud
  - Makse on tehtud
  - Toode on reserveeritud
  - Klient on saanud kinnituse

---

#### Peamine voog

1. Klient sirvib tootekataloogis
2. Klient valib soovitud toote
3. Süsteem kuvab toote detailse info (pilt, kirjeldus, hind, arvustused)
4. Klient valib toote variandi (suurus, värv jne)
5. Klient klikib "Lisa ostukorvi"
6. Süsteem lisab toote ostukorvi ja kuvab kinnituse
7. Klient klikib "Mine kassasse"
8. Süsteem kuvab ostukorvi sisu ja kogusumma
9. Klient kontrollib tellimust
10. Klient klikib "Jätka ostuga"
11. Süsteem kuvab tarneaadressi vormi
12. Klient sisestab või kinnitab tarneaadressi
13. Süsteem kuvab tarneviisi valikud
14. Klient valib tarneviisi
15. Süsteem kuvab makseviisi valikud
16. Klient valib makseviisi
17. Klient sisestab makseandmed
18. Süsteem suunab maksesüsteemi
19. Maksesüsteem töötleb makse
20. Maksesüsteem kinnitab makse
21. Süsteem loob tellimuse
22. Süsteem vähendab laoseisu
23. Süsteem saadab kinnituse e-posti
24. Süsteem kuvab tellimuse kinnituse lehe
25. Kasutusjuhtum lõpeb

---

#### Alternatiivsed vood

**A1: Kiire ost (Step 6)**

- 6a. Klient klikib "Osta kohe"
- 6b. Süsteem jätab vahele ostukorvi ja suunab otse kassasse
- 6c. Jätkub sammust 11

**A2: Guest checkout (Step 1)**

- 1a. Klient pole sisse loginud
- 1b. Süsteem pakub "Jätka külalisena" võimalust
- 1c. Klient valib külalisena jätkamise
- 1d. Jätkub sammust 2

**A3: Sooduskood (Step 10)**

- 10a. Klient klikib "Lisa sooduskood"
- 10b. Süsteem kuvab sooduskoodi välja
- 10c. Klient sisestab sooduskoodi
- 10d. Süsteem valideerib koodi
- 10e. Süsteem rakendab allahindlust
- 10f. Süsteem uuendab kogusummat
- 10g. Jätkub sammust 10

**A4: Salvestatud makseandmed (Step 17)**

- 17a. Kliendil on salvestatud makseviis
- 17b. Süsteem kuvab salvestatud kaardid
- 17c. Klient valib salvestatud kaardi
- 17d. Jätkub sammust 18

---

#### Erandid

**E1: Toode ei ole enam laos (Step 6)**

- 6e1. Süsteem tuvastab, et toode on otsas
- 6e2. Süsteem kuvab veateate "Kahjuks on see toode hetkel otsas"
- 6e3. Süsteem pakub alternatiive või "Teavita mind" võimalust
- 6e4. Kasutusjuhtum lõpeb

**E2: Kehtetu tarneaadress (Step 12)**

- 12e1. Süsteem valideerib aadressi
- 12e2. Aadress on puudulik või kehtetu
- 12e3. Süsteem kuvab veateate konkreetsete vigade kohta
- 12e4. Klient parandab aadressi
- 12e5. Jätkub sammust 12

**E3: Makse ebaõnnestub (Step 20)**

- 20e1. Maksesüsteem tagastab vea (nt ebapiisav saldo)
- 20e2. Süsteem kuvab veateate
- 20e3. Süsteem pakub alternatiivset makseviisi
- 20e4. Klient valib uue makseviisi
- 20e5. Jätkub sammust 17

**E4: Sessiooni aegumine (Igal sammul)**

- Xe1. Kasutaja sessioon on aegunud
- Xe2. Süsteem kuvab "Sessioon aegus" teate
- Xe3. Süsteem suunab login-lehele
- Xe4. Süsteem säilitab ostukorvi
- Xe5. Pärast sisselogimist jätkub katkestatud kohast

---

#### Ärireeglid

- Minimaalne tellimuse väärtus: 10€
- Tasuta kohaletoimetamine tellimustele üle 50€
- Maksimum 10 sama toodet ostukorvis
- Sooduskoodid ei ole kombineeritavad
- Tagastamine lubatud 14 päeva jooksul

#### Mitte-funktsionaalsed nõuded

- Lehe laadimisaeg: max 2 sekundit
- Makse protsess: max 30 sekundit
- Süsteem peab töötama 99.9% ajast
- SSL krüpteerimine kõigile lehekülgedele
- GDPR nõuetele vastavus

---

## Kasutusjuhtumi mall 2: SaaS Rakendus

### UC-015: Projekti loomine ja meeskonna määramine

#### Põhiinfo

- **Kasutusjuhtumi ID:** UC-015
- **Nimi:** Projekti loomine ja meeskonna määramine
- **Kirjeldus:** Projektijuht loob uue projekti ja määrab sellele meeskonnaliikmed
- **Aktorid:**
  - Esmane: Projektijuht
  - Sekundaarne: Meeskonnaliikmed, Teavitussüsteem
- **Prioriteet:** Kõrge
- **Keerukus:** Keskmine
- **Eeltingimused:**
  - Kasutaja on sisselogitud
  - Kasutajal on "Projektijuhi" õigused
  - Organisatsioonis on olemas kasutajad
- **Järeltingimused:**
  - Uus projekt on loodud
  - Meeskonnaliikmed on määratud
  - Teavitused on saadetud
  - Projekt on nähtav meeskonnale

---

#### Peamine voog

1. Projektijuht navigeerib "Projektid" lehele
2. Projektijuht klikib "Uus projekt" nupul
3. Süsteem kuvab projekti loomise vormi
4. Projektijuht sisestab projekti nime
5. Projektijuht sisestab projekti kirjelduse
6. Projektijuht valib projekti kategooria
7. Projektijuht seab projekti algus- ja lõppkuupäeva
8. Projektijuht valib projekti prioriteedi (Madal/Keskmine/Kõrge)
9. Projektijuht klikib "Edasi: Lisa meeskond"
10. Süsteem salvestab projekti põhiandmed
11. Süsteem kuvab meeskonna lisamise lehekülje
12. Projektijuht otsib meeskonnaliikmeid nime järgi
13. Süsteem kuvab sobivad kasutajad
14. Projektijuht valib kasutaja
15. Projektijuht määrab kasutajale rolli (Juht/Liige/Vaatleja)
16. Süsteem lisab kasutaja projekti meeskonda
17. Projektijuht kordab samme 12-16 kõigi liikmetega
18. Projektijuht klikib "Loo projekt"
19. Süsteem valideerib sisestatud andmed
20. Süsteem loob projekti
21. Süsteem saadab teavitused meeskonnaliikmetele
22. Süsteem kuvab projekti lehekülge
23. Süsteem kuvab õnnestumise teate "Projekt loodud!"
24. Kasutusjuhtum lõpeb

---

#### Alternatiivsed vood

**A1: Projekti mall (Step 3)**

- 3a. Projektijuht klikib "Kasuta malli"
- 3b. Süsteem kuvab saadaolevad mallid
- 3c. Projektijuht valib malli
- 3d. Süsteem täidab vormi malli andmetega
- 3e. Jätkub sammust 4

**A2: Import meeskonda teisest projektist (Step 12)**

- 12a. Projektijuht klikib "Impordi teisest projektist"
- 12b. Süsteem kuvab projektide loendi
- 12c. Projektijuht valib projekti
- 12d. Süsteem lisab kõik meeskonnaliikmed
- 12d. Jätkub sammust 18

**A3: Kutsu väline kasutaja (Step 14)**

- 14a. Kasutajat ei leita süsteemist
- 14b. Projektijuht klikib "Kutsu e-postiga"
- 14c. Süsteem kuvab kutse vormi
- 14d. Projektijuht sisestab e-posti aadressi
- 14e. Süsteem saadab kutse
- 14f. Jätkub sammust 17

---

#### Erandid

**E1: Duplikaat projekti nimi (Step 19)**

- 19e1. Süsteem tuvastab, et projekti nimi on juba olemas
- 19e2. Süsteem kuvab veateate "Selle nimega projekt on juba olemas"
- 19e3. Süsteem fookustab projekti nime väljale
- 19e4. Projektijuht muudab nime
- 19e5. Jätkub sammust 18

**E2: Puuduvad kohustuslikud väljad (Step 19)**

- 19e1. Süsteem tuvastab tühjad kohustuslikud väljad
- 19e2. Süsteem kuvab veateate ja märgib puuduvad väljad punasega
- 19e3. Projektijuht täidab puuduvad väljad
- 19e4. Jätkub sammust 18

**E3: Kehtetu kuupäev (Step 19)**

- 19e1. Lõppkuupäev on enne alguskuupäeva
- 19e2. Süsteem kuvab veateate "Lõppkuupäev peab olema pärast alguskuupäeva"
- 19e3. Projektijuht parandab kuupäevi
- 19e4. Jätkub sammust 18

**E4: Pole õigusi (Step 1)**

- 1e1. Kasutajal pole projektide loomise õigust
- 1e2. Süsteem kuvab veateate "Sul pole õigust projekte luua"
- 1e3. Süsteem peidab "Uus projekt" nupu
- 1e4. Kasutusjuhtum lõpeb

**E5: Teavituste saatmine ebaõnnestub (Step 21)**

- 21e1. E-posti server ei ole kättesaadav
- 21e2. Süsteem logib vea
- 21e3. Süsteem lisab teavitused järjekorda uuesti saatmiseks
- 21e4. Süsteem jätkab sammust 22 (projekt on loodud)

---

#### Ärireeglid

- Projekt peab omama vähemalt ühte meeskonnaliiget
- Projekti nimi peab olema unikaalne organisatsiooni piires
- Maksimum 100 meeskonnaliiget projekti kohta
- Lõppkuupäev peab olema alguskuupäevast hiljem
- Ainult kasutajad rolliga "Projektijuht" saavad projekte luua

#### Mitte-funktsionaalsed nõuded

- Vormi valideerimise aeg: max 1 sekund
- Projekti loomise aeg: max 3 sekundit
- Teavituste saatmine: max 10 sekundit
- Kasutajaliides peab toetama 1000+ kasutaja otsimist
- Andmete krüpteerimine serveris ja ülekandevõrgus

---

## Kasutusjuhtumi mall 3: Mobiilirakendus

### UC-023: Treeningu loggemine

#### Põhiinfo

- **Kasutusjuhtumi ID:** UC-023
- **Nimi:** Treeningu loggemine
- **Kirjeldus:** Kasutaja logib oma treeningu ja jälgib progressi
- **Aktorid:**
  - Esmane: Rakenduse kasutaja
  - Sekundaarne: Apple Health, Google Fit
- **Prioriteet:** Kõrge
- **Keerukus:** Keskmine
- **Eeltingimused:**
  - Kasutaja on rakenduses registreeritud
  - Rakendus on installitud
  - GPS ja liikumisandurid on lubatud (valikuline)
- **Järeltingimused:**
  - Treening on salvestatud
  - Progress on uuendatud
  - Statistika on uuendatud
  - Soovitused on genereeritud

---

#### Peamine voog

1. Kasutaja avab rakenduse
2. Kasutaja navigeerib "Treeningud" sektsiooni
3. Kasutaja klikib "Alusta treeningut"
4. Süsteem kuvab treeningu tüüpide nimekirja
5. Kasutaja valib treeningu tüübi (nt Jooksmine)
6. Süsteem kuvab treeningu seadistusi
7. Kasutaja seab eesmärgi (distants, aeg või kalorid)
8. Kasutaja klikib "Alusta"
9. Süsteem alustab taimeri
10. Süsteem alustab GPS jälgimist (kui lubatud)
11. Süsteem kuvab reaalajas statistikat (aeg, kiirus, distants)
12. Kasutaja teostab treeningut
13. Kasutaja klikib "Lõpeta"
14. Süsteem peatab taimeri ja GPS-i
15. Süsteem arvutab treeningu tulemused
16. Süsteem kuvab treeningu kokkuvõtte
17. Kasutaja vaatab tulemusi
18. Kasutaja klikib "Salvesta"
19. Süsteem salvestab treeningu andmebaasi
20. Süsteem uuendab kasutaja statistikat
21. Süsteem arvutab põletatud kalorid
22. Süsteem kontrollib saavutusi (achievements)
23. Süsteem kuvab saavutuse, kui teenitud
24. Süsteem küsib "Jaga sotsiaalmeediasse?"
25. Kasutusjuhtum lõpeb

---

#### Alternatiivsed vood

**A1: Kiire start (Step 4)**

- 4a. Kasutaja valib "Korda viimast"
- 4b. Süsteem laadib viimase treeningu seadistused
- 4c. Jätkub sammust 8

**A2: Paus treeningu ajal (Step 12)**

- 12a. Kasutaja klikib "Paus"
- 12b. Süsteem peatab taimeri ja jälgimise
- 12c. Kasutaja puhkab
- 12d. Kasutaja klikib "Jätka"
- 12e. Süsteem jätkab taimeri ja jälgimise
- 12f. Jätkub sammust 12

**A3: Muusika kuulamine (Step 8)**

- 8a. Kasutaja klikib "Lisa muusika"
- 8b. Süsteem näitab esitusloende
- 8c. Kasutaja valib esitusloendit
- 8d. Süsteem alustab muusika esitamist
- 8e. Jätkub sammust 8

**A4: Jagamine sotsiaalmeediasse (Step 24)**

- 24a. Kasutaja valib "Jah, jaga"
- 24b. Süsteem genereerib jagamisgraafika
- 24c. Süsteem kuvab sotsiaalmeedia valikud
- 24d. Kasutaja valib platvormi
- 24e. Süsteem avab jagamise liidese
- 24f. Kasutaja jagab postitust
- 24g. Jätkub sammust 25

**A5: Sync wearable'iga (Step 10)**

- 10a. Apple Watch / Fitbit on ühendatud
- 10b. Süsteem sünkroneerib andmed seadmelt
- 10c. Süsteem kuvab südame löögisagedust
- 10d. Jätkub sammust 11

---

#### Erandid

**E1: GPS pole saadaval (Step 10)**

- 10e1. Seade ei luba GPS-i kasutada
- 10e2. Süsteem kuvab hoiatuse "GPS pole lubatud"
- 10e3. Süsteem pakub "Jätka ilma GPS-ta" või "Luba GPS"
- 10e4a. Kasutaja lubab GPS-i → Jätkub sammust 10
- 10e4b. Kasutaja jätkab ilma → Jätkub sammust 11 (ilma distantsi mõõtmiseta)

**E2: Madal aku (Step 8)**

- 8e1. Seadme aku on alla 10%
- 8e2. Süsteem kuvab hoiatuse "Madal aku, soovitatakse laadida"
- 8e3. Kasutaja otsustab jätkata või tühistada
- 8e4a. Jätka → Jätkub sammust 8
- 8e4b. Tühista → Kasutusjuhtum lõpeb

**E3: Ühendus kadunud (Step 19)**

- 19e1. Internetiühendus puudub
- 19e2. Süsteem salvestab andmed kohalikult
- 19e3. Süsteem kuvab "Salvestatud lokaalselt, sünkitakse hiljem"
- 19e4. Süsteem proovib uuesti, kui ühendus taastub
- 19e5. Jätkub sammust 25

**E4: Rakendus crashib (Step 12)**

- 12e1. Rakendus ootamatult sulgub
- 12e2. Süsteem salvestab viimaseid andmeid kohalikult
- 12e3. Kasutaja avab rakenduse uuesti
- 12e4. Süsteem kuvab "Soovid jätkata katkestatud treeningut?"
- 12e5a. Jah → Taastab treeningu sammust 12
- 12e5b. Ei → Kasutusjuhtum lõpeb

---

#### Ärireeglid

- Minimaalne treeningu kestus: 1 minut
- Maksimaalne treeningu kestus: 12 tundi
- Kalorite arvutamine põhineb kasutaja andmetel (vanus, kaal, sugu)
- Treeningut ei saa kustutada, ainult arhiveerida
- Tasuta kasutajad saavad salvestada kuni 50 treeningut

#### Mitte-funktsionaalsed nõuded

- GPS täpsus: +/- 10 meetrit
- Aku tarbimine: max 5% tunnis
- Andmete sünkroonimine: max 5 sekundit
- Rakendus peab töötama offline režiimis
- Toetab iOS 14+ ja Android 10+

---

## Kasutusjuhtumite diagramm (UML)

Kasutusjuhtumite visualiseerimiseks kasutatakse UML diagramme:

```
        ┌─────────────────┐
        │   Kasutaja      │
        └────────┬────────┘
                 │
       ┌─────────┴──────────┐
       │                    │
       ▼                    ▼
  ┌────────┐         ┌──────────┐
  │ Login  │         │  Logout  │
  └────────┘         └──────────┘
       │
       │ <<include>>
       ▼
  ┌──────────────┐
  │   Browse     │
  │   Products   │
  └──────┬───────┘
         │
         │ <<extend>>
         ▼
  ┌──────────────┐
  │   Search     │
  │   Products   │
  └──────────────┘
```

---

## Tühi kasutusjuhtumi mall

### UC-XXX: [Kasutusjuhtumi nimi]

#### Põhiinfo

- **Kasutusjuhtumi ID:** UC-XXX
- **Nimi:**
- **Kirjeldus:**
- **Aktorid:**
  - Esmane:
  - Sekundaarne:
- **Prioriteet:** [Kõrge/Keskmine/Madal]
- **Keerukus:** [Lihtne/Keskmine/Keeruline]
- **Eeltingimused:**
  -
- **Järeltingimused:**
  -

---

#### Peamine voog

1.
2.
3. ...

---

#### Alternatiivsed vood

**A1: [Alternatiivi nimi] (Step X)**

- Xa.
- Xb.
  ...

---

#### Erandid

**E1: [Erandi nimi] (Step X)**

- Xe1.
- Xe2.
  ...

---

#### Ärireeglid

-

#### Mitte-funktsionaalsed nõuded

-

---

## Kasutusjuhtumite kirjutamise parimad praktikad

### ✅ Tee nii:

- Kasuta aktiivset häält ja lihtsat keelt
- Kirjelda kasutaja eesmärki, mitte tehnoloogiat
- Hoia sammud lühikesed ja konkreetsed
- Nimeta selgelt aktorid
- Dokumenteeri kõik erandid
- Kasuta numberdatud samme
- Lisa ärireeglid

### ❌ Väldi seda:

- Tehnilise žargooni kasutamine
- Liiga detailsed UI kirjeldused
- Ebaselged sammud
- Erandite ignoreerimine
- "Kasutaja võib..." (ole konkreetne)
- Liiga palju alternatiive (hoia fookuses)

---

## Kasutusjuhtumid vs Kasutajalood

| Aspekt         | Kasutusjuhtumid        | Kasutajalood                 |
| -------------- | ---------------------- | ---------------------------- |
| **Detailsus**  | Väga detailne          | Üldine                       |
| **Pikkus**     | Pikk (leheküljed)      | Lühike (mõned laused)        |
| **Fookus**     | Süsteemi käitumine     | Kasutaja väärtus             |
| **Kasutamine** | Nõuete analüüs         | Agile development            |
| **Formaalsus** | Formaalne              | Mitteformaalne               |
| **Erandid**    | Detailselt kirjeldatud | Aktsepteerimiskriteeriumides |

**Soovitus:** Kasuta mõlemat! Kasutajalood planeerimiseks, kasutusjuhtumid detailseks spetsifikatsiooniks.

---

## Tööriistad

- **Lucidchart** - UML diagrammid
- **Draw.io** - Tasuta diagrammide tööriist
- **Enterprise Architect** - Professionaalne UML tööriist
- **Visual Paradigm** - UML ja kasutusjuhtumid
- **Confluence** - Dokumenteerimine
- **Google Docs** - Lihtne ja ligipääsetav

---

**Viimati uuendatud:** 24. november 2025
