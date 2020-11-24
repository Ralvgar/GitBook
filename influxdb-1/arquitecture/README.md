# Arquitecture

All data saved into influxdb is ordered by columns if you do a get request you're going to recive an answer like this: 

```text
{
    "results": [
        {
            "statement_id": 0,
            "series": [
                {
                    "name": "Andreas_IBZ",
                    "columns": [
                        "time",
                        "CO2[ppm]",
                        "Sensor",
                        "TVOC[ppb]",
                        "T[°C]",
                        "baseline",
                        "eCO2[ppm]",
                        "p[hPa]",
                        "rH[o/o]"
                    ],
                    "values": [
                        [
                            "2020-10-13T06:49:28.151206703Z",
                            null,
                            "CCS811-001",
                            0,
                            0,
                            null,
                            0,
                            972.35,
                            0
                        ]....
```

The columns array contain the name of each value in the same order, if you want only the value of one column you can recive it using the column name into your request:

```text
SELECT MEAN("eCO2[ppm]") FROM "Andreas_IBZ"
```

