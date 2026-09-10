# Pika të reja — rregullat e projektit

## Çfarë është
PWA për pikat POTENCIALE — lokale ku dua të vendos aparate por ende s'kanë.
Programi **Aparatet** mban pikat që KANË aparat. Kur një pikë pranon, kalon
te Aparatet dhe këtu shënohet `aktiv`.

## Modeli i biznesit (i fiksuar)
- **Përqindje:** 7% e qarkullimit (interval i zakonshëm 3–15%)
- **Fikse:** 0.25–0.35 € për pako (interval i zakonshëm 0.20–0.40 €)
- **Barazimi:** çdo 6 ose 12 muaj, sipas marrëveshjes së atij lokali

Llogaritja — formula shfaqet GJITHMONË nën rezultat:
- Përqindje: `qarkullim × vlera/100`
- Fikse: `pako × vlera` → *"1,240 pako × 0.30 € = 372.00 €"*

## Rregulla që nuk shkelen
1. **Asnjë barazim i kryer nuk ndryshohet pa gjurmë** — çdo ndryshim shkon te
   `ptr_log` me shumën e vjetër dhe të re.
2. Të gjitha shumat në euro me **dy shifra dhjetore**.
3. Punon **plotësisht offline**. Kërkimi i lokaleve është e vetmja gjë që
   kërkon internet.
4. Backup-i JSON përfshin **të gjitha** tabelat. Testo eksport → import.
5. **Ruajtja verifikohet me rilexim** — localStorage mund të "duket" i ruajtur
   pa qenë. Nëse dështon, paralajmërim i qartë.
6. Asnjë `catch(e){}` bosh. Çdo dështim duhet të shihet.

## Ruajtja
`localStorage` me prefiks `ptr_`:
- `ptr_pika` · `ptr_oferta` · `ptr_barazim` · `ptr_log`

**E rëndësishme:** localStorage lidhet me DOMENIN, jo me shtegun. Ky program
dhe Aparatet janë të dy te `luqa25.github.io`, prandaj **i ndajnë të dhënat**.
Kalimi i një pike te Aparatet bëhet duke shkruar te `apar_live_catalog`.

## Statuset
`potencial` → `oferte` → `pranuar` → `aktiv`
(ose `refuzuar` / `hequr`)

## Publikimi
GitHub Pages: `luqa25.github.io/pika-te-reja/`
Çdo ndryshim **duhet** të rrisë versionin te `sw.js` (emri i cache-it),
përndryshe telefoni mbetet me versionin e vjetër.

## Kufizim i njohur
OpenStreetMap i njeh mirë qytetet (Pejë ~33 lokale), por në **fshatra shpesh
s'ka asnjë lokal të hartuar**. Aty pikat shtohen me dorë me GPS nga terreni.
