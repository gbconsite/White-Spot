# Whitespot API

Zugang über Basic Authentication

## 1. Abfrage welche Werte zur Verfügung stehen.

<https://www.white-spot.de/api/available_values.json>

Bsp. Rückgabe:  

    {
      "values": {
        "ew": "Einwohner",
        "ew_0014": "Einwohner 0 bis 14 Jahre",
        "hh": "Anzahl Haushalte",
        "ew_zz": "Zuzüge insgesamt",
        "p25ew": "Einwohner insgesamt - Prognose 2025",
        "p30ew": "Einwohner insgesamt - Prognose 2030",
        "bap_gesamt": "Büroarbeitsplätze insgesamt",
        "cfiw_abs": "Affinität für Fitness/Wellness absolut",
        "lohas_abs": "Lifestyles of Health and Sustainability absolut",
        "sysgastro": "Systemgastronomie",
        "kk_ew": "Kaufkraft pro Einwohner",
        "tech_prueforga": "Technische Prüforganisationen" 
      }
    }

## 2. Abfrage welche Punkt Layer zur Verfügung stehen.

<https://www.white-spot.de/api/available_layers.json>

-   System Layers, diese Daten kommen von gbconsite
-   Own Layers, diese Daten kommen von Kunden

Bsp. Rückgabe:  

    {
        "system_layers": {
            "129": {
                "name": "FSP",
                "properties": ["Name", "Adresse", "Entfernung (Meter)"]
            },
            "128": {
                "name": "GTÜ",
                "properties": ["Name", "Adresse", "Entfernung (Meter)"]
            },
            "135": {
                "name": "Kfz-Handel",
                "properties": ["Name", "Adresse", "Entfernung (Meter)"]
            },
            "130": {
                "name": "KÜS",
                "properties": ["Name", "Adresse", "Entfernung (Meter)"]
            },
            "132": {
                "name": "TÜV NORD",
                "properties": ["Name", "Adresse", "Entfernung (Meter)"]
            },
            "127": {
                "name": "TÜV Rheinland",
                "properties": ["Name", "Adresse", "Entfernung (Meter)"]
            },
            "133": {
                "name": "TÜV SÜD",
                "properties": ["Name", "Adresse", "Entfernung (Meter)"]
            },
            "131": {
                "name": "TÜV Thüringen",
                "properties": ["Name", "Adresse", "Entfernung (Meter)"]
            },
            "134": {
                "name": "Unterhaltungselektronik-Fachmarkt",
                "properties": ["Name", "Adresse", "Entfernung (Meter)"]
            }
        },
        "own_layers": {
            "11": {
                "name": "PLZ Zentroide",
                "properties": ["name", "description", "Entfernung (Meter)"]
            },
            "10": {
                "name": "Schüco-Partner",
                "properties": ["ID", "Art", "Ort", "PLZ", "Typ", "Name", "Status", "Adresse", "Entfernung (Meter)"]
            }
        }
    }

## 3. Abfrage zum Standort

<https://www.white-spot.de/api/whitespot_location.json?lat=48.27679550566659&lon=11.574096679687498&radius=3000>

| Parameter         | Beschreibung                                                                                                                         | Werte                     |
|-------------------|--------------------------------------------------------------------------------------------------------------------------------------|---------------------------|
| radius            | **Required** Radius                                                                                                                  | integer                   |
| minuten           | **Required** Für Fahrzeitgebiet statt Radius                                                                                         | integer                   |
| lat               | **Required** Latitude                                                                                                                | float                     |
| lon               | **Required** Longitude                                                                                                               | float                     |
| postalCode        | **Required alt. 1** Postleitzahl                                                                                                     | string                    |
| city              | **Required alt. 1** Ort                                                                                                              | string                    |
| street            | **Required alt. 1** Straße (kann auch die Hausnummer beinhalten)                                                                     | string                    |
| houseNumber       | **Optional alt. 1** Hausnummer                                                                                                       | string                    |
| country           | **Optional alt. 1** Land                                                                                                             | string                    |
| address           | **Required alt.2 (kann mit alt 1 kombiniert werden)** kompletter Adressstring                                                        | string                    |
| countryCode       | **Optional alt. 1/2** Land ISO 3166-1 alpha-3 (DEU)                                                                                  | string                    |
| 200               | **Optional** Die Werte werden in einem 200x200 Meter Raster ermittelt statt 600x600. (sinnvoll bei kleinem Radius bzw wenig Minuten. | true oder false (default) |
| all\_layers       | **Optional** Alle System Layers                                                                                                      | true oder false (default) |
| layer\_ids        | **Optional** System Layers mit Ids                                                                                                   | Komma Liste               |
| layer\_names      | **Optional** System Layers mit Namen                                                                                                 | Komma Liste               |
| all\_own\_layers  | Alle Eigenen Layers                                                                                                                  | true oder false (default) |
| own\_layer\_ids   | **Optional** Eigene Layers mit Ids                                                                                                   | Komma Liste               |
| own\_layer\_names | **Optional** Eigene Layers mit Namen                                                                                                 | Komma Liste               |

Wenn keine Koordinaten vorhanden sind, lässt sich Alternative 1
und 2 verwenden.  
Alternative 1: Es muss mindestens 1 Wert angegeben sein.

Bsp. Rückgabe:  

    {
        "data": {
            "ew": {
                "name": "Einwohner",
                "value": 37332
            },
            "ew_0014": {
                "name": "Einwohner 0 bis 14 Jahre",
                "value": 5112
            },
            "hh": {
                "name": "Anzahl Haushalte",
                "value": 18586
            },
            "ew_zz": {
                "name": "Zuzüge insgesamt",
                "value": 3462
            },
            "p25ew": {
                "name": "Einwohner insgesamt - Prognose 2025",
                "value": 40568
            },
            "p30ew": {
                "name": "Einwohner insgesamt - Prognose 2030",
                "value": 41939
            },
            "bap_gesamt": {
                "name": "Büroarbeitsplätze insgesamt",
                "value": 12400
            },
            "cfiw_abs": {
                "name": "Affinität für Fitness/Wellness absolut",
                "value": 10023
            },
            "lohas_abs": {
                "name": "Lifestyles of Health and Sustainability absolut",
                "value": 6370
            },
            "sysgastro": {
                "name": "Systemgastronomie",
                "value": 3
            },
            "kk_ew": {
                "name": "Kaufkraft pro Einwohner",
                "value": 27163
            },
            "tech_prueforga": {
                "name": "Technische Prüforganisationen",
                "value": 2
            }
        },
        "layer": [],
        "own_layer": [],
        "input": {
            "radius": "3000",
            "minuten": null,
            "latitude": "48.27679550566659",
            "longitude": "11.574096679687498",
            "geocode": {
                "postalCode": null,
                "city": null,
                "street": null,
                "houseNumber": null,
                "country": null,
                "address": null,
                "countryCode": null
            },
            "layer_ids": null,
            "layer_names": null,
            "own_layer_ids": null,
            "own_layer_names": true,
            "all_layers": null,
            "all_own_layers": null,
            "200": false
        }
    }

<https://www.white-spot.de/api/whitespot_location.json?lat=48.27679550566659&lon=11.574096679687498&radius=3000&all_own_layers=true&all_layers=true>

    {
        "data": {
            "ew": {
                "name": "Einwohner",
                "value": 55238
            },
            "ew_0014": {
                "name": "Einwohner 0 bis 14 Jahre",
                "value": 7671
            },
            "hh": {
                "name": "Anzahl Haushalte",
                "value": 26892
            },
            "ew_zz": {
                "name": "Zuzüge insgesamt",
                "value": 5313
            },
            "p25ew": {
                "name": "Einwohner insgesamt - Prognose 2025",
                "value": 60750
            },
            "p30ew": {
                "name": "Einwohner insgesamt - Prognose 2030",
                "value": 62903
            },
            "bap_gesamt": {
                "name": "Büroarbeitsplätze insgesamt",
                "value": 21989
            },
            "cfiw_abs": {
                "name": "Affinität für Fitness/Wellness absolut",
                "value": 15191
            },
            "lohas_abs": {
                "name": "Lifestyles of Health and Sustainability absolut",
                "value": 9516
            },
            "sysgastro": {
                "name": "Systemgastronomie",
                "value": 3
            },
            "kk_ew": {
                "name": "Kaufkraft pro Einwohner",
                "value": 26675
            },
            "tech_prueforga": {
                "name": "Technische Prüforganisationen",
                "value": 6
            }
        },
        "layer": [{
            "name": "Kfz-Handel",
            "id": 135,
            "data": [{
                "Name": "Auto-Service-Team GmbH",
                "Adresse": "Hauptstraße 41, 85716 Unterschleißheim",
                "Entfernung (Meter)": 662
            }, {
                "Name": "KölblKratzmeier GmbH \u0026 Co. KG",
                "Adresse": "Carl-von-Linde-Straße 31, 85716 Unterschleißheim",
                "Entfernung (Meter)": 680
            }, {
                "Name": "KölblKratzmeier GmbH \u0026 Co. KG",
                "Adresse": "Carl-von-Linde-Straße 31, 85716 Unterschleißheim",
                "Entfernung (Meter)": 680
            }, {
                "Name": "Auto Kölbl GmbH",
                "Adresse": "Beim Pfarracker 55, 85716 Unterschleißheim",
                "Entfernung (Meter)": 719
            }, {
                "Name": "Auto Kölbl GmbH",
                "Adresse": "Beim Pfarracker 55, 85716 Unterschleißheim",
                "Entfernung (Meter)": 719
            }, {
                "Name": "Auto Forum Auto Kölbl Vertriebs GmbH \u0026 Co. KG",
                "Adresse": "Landshuter Straße 25, 85716 Unterschleißheim",
                "Entfernung (Meter)": 736
            }, {
                "Name": "Autohaus Berker GmbH",
                "Adresse": "Landshuter Straße 23, 85716 Unterschleißheim",
                "Entfernung (Meter)": 785
            }, {
                "Name": "Autohaus Berker GmbH",
                "Adresse": "Landshuter Straße 23, 85716 Unterschleißheim",
                "Entfernung (Meter)": 785
            }, {
                "Name": "Dennemarck GmbH",
                "Adresse": "Sportplatzstraße 1, 85716 Unterschleißheim",
                "Entfernung (Meter)": 1136
            }, {
                "Name": "Dennemarck GmbH",
                "Adresse": "Sportplatzstraße 1, 85716 Unterschleißheim",
                "Entfernung (Meter)": 1136
            }, {
                "Name": "Autohaus Dill",
                "Adresse": "Obere Hauptstraße 8, 85386 Eching",
                "Entfernung (Meter)": 3970
            }, {
                "Name": "BMW AG Niederlassung München",
                "Adresse": "Schleißheimer Straße 82, 85748 Garching bei München",
                "Entfernung (Meter)": 4953
            }]
        }, {
            "name": "TÜV Rheinland",
            "id": 127,
            "data": []
        }, {
            "name": "GTÜ",
            "id": 128,
            "data": [{
                "Name": "Kfz-Prüfstelle Unterschleißheim Schubert Kfz-Sachverständige GmbH",
                "Adresse": "Einsteinstr. 6, 85716 Unterschleißheim",
                "Entfernung (Meter)": 1230
            }]
        }, {
            "name": "FSP",
            "id": 129,
            "data": []
        }, {
            "name": "KÜS",
            "id": 130,
            "data": [{
                "Name": "Dipl.-Ing. (FH) Bernd Daniel-Soldner",
                "Adresse": "Dieselstr. 1a, 85716 Unterschleißheim",
                "Entfernung (Meter)": 550
            }, {
                "Name": "Ingenieurbüro Johannes Kreuch",
                "Adresse": "Eggentaler Str. 27, 85778 Haimhausen",
                "Entfernung (Meter)": 4096
            }]
        }, {
            "name": "TÜV Thüringen",
            "id": 131,
            "data": []
        }, {
            "name": "TÜV NORD",
            "id": 132,
            "data": []
        }, {
            "name": "TÜV SÜD",
            "id": 133,
            "data": [{
                "Name": "TÜV SÜD Service-Center Garching",
                "Adresse": "Schleißheimer Str. 126a, 85748 Garching b.München",
                "Entfernung (Meter)": 3750
            }]
        }, {
            "name": "Unterhaltungselektronik-Fachmarkt",
            "id": 134,
            "data": []
        }],
        "own_layer": [{
            "name": "Schüco-Partner",
            "id": 10,
            "data": []
        }, {
            "name": "PLZ Zentroide",
            "id": 11,
            "data": [{
                "name": "85716",
                "description": "Unterschleißheim, St",
                "Entfernung (Meter)": 839
            }, {
                "name": "85764",
                "description": "Oberschleißheim",
                "Entfernung (Meter)": 3306
            }, {
                "name": "85386",
                "description": "Eching",
                "Entfernung (Meter)": 4547
            }, {
                "name": "85778",
                "description": "Haimhausen",
                "Entfernung (Meter)": 4954
            }]
        }],
        "input": {
            "radius": "5000",
            "minuten": null,
            "latitude": "48.27679550566659",
            "longitude": "11.574096679687498",
            "geocode": {
                "postalCode": null,
                "city": null,
                "street": null,
                "houseNumber": null,
                "country": null,
                "address": null,
                "countryCode": null
            },
            "layer_ids": null,
            "layer_names": null,
            "own_layer_ids": null,
            "own_layer_names": true,
            "all_layers": "true",
            "all_own_layers": "true",
            "200": false
        }
    }
