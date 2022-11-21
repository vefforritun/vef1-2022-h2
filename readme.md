# Vefforritun 1, 2022, hópverkefni 2

Verkefnið felst í að útbúa vef sem birtir viðburði (eða, endurgera dagskrárvef Menningarnætur sjá þó nánar í yfirferð um útlit).

Vefur skal vera prófaður og virka í nýjustu útgáfum af Firefox og Chrome.

## Verkefnalýsing

### Gögn

Gefin eru gögn sem sótt eru frá [dagskrárvef Menningarnætur 2022](https://menningarnott.is/dagskra), sér í lagi frá [vefþjónustu fyrir þau](https://hvirfill.reykjavik.is/find?search=&all=menningarnott.is&range=2022-08-20%2C2022-08-20&limit=30&offset=0&sort=start&lang=is) sem [skaffar það JSON skjal](https://hvirfill.reykjavik.is/find?all=menningarnott.is&format=json&lang=is&limit=30&offset=0&range=2022-08-20%2C2022-08-20&search=&sort=start) sem gefið er. Þar sem ekki eru skilgreindir CORS headerar er ekki hægt að sækja gögnin beint svo nota skal gefið JSON skjal.

Gögnin eru í JSON skrá sem inniheldur lista af viðburðum. Hver viðburður er lýst með slatta af gögnum en það sem birta skal er a.m.k.:

* Lýsing á viðburði á íslensku eða ensku, ekki er krafa að nota bæði
  * `title`, `text` og `place`
* Tími viðburðar, `start` og `end`, birta ætti sem t.d. `20. ágúst 2022 kl. 20:00`
* Mynd af viðburði, en þar sem myndir eru hýstar á öðrum vef, skal nota handahófskenndamynd (t.d. með [picsum.photos](https://picsum.photos/) eða með því að vista myndir frá vefnum í `images` möppu og nota þær)
* `location` er staðsetning viðburðar, birta ætti hana á korti, sjá neðar

Leyfilegt er að birta fleiri gögn, t.d. `tags`, `meda.website` eða `media.facebook`.

Leyfilegt er að nota önnur gögn en þau sem gefin eru, t.d. finna aðra viðburði á vefnum eða búa til einhver gervigögn en þau þurfa að innihalda a.m.k. það sem lýst er að ofan og geta útfært það sem lýst er neðar.

Þegar vefur er opnaður skal sækja gögnin í JSON skjalið með `fetch` og vinna það sem þarf til að geta birt þau eftir því hvernig er verið að birta þau. Engar upplýsingar skulu „harðkóðaðar“ í HTML. Birta skal skilaboð á meðan gögn eru hlaðin. Athugið að ef þetta væri „alvöru“ verkefni værum við með bakenda sem myndi sjá um að skrifa út rétt gögn í HTML í byrjun.

### Yfirlitssíða

Á yfirlitssíðu skal birta alla viðburði í lista, með mynd, titli, staðsetningu og tíma. Birta skal sem sem „card“ eða sem lista, ekki er krafa að birta bæði. Sjálfgefið skal birta listann í tímaröð, þ.e.a.s. fyrst þá viðburði sem byrja (byrjuðu) fyrst.

Útfæra skal eitt af eftirfarandi:

1. _Filtering_. Hægt er að velja leið til að _filtera_ gögnin, t.d. að skrifa í `<input>` sem sýnir alla viðburði sem eiga við innslegin texta, eða að nota `<select>` til að velja `place` úr öllum þeim sem eru skilgreindir í gögnum.
2. _Sorting_. Að hægt sé að velja leið til að raða gögnum á a.m.k. tvo vegu, sjálfgefna og eitthvað annað, t.d. eftir `title` í stafrófsröð.
3. _Paging_. Birta aðeins tíu viðburði í einu, með möguleika á að fara á síðu 2, 3, 4, …, n. Þá er öllum viðburðum hlaðið inn í byrjun en síðan eru aðeins birtir tíu í einu.

### Stakur viðburður

Þegar smellt er á viðburð er hann opnaður á síðu sem birtir allar upplýsingar um hann sbr. að ofan. Þar er hægt að velja að fara aftur á yfirlitssíðuna. Síðan skal ver með auðkenni á viðburði í _querystring_, t.d. `event.html?id=1`. Sá vefur grípur hver viðburðurinn er og birtir.

Ef viðburðurinn er ekki til (id er ekki í `events.json`) eru upplýsingar um það birt.

### Kortavirkni

*Bónus virkni*

Ef útfært ætti að vera til sér kortasíða. Á þessari síðu skal birta alla viðburði sem hafa `location`. Nota skal pakka til þess, t.d. [Leaflet](https://leafletjs.com/) eða [Mapbox](https://www.mapbox.com/).

Þegar smellt er á hvern viðburð skal annaðhvort birta titil og lýsingu í „popup“ eða senda á síðu viðburðar.

### Útlit

Hægt skal vera að fara á milli yfirlitssíðu og kortasíðu. Frá stökum viðburð síðu skal hægt að fara aftur á yfirlitssíðu.

**Ekki** er krafa um að endurgera dagskrárvef Menningarnætur að öllu leiti, það má, en það er ekki krafa. **Útlit er ekki aðalatriði verkefnis**, en það skal þó vera nógu gott til að vera nothæft. Nota skal Sass og skipta því upp í skrár með stillingum/breytum.

Vefur skal vera skalanlegur og virka frá `400px` upp í a.m.k. `1200px`.

## Hópavinna

Verkefnið skal unnið í hóp með 3-4 einstaklingum. Hafið samband við kennara ef ekki er mögulegt að vinna í hóp. Hægt er að leita að félögum á slack á rásinni `#vef1-2022-h2-vantar-hop`. Ekki þarf að vera í sama hóp og í hópverkefni 1.

Notast skal við Git og GitHub. Engar zip skrár með kóða ættu að ganga á milli í hópavinnu, heldur á að „committa“ allan kóða og vinna gegnum Git.

Sjást ætti á _commit history_ að allir meðlimir hóps hafi tekið þátt í verkefni.

Útbúa ætti a.m.k. fimm Pull Request (PR) þar sem búið er að fara yfir af öðrum meðlim í hóp.

## Lýsing á verkefni

`README.md` skrá skal vera í rót verkefnis og innihalda:

* Upplýsingar um hvernig keyra skuli verkefnið
  * `npm run dev` eða `npm start`
  * `npm run lint` skal vera til staðar og keyra stylelint á Sass
* Létt lýsing á uppsetningu verkefnis, hvernig því er skipt í möppur, hvernig CSS/Sass er skipulagt og fleira sem á við
* Upplýsingar um alla sem unnu verkefni, nöfn, HÍ notendanöfn og GitHub notendanöfn

## Tæki og tól

Verkefnið skal innihalda `package.json` og `package-lock.json` sem innihalda öll notuð tól.

Þegar verkefnið er sótt verður `npm install` keyrt á undan öllum öðrum skipunum.

Setja skal upp Sass og stylelint með `stylelint-config-sass-guidelines` og `stylelint-config-standard` fyrir verkefnið.

Setja skal upp eslint með airbnb staðli.

## Mat

* 10% - Git og GitHub PR eftir forskrift
* 15% — `README` eftir forskrift, tæki og tól uppsett, vefur keyrir á Netilfy
* 25% — Útlit og skalanleiki
* 30% — Gögn sótt og birt á yfirlitssíðu með _filter_, _paging_ eða _sorting_
* 20% – Birting á stökum viðburð
* *Bónus* 10% — Kortavirkni

## Sett fyrir

Verkefni sett fyrir í fyrirlestri mánudaginn 24. október 2022.

## Skil

Einn aðili úr hóp skal skila fyrir hönd allra og skila skal í Canvas í seinasta lagi 25. nóvember.

Skil skulu innihalda:

* nöfn allra í hóp ásamt notendanafni
* slóð á verkefni keyrandi á Netlify
* slóð á **private** GitHub repo fyrir verkefni. Dæmatímakennurum skal hafa verið boðið í repo. Notendanöfn þeirra eru:
  * `MarzukIngi`
  * `Stimmikex`
  * `brynjar13`
  * `ofurtumi`
  * `BjarniHaskoli`
  * `Stulli888`

## Einkunn

Sett verða fyrir tíu minni verkefni þar sem átta bestu gilda 5% hvert, samtals 40% af lokaeinkunn.

Sett verða fyrir tvö hópverkefni þar sem hvort um sig gildir 10%, samtals 20% af lokaeinkunn.

> Útgáfa 0.2, nánar um útlit, kortavirkni er bónus
