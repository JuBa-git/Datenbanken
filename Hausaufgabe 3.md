# Hausaufgabe
## A) Geben Sie einer Liste aller Schüler aus, die ein Apple-Smartphone besitzen. Auszugeben sind der Schülername und der Name des Wohnorts.
```sql
SELECT s.name, o.name
FROM schueler s , orte o, smartphones p
WHERE p.marke = 'Apple'
  AND s.idSmartphones = p.id
  AND s.idOrte = o.id ;
```
## B1) Wir brauchen eine Liste mit den Namen aller Lehrer und der zugehörigen Schüler. Die Spalten sollen genau diese Überschrift haben: "Lehrername" / "Schülername". (Das wird etwas unübersichtlich, macht nichts.)
```sql
SELECT l.name as 'Lehrername', s.name as 'Schülername'
FROM lehrer l left join lehrer_hat_schueler ls on l.id = ls.idLehrer, schueler s
WHERE ls.idSchueler = s.id;
```

## B2) Wir brauchen eine Liste der Schüler von Frau Maier. Wir brauchen folgende Spalten: Schülername, Schülerwohnort
```sql
SELECT s.name, o.name
FROM lehrer l, lehrer_hat_schueler ls, schueler s, orte o
WHERE l.id = ls.idLehrer
  AND ls.idSchueler = s.id
  AND s.idOrte = o.id
  AND l.name = 'Maier';
```

## C) Geben Sie alle Schüler aus, die in Emmendingen wohnen. Folgende Spalten anzeigen: Schülername, Wohnort, Smartphonemarke.
```sql
SELECT s.name, o.name, p.marke
FROM schueler s, orte o, smartphones p
WHERE s.idSmartphones = p.id
  AND s.idOrte = o.id
  AND o.name = 'Emmendingen';
```

## D) Geben Sie alle Schüler aus, die in Emmendingen wohnen und bei Herrn Huber Unterricht haben. Ausgabe Schülername, Wohnort, Lehrername.
```sql
SELECT s.name, o.name, l.name
FROM schueler s, orte o, lehrer l, lehrer_hat_schueler ls
WHERE l.id = ls.idLehrer
  AND ls.idSchueler = s.id
  AND s.idOrte = o.id
  AND o.name = 'Emmendingen'
  AND l.name = 'Huber';
```
