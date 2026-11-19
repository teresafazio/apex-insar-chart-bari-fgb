# apex-insar-chart-bari

Esempio di configurazione per **APEx Geospatial Explorer**: cliccando su un punto InSAR si apre il grafico della serie storica dello spostamento.

Dati di test **sintetici**: 10 punti Sentinel-1 (orbita discendente) lungo la costa di Bari.

## Contenuto

- `data/output_descending.geojson` – velocità media LOS (`vel`, mm/anno) e attributo `statistics-url`
- `data/ts/` – spostamento cumulato LOS (`disp`, mm), un GeoJSON per trimestre, per il cursore temporale
- `data/csv/` – serie storica completa di ogni punto (277 date, colonne `date`, `disp`)
- `apex-config.json` – configurazione da importare nel Configuration Builder

## Come funziona il grafico

Ogni punto ha l'attributo `statistics-url` con l'indirizzo del CSV della sua serie storica.
Nel config, il grafico usa una sorgente `lookupURL` sul campo `statistics-url`:
al clic sul punto APEx scarica il CSV e lo disegna.

## Uso

1. Importa `apex-config.json` nel Configuration Builder (Home → Load).
2. In anteprima: *Data Values* → clic su un punto → scheda *Charts*.

## Variante FlatGeobuf

- `data/fgb/` – gli stessi dati in formato FlatGeobuf (EPSG:3857, con indice spaziale)
- `apex-config-fgb.json` – configurazione identica ad `apex-config.json` ma con i layer letti dai file `.fgb`

Il grafico funziona allo stesso modo: ogni punto ha l'attributo `statistics-url` che punta al CSV in `data/csv/`.
