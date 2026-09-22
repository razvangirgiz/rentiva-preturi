# Prețul pieței de închirieri auto în România

Prețul median pe zi, pe categoriile ACRISS, pentru închirieri de 1–3, 4–7, 8–15 și peste 15
zile, plus curba de sezon pe următoarele 12 luni. Prețurile vin din ofertele cerute pe
site-urile firmelor de închirieri, ca un client, fără rezervare. Unde o firmă nu are
rezervare online, folosim tarifele publicate pe site. Toate prețurile sunt cu TVA, în euro, și
corespund protecției cu garanția cea mai mică: 0 sau cel mult 200 €.

Cifrele se văd pe [rentiva.ro/unelte/pret-piata](https://rentiva.ro/unelte/pret-piata), care
citește fișierul `market-prices.json` de aici. Se actualizează în fiecare luni dimineață.

## Ce e în fișier

- `updatedAt`: ziua în care au fost cerute ofertele.
- `eurRon`: cursul BNR din ziua aceea, pentru firmele cu prețuri în lei.
- `firmsChecked`, `firmsUsed` și `firmsQuoted`: câte firme am verificat, câte au intrat în
  calcul și câte dintre ele prin oferte cerute pe site.
- `categories[]`: categoriile macro ACRISS (`economy`, `compact-suv`, `passenger-van-9` etc.),
  fiecare cu:
  - `label`: numele ACRISS;
  - `family`: `car`, `suv`, `mpv`, `passenger-van` sau `cargo-van`;
  - `examples`: modele din categorie;
  - `thin` și `reference`: sub 3 firme categoria e subțire, iar reperul vine din categoria
    vecină.
- `categories[].durations.{short,week,twoWeeks,long}.firmMedians`: mediana fiecărei firme pe
  categorie, în euro pe zi, fără nume de firme. Duratele sunt 2, 4, 10 și 21 de zile, cu
  ridicarea într-o zi de luni, peste cel puțin o săptămână (predarea cade în zi lucrătoare).
- `season`: pentru fiecare lună, prețul față de media anului (1 = medie), pe durate, cu vara,
  Crăciunul și Paștele marcate. Rămâne `null` până avem destule luni măsurate.

Categoria o stabilim după modelul mașinii (codul SIPP), nu după cum o numește fiecare firmă,
iar fiecare firmă contează o singură dată. Metoda completă e pe pagină, la „De unde vin
cifrele”.
