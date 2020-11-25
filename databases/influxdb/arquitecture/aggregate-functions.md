---
description: Some functions that could be important for our app.
---

# Aggregate functions

### Mean <a id="mean"></a>

Returns arithmetic mean \(average\) of specified column

```text
SELECT MEAN(column_name) FROM series_name group by time(10m) ...
```

### First/Last <a id="firstlast"></a>

Returns first/last value from one column

```text
SELECT FIRST(column_name) FROM series_name ...

SELECT LAST(column_name) FROM series_name ...
```

## Group by time

you can group the values by time selected, it also works with days, hours, min, etc.

```text
SELECT MEAN(column_name) FROM series_name group by time(10m) ...
```

