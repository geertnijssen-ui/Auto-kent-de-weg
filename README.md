# Routenet

Navigatie-app die zo veel mogelijk binnendoor rijdt: grote en drukke wegen worden vermeden, zandwegen en aardepaden vermeden; goed berijdbare grind- of halfverharde wegen waar auto's mogen komen wel (uit te zetten).

## Zo werkt het
- **Kaart:** OpenStreetMap (standaardkaart, geen sleutel nodig).
- **Routes:** de gratis publieke [Valhalla](https://valhalla.github.io/valhalla/)-server. Per rit worden drie profielen gevraagd (rustig, binnendoor, landweggetjes) plus alternatieven. Daarna "duwt" de app de route van grote wegen af: midden op lange stukken provinciale of grote weg worden kleine blokkades gezet en wordt opnieuw gerekend, tot hij door wijken en binnenbaantjes gaat (binnen je omweg-grens). Toegangsregels uit OpenStreetMap (bv. alleen landbouwverkeer) worden altijd gerespecteerd.
- **Rustscore:** van elke route wordt per stuk weg de wegklasse opgehaald. Kilometers op snelweg, autoweg en provinciale weg tellen zwaar, dorpsstraten en landwegen licht. Zo krijgt elke route een percentage "rustig", en de kaart kleurt groen, oranje of rood. N-wegen (gewestwegen) en R-ringwegen tellen altijd als grote weg, ook als ze in OpenStreetMap kleiner zijn ingetekend.
- **Soort route:** drie knoppen. *Kort & groen* (standaard): zo kort mogelijk maar binnendoor. *Groenst*: rustigste route, omweg mag. *Sneller*: snelle route, rustig waar het kan. Via-punten, vermijd-plekken en grindwegen staan onder "Meer opties".
- **Rijden via:** typ een dorp of straat bij "Rijden via…" of tik "+ Via-punt op kaart" en tik op een weg. De route gaat daar dan langs (bv. Lanaken → Rekem → Opgrimbie → Zutendaal). Tik op een blauw label om het weg te halen.
- **Drukke plek vermijden:** tik op "+ Drukke plek vermijden" en tik op de kaart. Die plek wordt voortaan omzeild (wordt op je toestel bewaard).
- **Navigeren:** GPS, gesproken Nederlandse aanwijzingen, automatisch herberekenen als je van de route afgaat, scherm blijft aan.
- **Demo-rit:** rijdt de route virtueel na om alles thuis te testen. Tik op de snelheid om sneller af te spelen.
- **Op je beginscherm zetten:** open de site op je telefoon en kies "Zet op beginscherm". Dan opent hij als een app.

## Online zetten met Netlify
1. Op netlify.com: **Add new project → Import an existing project → GitHub**.
2. Kies deze repo. Build command leeg laten, publish directory `.` (staat al in `netlify.toml`).
3. **Deploy**. Elke wijziging in deze repo komt daarna vanzelf online.

## Grenzen van dit prototype
- De publieke Valhalla-server is bedoeld voor licht gebruik en heeft geen live verkeersinformatie. "Drukke punten" worden dus bepaald door het type weg en je eigen vermijd-plekken, niet door actuele files.
- De kaart draait niet mee met je rijrichting (noorden blijft boven).
