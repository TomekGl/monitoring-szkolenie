# Serwer Prometheus

## Uruchomienie

```
docker-compose up -d
```

## Dostęp do UI

http://localhost:9090

## Status targetów

http://localhost:9090/targets

## PromQL

http://localhost:9090/graph

### Typy danych
  * Wektor Instant vector - wiele metryk z tym samym TS
  * Wektor Range vector - przedział czasu
  * Skalar

### Wybieranie danych z bazy
  * Filtrowanie wg labeli
  * Operatory
  * Funkcje

## Zadania w PromQL UI

1. Znaleźć metrykę zawierającą użycie dysku, rozmiar dysku

2. Wyliczyć wolne miejsce na dysku (procentowo)

3. Wykres użycia procesora
* Wyświetlić metryki `node_cpu_seconds_total`
* Przełączyć na tryb wykresu
* Wybrać metryki z labelem `mode` innym niż `idle`
* Policzyć pochodną (rate). Uwaga: funkcja przyjmuje szereg czasowy, a nie skalar.
* Zsumować z wszystkich `mode`, zachowując pozostałe labele
* Zsumować z wszystkich `cpu`, zachowując label `node`.

2. Hint: zamiast sumować wszystkie różne niż `idle`, można odjąć `idle` od 1 (100%).

Test obciążeniowy: `docker run --rm -it progrium/stress --cpu 2 --timeout 60s`
