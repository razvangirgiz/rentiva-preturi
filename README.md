# Prețul pieței de închirieri auto, cu casco inclus

Prețul median pe zi pentru fiecare categorie de mașini, din tarifele pe care firmele de
închirieri din România le publică pe site-ul lor. Doar prețuri cu casco inclus și TVA,
pentru închirieri de 1–3 zile (`short`) și de 7 zile (`week`), în euro.

Cifrele se văd pe [rentiva.ro/unelte/pret-piata](https://rentiva.ro/unelte/pret-piata),
care citește fișierul `market-prices.json` de aici. Se actualizează în fiecare luni
dimineață.

## Ce e în fișier

- `updatedAt`: ziua în care au fost citite tarifele.
- `eurRon`: cursul BNR din ziua aceea, folosit pentru firmele care au prețuri în lei.
- `firmsChecked` / `firmsUsed`: câte firme am verificat și câte au casco inclus și tarife
  complete.
- `categories[].durations.{short,week}.firmMedians`: mediana fiecărei firme pe categorie,
  în euro pe zi, fără nume de firme. Pagina calculează din ele mediana și jumătatea din
  mijloc.

Categoria o stabilim după model, nu după eticheta firmei, iar fiecare firmă contează o
singură dată. Metoda completă e pe pagină, la „De unde vin cifrele”.
