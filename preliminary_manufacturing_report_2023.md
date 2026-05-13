# Preliminary Report: Municipal Manufacturing Capacity in Mexico

**Generated on:** 2026-05-13

## 1. Objective

This report presents the first exploratory results of the project *Market Opportunity Analytics for Nearshoring-Driven Industrial B2B Services in Mexico*.

At this stage, the objective is not to estimate nearshoring effects directly. The current goal is to build and validate a municipal-level data foundation to analyze manufacturing capacity across Mexico.

The report focuses on 2023 and uses the first version of the industrial capacity panel created from INEGI Economic Census data.

## 2. Data

The analysis uses the processed file:

- `municipality_industrial_capacity_panel.csv`

The unit of observation is:

`year × municipality`

For 2023, the panel includes **2,451 municipalities** across **32 federal entities**.

The main variables used in this report include manufacturing employment, value added, establishments, value added per worker, industrial diversity, and the composite industrial capacity score.

## 3. Methodological Approach

The main index used in this report is:

- `industrial_capacity_score`

This is a descriptive composite score of installed manufacturing capacity. It combines normalized indicators of manufacturing employment, value added, income, establishments, industrial diversity, average establishment size, and value added per worker.

The score should not be interpreted as a nearshoring score, a causal measure, or a prediction of future investment. It summarizes relative manufacturing strength within the same year.

For relative interpretation, the report uses:

- `industrial_capacity_percentile`

This percentile is calculated after ranking municipalities by the composite score within 2023. It indicates the relative position of each municipality compared with other municipalities in the same year.

## 4. Main Results

The municipality with the highest industrial capacity score in 2023 is **Saltillo, Coahuila de Zaragoza**, with an industrial capacity score of **0.993** and an industrial capacity percentile of **1.000**.

The following table presents the top 10 municipalities by the composite industrial capacity score.

|   Rank | Municipality    | State                |   Score |   Percentile | Group              | Employment   | Value added   | Establishments   |
|-------:|:----------------|:---------------------|--------:|-------------:|:-------------------|:-------------|:--------------|:-----------------|
|      1 | Saltillo        | Coahuila de Zaragoza |   0.993 |        1     | Top industrial hub | 74,640       | 226,838.4     | 2,758            |
|      2 | San Luis Potosí | San Luis Potosí      |   0.992 |        1     | Top industrial hub | 122,990      | 112,107.0     | 3,545            |
|      3 | Querétaro       | Querétaro            |   0.991 |        0.999 | Top industrial hub | 112,895      | 111,460.5     | 3,544            |
|      4 | Aguascalientes  | Aguascalientes       |   0.991 |        0.999 | Top industrial hub | 75,556       | 128,718.7     | 4,166            |
|      5 | Toluca          | México               |   0.991 |        0.998 | Top industrial hub | 97,042       | 99,527.3      | 5,132            |
|      6 | Tijuana         | Baja California      |   0.99  |        0.998 | Top industrial hub | 325,983      | 153,382.8     | 3,977            |
|      7 | Zapopan         | Jalisco              |   0.99  |        0.997 | Top industrial hub | 125,448      | 96,995.7      | 4,454            |
|      8 | Juárez          | Chihuahua            |   0.989 |        0.997 | Top industrial hub | 364,180      | 162,648.3     | 2,631            |
|      9 | Hermosillo      | Sonora               |   0.989 |        0.996 | Top industrial hub | 65,023       | 101,436.6     | 4,034            |
|     10 | Apodaca         | Nuevo León           |   0.988 |        0.996 | Top industrial hub | 161,584      | 135,425.6     | 1,597            |

## 5. Rankings by Individual Indicator

The following tables show the top municipalities for selected manufacturing indicators.

### 5.1 Highest Manufacturing Employment

|   Rank | Municipality    | State           | Employment   |   Capacity percentile | Capacity group     |
|-------:|:----------------|:----------------|:-------------|----------------------:|:-------------------|
|      1 | Juárez          | Chihuahua       | 364,180      |              0.996937 | Top industrial hub |
|      2 | Tijuana         | Baja California | 325,983      |              0.997812 | Top industrial hub |
|      3 | León            | Guanajuato      | 167,948      |              0.992123 | Top industrial hub |
|      4 | Apodaca         | Nuevo León      | 161,584      |              0.996061 | Top industrial hub |
|      5 | Reynosa         | Tamaulipas      | 156,496      |              0.989059 | Top industrial hub |
|      6 | Zapopan         | Jalisco         | 125,448      |              0.997374 | Top industrial hub |
|      7 | Chihuahua       | Chihuahua       | 124,212      |              0.995624 | Top industrial hub |
|      8 | San Luis Potosí | San Luis Potosí | 122,990      |              0.999562 | Top industrial hub |
|      9 | Guadalajara     | Jalisco         | 119,521      |              0.993435 | Top industrial hub |
|     10 | Mexicali        | Baja California | 113,604      |              0.994748 | Top industrial hub |

### 5.2 Highest Manufacturing Value Added

|   Rank | Municipality    | State                | Value added   |   Capacity percentile | Capacity group     |
|-------:|:----------------|:---------------------|:--------------|----------------------:|:-------------------|
|      1 | Saltillo        | Coahuila de Zaragoza | 226,838.4     |              1        | Top industrial hub |
|      2 | Juárez          | Chihuahua            | 162,648.3     |              0.996937 | Top industrial hub |
|      3 | Ramos Arizpe    | Coahuila de Zaragoza | 155,813.0     |              0.985558 | Top industrial hub |
|      4 | Celaya          | Guanajuato           | 154,528.5     |              0.995186 | Top industrial hub |
|      5 | Tijuana         | Baja California      | 153,382.8     |              0.997812 | Top industrial hub |
|      6 | Apodaca         | Nuevo León           | 135,425.6     |              0.996061 | Top industrial hub |
|      7 | Aguascalientes  | Aguascalientes       | 128,718.7     |              0.998687 | Top industrial hub |
|      8 | San Luis Potosí | San Luis Potosí      | 112,107.0     |              0.999562 | Top industrial hub |
|      9 | Querétaro       | Querétaro            | 111,460.5     |              0.999125 | Top industrial hub |
|     10 | Hermosillo      | Sonora               | 101,436.6     |              0.996499 | Top industrial hub |

### 5.3 Highest Number of Manufacturing Establishments

|   Rank | Municipality                           | State               | Establishments   |   Capacity percentile | Capacity group                 |
|-------:|:---------------------------------------|:--------------------|:-----------------|----------------------:|:-------------------------------|
|      1 | León                                   | Guanajuato          | 12,015           |              0.992123 | Top industrial hub             |
|      2 | Puebla                                 | Puebla              | 8,093            |              0.988184 | Top industrial hub             |
|      3 | Guadalajara                            | Jalisco             | 7,684            |              0.993435 | Top industrial hub             |
|      4 | Ecatepec de Morelos                    | México              | 7,679            |              0.991247 | Top industrial hub             |
|      5 | Iztapalapa                             | Ciudad de México    | 7,551            |              0.986871 | Top industrial hub             |
|      6 | Toluca                                 | México              | 5,132            |              0.998249 | Top industrial hub             |
|      7 | Heroica Ciudad de Juchitán de Zaragoza | Oaxaca              | 5,132            |              0.834136 | Relevant industrial base       |
|      8 | Monterrey                              | Nuevo León          | 4,957            |              0.993873 | Top industrial hub             |
|      9 | Morelia                                | Michoacán de Ocampo | 4,773            |              0.976368 | Top industrial hub             |
|     10 | Nezahualcóyotl                         | México              | 4,607            |              0.948796 | Strong industrial municipality |

### 5.4 Highest Manufacturing Value Added per Worker

|   Rank | Municipality          | State                           |   Value added per worker |   Capacity percentile | Capacity group                 |
|-------:|:----------------------|:--------------------------------|-------------------------:|----------------------:|:-------------------------------|
|      1 | Nacozari de García    | Sonora                          |                   17.144 |              0.843326 | Relevant industrial base       |
|      2 | Nava                  | Coahuila de Zaragoza            |                    7.775 |              0.910284 | Strong industrial municipality |
|      3 | Apazapan              | Veracruz de Ignacio de la Llave |                    7.046 |              0.621882 | Moderate industrial base       |
|      4 | Salina Cruz           | Oaxaca                          |                    6.147 |              0.952735 | Top industrial hub             |
|      5 | Apan                  | Hidalgo                         |                    5.187 |              0.892341 | Relevant industrial base       |
|      6 | Ixhuatlán del Sureste | Veracruz de Ignacio de la Llave |                    4.885 |              0.647702 | Moderate industrial base       |
|      7 | Cosoleacaque          | Veracruz de Ignacio de la Llave |                    4.65  |              0.917724 | Strong industrial municipality |
|      8 | Santiago de Anaya     | Hidalgo                         |                    4.606 |              0.747921 | Moderate industrial base       |
|      9 | Chinameca             | Veracruz de Ignacio de la Llave |                    4.408 |              0.799125 | Relevant industrial base       |
|     10 | Reforma               | Chiapas                         |                    4.205 |              0.895405 | Relevant industrial base       |

### 5.5 Highest Manufacturing Diversity

|   Rank | Municipality             | State                |   Manufacturing activities |   Capacity percentile | Capacity group     |
|-------:|:-------------------------|:---------------------|---------------------------:|----------------------:|:-------------------|
|      1 | San Nicolás de los Garza | Nuevo León           |                         21 |              0.987746 | Top industrial hub |
|      2 | Saltillo                 | Coahuila de Zaragoza |                         21 |              1        | Top industrial hub |
|      3 | San Luis Potosí          | San Luis Potosí      |                         21 |              0.999562 | Top industrial hub |
|      4 | Querétaro                | Querétaro            |                         21 |              0.999125 | Top industrial hub |
|      5 | Guadalajara              | Jalisco              |                         21 |              0.993435 | Top industrial hub |
|      6 | Monterrey                | Nuevo León           |                         21 |              0.993873 | Top industrial hub |
|      7 | Guadalupe                | Nuevo León           |                         21 |              0.994311 | Top industrial hub |
|      8 | Mexicali                 | Baja California      |                         21 |              0.994748 | Top industrial hub |
|      9 | Celaya                   | Guanajuato           |                         21 |              0.995186 | Top industrial hub |
|     10 | Chihuahua                | Chihuahua            |                         21 |              0.995624 | Top industrial hub |

## 6. Preliminary Interpretation

The results suggest that manufacturing capacity in Mexico is concentrated in a limited group of municipalities. The leading municipalities tend to combine high employment, high value added, a significant number of establishments, and a relatively diversified manufacturing base.

The composite score provides a broader view than any single indicator. Some municipalities may rank highly by employment but not by value added per worker, while others may show high productivity indicators despite having a smaller manufacturing base.

At this stage, the most appropriate interpretation is that municipalities with high industrial capacity percentiles have stronger relative manufacturing bases compared with other Mexican municipalities in 2023.

## 7. Limitations

This analysis is descriptive and preliminary.

The current score does not measure nearshoring causally and should not be interpreted as a direct measure of future investment attraction.

The current module does not yet include local B2B service supply, logistics infrastructure, talent availability, IMMEX activity, exports, foreign direct investment, industrial parks, security, energy, or water availability.

The monetary variables are used for relative comparisons within 2023. Additional work would be needed to make real intertemporal comparisons across census years.

## 8. Next Steps

The next steps are:

1. Review the top municipalities identified in the 2023 rankings.
2. Compare the composite score against individual indicators.
3. Incorporate DENUE data to measure local B2B service supply.
4. Compare manufacturing capacity with the local availability of industrial B2B services.
5. Develop a preliminary municipal opportunity typology.
