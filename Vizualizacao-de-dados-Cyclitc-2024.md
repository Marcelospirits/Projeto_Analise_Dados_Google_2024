vizualizacao\_dados\_bikes
================

obs importante(caso você esteja tendo problemas na hora de executar o
Knit, erro UTF-8 caracteres especiais ) Verifique o arquivo de entrada:
Certifique-se de que o arquivo R Markdown esteja codificado em UTF-8.
Você pode verificar isso no RStudio, indo para File &gt; Reopen with
Encoding &gt; UTF-8. Remova caracteres especiais:(voce vai ver que onde
era para aparecer Exemplo “está”" vai aparecer “est?” ) Se o arquivo
contiver caracteres especiais não reconhecidos pelo UTF-8, tente
removê-los ou substituí-los por uma versão UTF-8 compatível. Use
stringAsFactors = FALSE: Ao ler dados em R, certifique-se de usar
stringAsFactors = FALSE para evitar a conversão automática de strings em
fatores, o que pode causar problemas de codificação.

``` r
library(tidyverse) #helps dados de wrangle
```

    ## ── Attaching core tidyverse packages ──────────────────────── tidyverse 2.0.0 ──
    ## ✔ dplyr     1.1.4     ✔ readr     2.1.5
    ## ✔ forcats   1.0.0     ✔ stringr   1.5.1
    ## ✔ ggplot2   3.5.0     ✔ tibble    3.2.1
    ## ✔ lubridate 1.9.3     ✔ tidyr     1.3.1
    ## ✔ purrr     1.0.2     
    ## ── Conflicts ────────────────────────────────────────── tidyverse_conflicts() ──
    ## ✖ dplyr::filter() masks stats::filter()
    ## ✖ dplyr::lag()    masks stats::lag()
    ## ℹ Use the conflicted package (<http://conflicted.r-lib.org/>) to force all conflicts to become errors

``` r
library(lubridate) #helps Atributos de data de de biblioteca (lubridato)
library(ggplot2) #helps visualizar dados
```

``` r
setwd("F:\\vizualixacao dados Cyclistic 2024")
```

\#usei F:\\ no chamado do local onde estão os dados porque ele da erro
usando só , o sistema acha que é um caracter especial.

Preparar Selecionado dados historicos dos ultimos 12 meses (janeiro de
2023 a janeiro de 2024), os dados foram fornecidos por Motivar
International Inc, sendo dados publicos. Os dados pessoais dos usuarios
sâo anonimizado.

``` r
#Importando datos 
bike_trips_2023_01_df <- read_csv("202301-divvy-tripdata.csv")
```

    ## Rows: 190301 Columns: 13
    ## ── Column specification ────────────────────────────────────────────────────────
    ## Delimiter: ","
    ## chr  (7): ride_id, rideable_type, start_station_name, start_station_id, end_...
    ## dbl  (4): start_lat, start_lng, end_lat, end_lng
    ## dttm (2): started_at, ended_at
    ## 
    ## ℹ Use `spec()` to retrieve the full column specification for this data.
    ## ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.

``` r
bike_trips_2023_02_df <- read_csv("202302-divvy-tripdata.csv")
```

    ## Rows: 190445 Columns: 13
    ## ── Column specification ────────────────────────────────────────────────────────
    ## Delimiter: ","
    ## chr  (7): ride_id, rideable_type, start_station_name, start_station_id, end_...
    ## dbl  (4): start_lat, start_lng, end_lat, end_lng
    ## dttm (2): started_at, ended_at
    ## 
    ## ℹ Use `spec()` to retrieve the full column specification for this data.
    ## ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.

``` r
bike_trips_2023_03_df <- read_csv("202303-divvy-tripdata.csv")
```

    ## Rows: 258678 Columns: 13
    ## ── Column specification ────────────────────────────────────────────────────────
    ## Delimiter: ","
    ## chr  (7): ride_id, rideable_type, start_station_name, start_station_id, end_...
    ## dbl  (4): start_lat, start_lng, end_lat, end_lng
    ## dttm (2): started_at, ended_at
    ## 
    ## ℹ Use `spec()` to retrieve the full column specification for this data.
    ## ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.

``` r
bike_trips_2023_04_df <- read_csv("202304-divvy-tripdata.csv")
```

    ## Rows: 426590 Columns: 13
    ## ── Column specification ────────────────────────────────────────────────────────
    ## Delimiter: ","
    ## chr  (7): ride_id, rideable_type, start_station_name, start_station_id, end_...
    ## dbl  (4): start_lat, start_lng, end_lat, end_lng
    ## dttm (2): started_at, ended_at
    ## 
    ## ℹ Use `spec()` to retrieve the full column specification for this data.
    ## ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.

``` r
bike_trips_2023_05_df <- read_csv("202305-divvy-tripdata.csv")
```

    ## Rows: 604827 Columns: 13
    ## ── Column specification ────────────────────────────────────────────────────────
    ## Delimiter: ","
    ## chr  (7): ride_id, rideable_type, start_station_name, start_station_id, end_...
    ## dbl  (4): start_lat, start_lng, end_lat, end_lng
    ## dttm (2): started_at, ended_at
    ## 
    ## ℹ Use `spec()` to retrieve the full column specification for this data.
    ## ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.

``` r
bike_trips_2023_06_df <- read_csv("202306-divvy-tripdata.csv")
```

    ## Rows: 719618 Columns: 13
    ## ── Column specification ────────────────────────────────────────────────────────
    ## Delimiter: ","
    ## chr  (7): ride_id, rideable_type, start_station_name, start_station_id, end_...
    ## dbl  (4): start_lat, start_lng, end_lat, end_lng
    ## dttm (2): started_at, ended_at
    ## 
    ## ℹ Use `spec()` to retrieve the full column specification for this data.
    ## ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.

``` r
bike_trips_2023_07_df <- read_csv("202307-divvy-tripdata.csv")
```

    ## Rows: 767650 Columns: 13
    ## ── Column specification ────────────────────────────────────────────────────────
    ## Delimiter: ","
    ## chr  (7): ride_id, rideable_type, start_station_name, start_station_id, end_...
    ## dbl  (4): start_lat, start_lng, end_lat, end_lng
    ## dttm (2): started_at, ended_at
    ## 
    ## ℹ Use `spec()` to retrieve the full column specification for this data.
    ## ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.

``` r
bike_trips_2023_08_df <- read_csv("202308-divvy-tripdata.csv")
```

    ## Rows: 771693 Columns: 13
    ## ── Column specification ────────────────────────────────────────────────────────
    ## Delimiter: ","
    ## chr  (7): ride_id, rideable_type, start_station_name, start_station_id, end_...
    ## dbl  (4): start_lat, start_lng, end_lat, end_lng
    ## dttm (2): started_at, ended_at
    ## 
    ## ℹ Use `spec()` to retrieve the full column specification for this data.
    ## ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.

``` r
bike_trips_2023_09_df <- read_csv("202309-divvy-tripdata.csv")
```

    ## Rows: 666371 Columns: 13
    ## ── Column specification ────────────────────────────────────────────────────────
    ## Delimiter: ","
    ## chr  (7): ride_id, rideable_type, start_station_name, start_station_id, end_...
    ## dbl  (4): start_lat, start_lng, end_lat, end_lng
    ## dttm (2): started_at, ended_at
    ## 
    ## ℹ Use `spec()` to retrieve the full column specification for this data.
    ## ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.

``` r
bike_trips_2023_10_df <- read_csv("202310-divvy-tripdata.csv")
```

    ## Rows: 537113 Columns: 13
    ## ── Column specification ────────────────────────────────────────────────────────
    ## Delimiter: ","
    ## chr  (7): ride_id, rideable_type, start_station_name, start_station_id, end_...
    ## dbl  (4): start_lat, start_lng, end_lat, end_lng
    ## dttm (2): started_at, ended_at
    ## 
    ## ℹ Use `spec()` to retrieve the full column specification for this data.
    ## ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.

``` r
bike_trips_2023_11_df <- read_csv("202311-divvy-tripdata.csv")
```

    ## Rows: 362518 Columns: 13
    ## ── Column specification ────────────────────────────────────────────────────────
    ## Delimiter: ","
    ## chr  (7): ride_id, rideable_type, start_station_name, start_station_id, end_...
    ## dbl  (4): start_lat, start_lng, end_lat, end_lng
    ## dttm (2): started_at, ended_at
    ## 
    ## ℹ Use `spec()` to retrieve the full column specification for this data.
    ## ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.

``` r
bike_trips_2023_12_df <- read_csv("202312-divvy-tripdata.csv")
```

    ## Rows: 224073 Columns: 13
    ## ── Column specification ────────────────────────────────────────────────────────
    ## Delimiter: ","
    ## chr  (7): ride_id, rideable_type, start_station_name, start_station_id, end_...
    ## dbl  (4): start_lat, start_lng, end_lat, end_lng
    ## dttm (2): started_at, ended_at
    ## 
    ## ℹ Use `spec()` to retrieve the full column specification for this data.
    ## ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.

``` r
bike_trips_2024_01_df <- read_csv("202401-divvy-tripdata.csv")
```

    ## Rows: 144873 Columns: 13
    ## ── Column specification ────────────────────────────────────────────────────────
    ## Delimiter: ","
    ## chr  (7): ride_id, rideable_type, start_station_name, start_station_id, end_...
    ## dbl  (4): start_lat, start_lng, end_lat, end_lng
    ## dttm (2): started_at, ended_at
    ## 
    ## ℹ Use `spec()` to retrieve the full column specification for this data.
    ## ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.

Eu crio uma lista do dataframe para facilitar a aplicação das funções
verificação.

``` r
# Lista con los data frames
bike_trips_list <- list(
  bike_trips_2023_01_df,
  bike_trips_2023_02_df,
  bike_trips_2023_03_df,
  bike_trips_2023_03_df,
  bike_trips_2023_04_df,
  bike_trips_2023_05_df,
  bike_trips_2023_06_df,
  bike_trips_2023_07_df,
  bike_trips_2023_08_df,
  bike_trips_2023_09_df,
  bike_trips_2023_10_df,
  bike_trips_2023_11_df,
  bike_trips_2023_12_df,
  bike_trips_2024_01_df
  
)
```

Verifico a estrutura dos dados para ter certeza de que estão
completos,corretos, relevantes para a análise e livres de
inconcistencias.

``` r
# Itero sobre la lista para obtener la estructura de cada df
for (df in bike_trips_list) {
  print(str(df))
}
```

    ## spc_tbl_ [190,301 × 13] (S3: spec_tbl_df/tbl_df/tbl/data.frame)
    ##  $ ride_id           : chr [1:190301] "F96D5A74A3E41399" "13CB7EB698CEDB88" "BD88A2E670661CE5" "C90792D034FED968" ...
    ##  $ rideable_type     : chr [1:190301] "electric_bike" "classic_bike" "electric_bike" "classic_bike" ...
    ##  $ started_at        : POSIXct[1:190301], format: "2023-01-21 20:05:42" "2023-01-10 15:37:36" ...
    ##  $ ended_at          : POSIXct[1:190301], format: "2023-01-21 20:16:33" "2023-01-10 15:46:05" ...
    ##  $ start_station_name: chr [1:190301] "Lincoln Ave & Fullerton Ave" "Kimbark Ave & 53rd St" "Western Ave & Lunt Ave" "Kimbark Ave & 53rd St" ...
    ##  $ start_station_id  : chr [1:190301] "TA1309000058" "TA1309000037" "RP-005" "TA1309000037" ...
    ##  $ end_station_name  : chr [1:190301] "Hampden Ct & Diversey Ave" "Greenwood Ave & 47th St" "Valli Produce - Evanston Plaza" "Greenwood Ave & 47th St" ...
    ##  $ end_station_id    : chr [1:190301] "202480.0" "TA1308000002" "599" "TA1308000002" ...
    ##  $ start_lat         : num [1:190301] 41.9 41.8 42 41.8 41.8 ...
    ##  $ start_lng         : num [1:190301] -87.6 -87.6 -87.7 -87.6 -87.6 ...
    ##  $ end_lat           : num [1:190301] 41.9 41.8 42 41.8 41.8 ...
    ##  $ end_lng           : num [1:190301] -87.6 -87.6 -87.7 -87.6 -87.6 ...
    ##  $ member_casual     : chr [1:190301] "member" "member" "casual" "member" ...
    ##  - attr(*, "spec")=
    ##   .. cols(
    ##   ..   ride_id = col_character(),
    ##   ..   rideable_type = col_character(),
    ##   ..   started_at = col_datetime(format = ""),
    ##   ..   ended_at = col_datetime(format = ""),
    ##   ..   start_station_name = col_character(),
    ##   ..   start_station_id = col_character(),
    ##   ..   end_station_name = col_character(),
    ##   ..   end_station_id = col_character(),
    ##   ..   start_lat = col_double(),
    ##   ..   start_lng = col_double(),
    ##   ..   end_lat = col_double(),
    ##   ..   end_lng = col_double(),
    ##   ..   member_casual = col_character()
    ##   .. )
    ##  - attr(*, "problems")=<externalptr> 
    ## NULL
    ## spc_tbl_ [190,445 × 13] (S3: spec_tbl_df/tbl_df/tbl/data.frame)
    ##  $ ride_id           : chr [1:190445] "CBCD0D7777F0E45F" "F3EC5FCE5FF39DE9" "E54C1F27FA9354FF" "3D561E04F739CC45" ...
    ##  $ rideable_type     : chr [1:190445] "classic_bike" "electric_bike" "classic_bike" "electric_bike" ...
    ##  $ started_at        : POSIXct[1:190445], format: "2023-02-14 11:59:42" "2023-02-15 13:53:48" ...
    ##  $ ended_at          : POSIXct[1:190445], format: "2023-02-14 12:13:38" "2023-02-15 13:59:08" ...
    ##  $ start_station_name: chr [1:190445] "Southport Ave & Clybourn Ave" "Clarendon Ave & Gordon Ter" "Southport Ave & Clybourn Ave" "Southport Ave & Clybourn Ave" ...
    ##  $ start_station_id  : chr [1:190445] "TA1309000030" "13379" "TA1309000030" "TA1309000030" ...
    ##  $ end_station_name  : chr [1:190445] "Clark St & Schiller St" "Sheridan Rd & Lawrence Ave" "Aberdeen St & Monroe St" "Franklin St & Adams St (Temp)" ...
    ##  $ end_station_id    : chr [1:190445] "TA1309000024" "TA1309000041" "13156" "TA1309000008" ...
    ##  $ start_lat         : num [1:190445] 41.9 42 41.9 41.9 41.8 ...
    ##  $ start_lng         : num [1:190445] -87.7 -87.6 -87.7 -87.7 -87.6 ...
    ##  $ end_lat           : num [1:190445] 41.9 42 41.9 41.9 41.8 ...
    ##  $ end_lng           : num [1:190445] -87.6 -87.7 -87.7 -87.6 -87.6 ...
    ##  $ member_casual     : chr [1:190445] "casual" "casual" "member" "member" ...
    ##  - attr(*, "spec")=
    ##   .. cols(
    ##   ..   ride_id = col_character(),
    ##   ..   rideable_type = col_character(),
    ##   ..   started_at = col_datetime(format = ""),
    ##   ..   ended_at = col_datetime(format = ""),
    ##   ..   start_station_name = col_character(),
    ##   ..   start_station_id = col_character(),
    ##   ..   end_station_name = col_character(),
    ##   ..   end_station_id = col_character(),
    ##   ..   start_lat = col_double(),
    ##   ..   start_lng = col_double(),
    ##   ..   end_lat = col_double(),
    ##   ..   end_lng = col_double(),
    ##   ..   member_casual = col_character()
    ##   .. )
    ##  - attr(*, "problems")=<externalptr> 
    ## NULL
    ## spc_tbl_ [258,678 × 13] (S3: spec_tbl_df/tbl_df/tbl/data.frame)
    ##  $ ride_id           : chr [1:258678] "6842AA605EE9FBB3" "F984267A75B99A8C" "FF7CF57CFE026D02" "6B61B916032CB6D6" ...
    ##  $ rideable_type     : chr [1:258678] "electric_bike" "electric_bike" "classic_bike" "classic_bike" ...
    ##  $ started_at        : POSIXct[1:258678], format: "2023-03-16 08:20:34" "2023-03-04 14:07:06" ...
    ##  $ ended_at          : POSIXct[1:258678], format: "2023-03-16 08:22:52" "2023-03-04 14:15:31" ...
    ##  $ start_station_name: chr [1:258678] "Clark St & Armitage Ave" "Public Rack - Kedzie Ave & Argyle St" "Orleans St & Chestnut St (NEXT Apts)" "Desplaines St & Kinzie St" ...
    ##  $ start_station_id  : chr [1:258678] "13146" "491" "620" "TA1306000003" ...
    ##  $ end_station_name  : chr [1:258678] "Larrabee St & Webster Ave" NA "Clark St & Randolph St" "Sheffield Ave & Kingsbury St" ...
    ##  $ end_station_id    : chr [1:258678] "13193" NA "TA1305000030" "13154" ...
    ##  $ start_lat         : num [1:258678] 41.9 42 41.9 41.9 41.9 ...
    ##  $ start_lng         : num [1:258678] -87.6 -87.7 -87.6 -87.6 -87.7 ...
    ##  $ end_lat           : num [1:258678] 41.9 42 41.9 41.9 41.9 ...
    ##  $ end_lng           : num [1:258678] -87.6 -87.7 -87.6 -87.7 -87.7 ...
    ##  $ member_casual     : chr [1:258678] "member" "member" "member" "member" ...
    ##  - attr(*, "spec")=
    ##   .. cols(
    ##   ..   ride_id = col_character(),
    ##   ..   rideable_type = col_character(),
    ##   ..   started_at = col_datetime(format = ""),
    ##   ..   ended_at = col_datetime(format = ""),
    ##   ..   start_station_name = col_character(),
    ##   ..   start_station_id = col_character(),
    ##   ..   end_station_name = col_character(),
    ##   ..   end_station_id = col_character(),
    ##   ..   start_lat = col_double(),
    ##   ..   start_lng = col_double(),
    ##   ..   end_lat = col_double(),
    ##   ..   end_lng = col_double(),
    ##   ..   member_casual = col_character()
    ##   .. )
    ##  - attr(*, "problems")=<externalptr> 
    ## NULL
    ## spc_tbl_ [258,678 × 13] (S3: spec_tbl_df/tbl_df/tbl/data.frame)
    ##  $ ride_id           : chr [1:258678] "6842AA605EE9FBB3" "F984267A75B99A8C" "FF7CF57CFE026D02" "6B61B916032CB6D6" ...
    ##  $ rideable_type     : chr [1:258678] "electric_bike" "electric_bike" "classic_bike" "classic_bike" ...
    ##  $ started_at        : POSIXct[1:258678], format: "2023-03-16 08:20:34" "2023-03-04 14:07:06" ...
    ##  $ ended_at          : POSIXct[1:258678], format: "2023-03-16 08:22:52" "2023-03-04 14:15:31" ...
    ##  $ start_station_name: chr [1:258678] "Clark St & Armitage Ave" "Public Rack - Kedzie Ave & Argyle St" "Orleans St & Chestnut St (NEXT Apts)" "Desplaines St & Kinzie St" ...
    ##  $ start_station_id  : chr [1:258678] "13146" "491" "620" "TA1306000003" ...
    ##  $ end_station_name  : chr [1:258678] "Larrabee St & Webster Ave" NA "Clark St & Randolph St" "Sheffield Ave & Kingsbury St" ...
    ##  $ end_station_id    : chr [1:258678] "13193" NA "TA1305000030" "13154" ...
    ##  $ start_lat         : num [1:258678] 41.9 42 41.9 41.9 41.9 ...
    ##  $ start_lng         : num [1:258678] -87.6 -87.7 -87.6 -87.6 -87.7 ...
    ##  $ end_lat           : num [1:258678] 41.9 42 41.9 41.9 41.9 ...
    ##  $ end_lng           : num [1:258678] -87.6 -87.7 -87.6 -87.7 -87.7 ...
    ##  $ member_casual     : chr [1:258678] "member" "member" "member" "member" ...
    ##  - attr(*, "spec")=
    ##   .. cols(
    ##   ..   ride_id = col_character(),
    ##   ..   rideable_type = col_character(),
    ##   ..   started_at = col_datetime(format = ""),
    ##   ..   ended_at = col_datetime(format = ""),
    ##   ..   start_station_name = col_character(),
    ##   ..   start_station_id = col_character(),
    ##   ..   end_station_name = col_character(),
    ##   ..   end_station_id = col_character(),
    ##   ..   start_lat = col_double(),
    ##   ..   start_lng = col_double(),
    ##   ..   end_lat = col_double(),
    ##   ..   end_lng = col_double(),
    ##   ..   member_casual = col_character()
    ##   .. )
    ##  - attr(*, "problems")=<externalptr> 
    ## NULL
    ## spc_tbl_ [426,590 × 13] (S3: spec_tbl_df/tbl_df/tbl/data.frame)
    ##  $ ride_id           : chr [1:426590] "8FE8F7D9C10E88C7" "34E4ED3ADF1D821B" "5296BF07A2F77CB5" "40759916B76D5D52" ...
    ##  $ rideable_type     : chr [1:426590] "electric_bike" "electric_bike" "electric_bike" "electric_bike" ...
    ##  $ started_at        : POSIXct[1:426590], format: "2023-04-02 08:37:28" "2023-04-19 11:29:02" ...
    ##  $ ended_at          : POSIXct[1:426590], format: "2023-04-02 08:41:37" "2023-04-19 11:52:12" ...
    ##  $ start_station_name: chr [1:426590] NA NA NA NA ...
    ##  $ start_station_id  : chr [1:426590] NA NA NA NA ...
    ##  $ end_station_name  : chr [1:426590] NA NA NA NA ...
    ##  $ end_station_id    : chr [1:426590] NA NA NA NA ...
    ##  $ start_lat         : num [1:426590] 41.8 41.9 41.9 41.9 41.9 ...
    ##  $ start_lng         : num [1:426590] -87.6 -87.7 -87.7 -87.7 -87.7 ...
    ##  $ end_lat           : num [1:426590] 41.8 41.9 41.9 41.9 41.9 ...
    ##  $ end_lng           : num [1:426590] -87.6 -87.7 -87.7 -87.7 -87.6 ...
    ##  $ member_casual     : chr [1:426590] "member" "member" "member" "member" ...
    ##  - attr(*, "spec")=
    ##   .. cols(
    ##   ..   ride_id = col_character(),
    ##   ..   rideable_type = col_character(),
    ##   ..   started_at = col_datetime(format = ""),
    ##   ..   ended_at = col_datetime(format = ""),
    ##   ..   start_station_name = col_character(),
    ##   ..   start_station_id = col_character(),
    ##   ..   end_station_name = col_character(),
    ##   ..   end_station_id = col_character(),
    ##   ..   start_lat = col_double(),
    ##   ..   start_lng = col_double(),
    ##   ..   end_lat = col_double(),
    ##   ..   end_lng = col_double(),
    ##   ..   member_casual = col_character()
    ##   .. )
    ##  - attr(*, "problems")=<externalptr> 
    ## NULL
    ## spc_tbl_ [604,827 × 13] (S3: spec_tbl_df/tbl_df/tbl/data.frame)
    ##  $ ride_id           : chr [1:604827] "0D9FA920C3062031" "92485E5FB5888ACD" "FB144B3FC8300187" "DDEB93BC2CE9AA77" ...
    ##  $ rideable_type     : chr [1:604827] "electric_bike" "electric_bike" "electric_bike" "classic_bike" ...
    ##  $ started_at        : POSIXct[1:604827], format: "2023-05-07 19:53:48" "2023-05-06 18:54:08" ...
    ##  $ ended_at          : POSIXct[1:604827], format: "2023-05-07 19:58:32" "2023-05-06 19:03:35" ...
    ##  $ start_station_name: chr [1:604827] "Southport Ave & Belmont Ave" "Southport Ave & Belmont Ave" "Halsted St & 21st St" "Carpenter St & Huron St" ...
    ##  $ start_station_id  : chr [1:604827] "13229" "13229" "13162" "13196" ...
    ##  $ end_station_name  : chr [1:604827] NA NA NA "Damen Ave & Cortland St" ...
    ##  $ end_station_id    : chr [1:604827] NA NA NA "13133" ...
    ##  $ start_lat         : num [1:604827] 41.9 41.9 41.9 41.9 42 ...
    ##  $ start_lng         : num [1:604827] -87.7 -87.7 -87.6 -87.7 -87.7 ...
    ##  $ end_lat           : num [1:604827] 41.9 41.9 41.9 41.9 41.9 ...
    ##  $ end_lng           : num [1:604827] -87.7 -87.7 -87.7 -87.7 -87.7 ...
    ##  $ member_casual     : chr [1:604827] "member" "member" "member" "member" ...
    ##  - attr(*, "spec")=
    ##   .. cols(
    ##   ..   ride_id = col_character(),
    ##   ..   rideable_type = col_character(),
    ##   ..   started_at = col_datetime(format = ""),
    ##   ..   ended_at = col_datetime(format = ""),
    ##   ..   start_station_name = col_character(),
    ##   ..   start_station_id = col_character(),
    ##   ..   end_station_name = col_character(),
    ##   ..   end_station_id = col_character(),
    ##   ..   start_lat = col_double(),
    ##   ..   start_lng = col_double(),
    ##   ..   end_lat = col_double(),
    ##   ..   end_lng = col_double(),
    ##   ..   member_casual = col_character()
    ##   .. )
    ##  - attr(*, "problems")=<externalptr> 
    ## NULL
    ## spc_tbl_ [719,618 × 13] (S3: spec_tbl_df/tbl_df/tbl/data.frame)
    ##  $ ride_id           : chr [1:719618] "6F1682AC40EB6F71" "622A1686D64948EB" "3C88859D926253B4" "EAD8A5E0259DEC88" ...
    ##  $ rideable_type     : chr [1:719618] "electric_bike" "electric_bike" "electric_bike" "electric_bike" ...
    ##  $ started_at        : POSIXct[1:719618], format: "2023-06-05 13:34:12" "2023-06-05 01:30:22" ...
    ##  $ ended_at          : POSIXct[1:719618], format: "2023-06-05 14:31:56" "2023-06-05 01:33:06" ...
    ##  $ start_station_name: chr [1:719618] NA NA NA NA ...
    ##  $ start_station_id  : chr [1:719618] NA NA NA NA ...
    ##  $ end_station_name  : chr [1:719618] NA NA NA NA ...
    ##  $ end_station_id    : chr [1:719618] NA NA NA NA ...
    ##  $ start_lat         : num [1:719618] 41.9 41.9 42 42 42 ...
    ##  $ start_lng         : num [1:719618] -87.7 -87.7 -87.7 -87.7 -87.7 ...
    ##  $ end_lat           : num [1:719618] 41.9 41.9 41.9 42 42 ...
    ##  $ end_lng           : num [1:719618] -87.7 -87.7 -87.6 -87.7 -87.7 ...
    ##  $ member_casual     : chr [1:719618] "member" "member" "member" "member" ...
    ##  - attr(*, "spec")=
    ##   .. cols(
    ##   ..   ride_id = col_character(),
    ##   ..   rideable_type = col_character(),
    ##   ..   started_at = col_datetime(format = ""),
    ##   ..   ended_at = col_datetime(format = ""),
    ##   ..   start_station_name = col_character(),
    ##   ..   start_station_id = col_character(),
    ##   ..   end_station_name = col_character(),
    ##   ..   end_station_id = col_character(),
    ##   ..   start_lat = col_double(),
    ##   ..   start_lng = col_double(),
    ##   ..   end_lat = col_double(),
    ##   ..   end_lng = col_double(),
    ##   ..   member_casual = col_character()
    ##   .. )
    ##  - attr(*, "problems")=<externalptr> 
    ## NULL
    ## spc_tbl_ [767,650 × 13] (S3: spec_tbl_df/tbl_df/tbl/data.frame)
    ##  $ ride_id           : chr [1:767650] "9340B064F0AEE130" "D1460EE3CE0D8AF8" "DF41BE31B895A25E" "9624A293749EF703" ...
    ##  $ rideable_type     : chr [1:767650] "electric_bike" "classic_bike" "classic_bike" "electric_bike" ...
    ##  $ started_at        : POSIXct[1:767650], format: "2023-07-23 20:06:14" "2023-07-23 17:05:07" ...
    ##  $ ended_at          : POSIXct[1:767650], format: "2023-07-23 20:22:44" "2023-07-23 17:18:37" ...
    ##  $ start_station_name: chr [1:767650] "Kedzie Ave & 110th St" "Western Ave & Walton St" "Western Ave & Walton St" "Racine Ave & Randolph St" ...
    ##  $ start_station_id  : chr [1:767650] "20204" "KA1504000103" "KA1504000103" "13155" ...
    ##  $ end_station_name  : chr [1:767650] "Public Rack - Racine Ave & 109th Pl" "Milwaukee Ave & Grand Ave" "Damen Ave & Pierce Ave" "Clinton St & Madison St" ...
    ##  $ end_station_id    : chr [1:767650] "877" "13033" "TA1305000041" "TA1305000032" ...
    ##  $ start_lat         : num [1:767650] 41.7 41.9 41.9 41.9 42 ...
    ##  $ start_lng         : num [1:767650] -87.7 -87.7 -87.7 -87.7 -87.7 ...
    ##  $ end_lat           : num [1:767650] 41.7 41.9 41.9 41.9 42 ...
    ##  $ end_lng           : num [1:767650] -87.7 -87.6 -87.7 -87.6 -87.6 ...
    ##  $ member_casual     : chr [1:767650] "member" "member" "member" "member" ...
    ##  - attr(*, "spec")=
    ##   .. cols(
    ##   ..   ride_id = col_character(),
    ##   ..   rideable_type = col_character(),
    ##   ..   started_at = col_datetime(format = ""),
    ##   ..   ended_at = col_datetime(format = ""),
    ##   ..   start_station_name = col_character(),
    ##   ..   start_station_id = col_character(),
    ##   ..   end_station_name = col_character(),
    ##   ..   end_station_id = col_character(),
    ##   ..   start_lat = col_double(),
    ##   ..   start_lng = col_double(),
    ##   ..   end_lat = col_double(),
    ##   ..   end_lng = col_double(),
    ##   ..   member_casual = col_character()
    ##   .. )
    ##  - attr(*, "problems")=<externalptr> 
    ## NULL
    ## spc_tbl_ [771,693 × 13] (S3: spec_tbl_df/tbl_df/tbl/data.frame)
    ##  $ ride_id           : chr [1:771693] "903C30C2D810A53B" "F2FB18A98E110A2B" "D0DEC7C94E4663DA" "E0DDDC5F84747ED9" ...
    ##  $ rideable_type     : chr [1:771693] "electric_bike" "electric_bike" "electric_bike" "electric_bike" ...
    ##  $ started_at        : POSIXct[1:771693], format: "2023-08-19 15:41:53" "2023-08-18 15:30:18" ...
    ##  $ ended_at          : POSIXct[1:771693], format: "2023-08-19 15:53:36" "2023-08-18 15:45:25" ...
    ##  $ start_station_name: chr [1:771693] "LaSalle St & Illinois St" "Clark St & Randolph St" "Clark St & Randolph St" "Wells St & Elm St" ...
    ##  $ start_station_id  : chr [1:771693] "13430" "TA1305000030" "TA1305000030" "KA1504000135" ...
    ##  $ end_station_name  : chr [1:771693] "Clark St & Elm St" NA NA NA ...
    ##  $ end_station_id    : chr [1:771693] "TA1307000039" NA NA NA ...
    ##  $ start_lat         : num [1:771693] 41.9 41.9 41.9 41.9 41.9 ...
    ##  $ start_lng         : num [1:771693] -87.6 -87.6 -87.6 -87.6 -87.6 ...
    ##  $ end_lat           : num [1:771693] 41.9 41.9 41.9 41.9 41.9 ...
    ##  $ end_lng           : num [1:771693] -87.6 -87.6 -87.6 -87.6 -87.7 ...
    ##  $ member_casual     : chr [1:771693] "member" "member" "member" "member" ...
    ##  - attr(*, "spec")=
    ##   .. cols(
    ##   ..   ride_id = col_character(),
    ##   ..   rideable_type = col_character(),
    ##   ..   started_at = col_datetime(format = ""),
    ##   ..   ended_at = col_datetime(format = ""),
    ##   ..   start_station_name = col_character(),
    ##   ..   start_station_id = col_character(),
    ##   ..   end_station_name = col_character(),
    ##   ..   end_station_id = col_character(),
    ##   ..   start_lat = col_double(),
    ##   ..   start_lng = col_double(),
    ##   ..   end_lat = col_double(),
    ##   ..   end_lng = col_double(),
    ##   ..   member_casual = col_character()
    ##   .. )
    ##  - attr(*, "problems")=<externalptr> 
    ## NULL
    ## spc_tbl_ [666,371 × 13] (S3: spec_tbl_df/tbl_df/tbl/data.frame)
    ##  $ ride_id           : chr [1:666371] "011C1903BF4E2E28" "87DB80E048A1BF9F" "7C2EB7AF669066E3" "57D197B010269CE3" ...
    ##  $ rideable_type     : chr [1:666371] "classic_bike" "classic_bike" "electric_bike" "classic_bike" ...
    ##  $ started_at        : POSIXct[1:666371], format: "2023-09-23 00:27:50" "2023-09-02 09:26:43" ...
    ##  $ ended_at          : POSIXct[1:666371], format: "2023-09-23 00:33:27" "2023-09-02 09:38:19" ...
    ##  $ start_station_name: chr [1:666371] "Halsted St & Wrightwood Ave" "Clark St & Drummond Pl" "Financial Pl & Ida B Wells Dr" "Clark St & Drummond Pl" ...
    ##  $ start_station_id  : chr [1:666371] "TA1309000061" "TA1307000142" "SL-010" "TA1307000142" ...
    ##  $ end_station_name  : chr [1:666371] "Sheffield Ave & Wellington Ave" "Racine Ave & Fullerton Ave" "Racine Ave & 15th St" "Racine Ave & Belmont Ave" ...
    ##  $ end_station_id    : chr [1:666371] "TA1307000052" "TA1306000026" "13304" "TA1308000019" ...
    ##  $ start_lat         : num [1:666371] 41.9 41.9 41.9 41.9 41.9 ...
    ##  $ start_lng         : num [1:666371] -87.6 -87.6 -87.6 -87.6 -87.6 ...
    ##  $ end_lat           : num [1:666371] 41.9 41.9 41.9 41.9 41.9 ...
    ##  $ end_lng           : num [1:666371] -87.7 -87.7 -87.7 -87.7 -87.7 ...
    ##  $ member_casual     : chr [1:666371] "member" "member" "member" "member" ...
    ##  - attr(*, "spec")=
    ##   .. cols(
    ##   ..   ride_id = col_character(),
    ##   ..   rideable_type = col_character(),
    ##   ..   started_at = col_datetime(format = ""),
    ##   ..   ended_at = col_datetime(format = ""),
    ##   ..   start_station_name = col_character(),
    ##   ..   start_station_id = col_character(),
    ##   ..   end_station_name = col_character(),
    ##   ..   end_station_id = col_character(),
    ##   ..   start_lat = col_double(),
    ##   ..   start_lng = col_double(),
    ##   ..   end_lat = col_double(),
    ##   ..   end_lng = col_double(),
    ##   ..   member_casual = col_character()
    ##   .. )
    ##  - attr(*, "problems")=<externalptr> 
    ## NULL
    ## spc_tbl_ [537,113 × 13] (S3: spec_tbl_df/tbl_df/tbl/data.frame)
    ##  $ ride_id           : chr [1:537113] "4449097279F8BBE7" "9CF060543CA7B439" "667F21F4D6BDE69C" "F92714CC6B019B96" ...
    ##  $ rideable_type     : chr [1:537113] "classic_bike" "electric_bike" "electric_bike" "classic_bike" ...
    ##  $ started_at        : POSIXct[1:537113], format: "2023-10-08 10:36:26" "2023-10-11 17:23:59" ...
    ##  $ ended_at          : POSIXct[1:537113], format: "2023-10-08 10:49:19" "2023-10-11 17:36:08" ...
    ##  $ start_station_name: chr [1:537113] "Orleans St & Chestnut St (NEXT Apts)" "Desplaines St & Kinzie St" "Orleans St & Chestnut St (NEXT Apts)" "Desplaines St & Kinzie St" ...
    ##  $ start_station_id  : chr [1:537113] "620" "TA1306000003" "620" "TA1306000003" ...
    ##  $ end_station_name  : chr [1:537113] "Sheffield Ave & Webster Ave" "Sheffield Ave & Webster Ave" "Franklin St & Lake St" "Franklin St & Lake St" ...
    ##  $ end_station_id    : chr [1:537113] "TA1309000033" "TA1309000033" "TA1307000111" "TA1307000111" ...
    ##  $ start_lat         : num [1:537113] 41.9 41.9 41.9 41.9 41.9 ...
    ##  $ start_lng         : num [1:537113] -87.6 -87.6 -87.6 -87.6 -87.6 ...
    ##  $ end_lat           : num [1:537113] 41.9 41.9 41.9 41.9 41.9 ...
    ##  $ end_lng           : num [1:537113] -87.7 -87.7 -87.6 -87.6 -87.6 ...
    ##  $ member_casual     : chr [1:537113] "member" "member" "member" "member" ...
    ##  - attr(*, "spec")=
    ##   .. cols(
    ##   ..   ride_id = col_character(),
    ##   ..   rideable_type = col_character(),
    ##   ..   started_at = col_datetime(format = ""),
    ##   ..   ended_at = col_datetime(format = ""),
    ##   ..   start_station_name = col_character(),
    ##   ..   start_station_id = col_character(),
    ##   ..   end_station_name = col_character(),
    ##   ..   end_station_id = col_character(),
    ##   ..   start_lat = col_double(),
    ##   ..   start_lng = col_double(),
    ##   ..   end_lat = col_double(),
    ##   ..   end_lng = col_double(),
    ##   ..   member_casual = col_character()
    ##   .. )
    ##  - attr(*, "problems")=<externalptr> 
    ## NULL
    ## spc_tbl_ [362,518 × 13] (S3: spec_tbl_df/tbl_df/tbl/data.frame)
    ##  $ ride_id           : chr [1:362518] "4EAD8F1AD547356B" "6322270563BF5470" "B37BDE091ECA38E0" "CF0CA5DD26E4F90E" ...
    ##  $ rideable_type     : chr [1:362518] "electric_bike" "electric_bike" "electric_bike" "classic_bike" ...
    ##  $ started_at        : POSIXct[1:362518], format: "2023-11-30 21:50:05" "2023-11-03 09:44:02" ...
    ##  $ ended_at          : POSIXct[1:362518], format: "2023-11-30 22:13:27" "2023-11-03 10:17:15" ...
    ##  $ start_station_name: chr [1:362518] "Millennium Park" "Broadway & Sheridan Rd" "State St & Pearson St" "Theater on the Lake" ...
    ##  $ start_station_id  : chr [1:362518] "13008" "13323" "TA1307000061" "TA1308000001" ...
    ##  $ end_station_name  : chr [1:362518] "Pine Grove Ave & Waveland Ave" "Broadway & Sheridan Rd" "State St & Pearson St" "Theater on the Lake" ...
    ##  $ end_station_id    : chr [1:362518] "TA1307000150" "13323" "TA1307000061" "TA1308000001" ...
    ##  $ start_lat         : num [1:362518] 41.9 42 41.9 41.9 41.9 ...
    ##  $ start_lng         : num [1:362518] -87.6 -87.7 -87.6 -87.6 -87.6 ...
    ##  $ end_lat           : num [1:362518] 41.9 42 41.9 41.9 41.9 ...
    ##  $ end_lng           : num [1:362518] -87.6 -87.6 -87.6 -87.6 -87.6 ...
    ##  $ member_casual     : chr [1:362518] "member" "member" "member" "member" ...
    ##  - attr(*, "spec")=
    ##   .. cols(
    ##   ..   ride_id = col_character(),
    ##   ..   rideable_type = col_character(),
    ##   ..   started_at = col_datetime(format = ""),
    ##   ..   ended_at = col_datetime(format = ""),
    ##   ..   start_station_name = col_character(),
    ##   ..   start_station_id = col_character(),
    ##   ..   end_station_name = col_character(),
    ##   ..   end_station_id = col_character(),
    ##   ..   start_lat = col_double(),
    ##   ..   start_lng = col_double(),
    ##   ..   end_lat = col_double(),
    ##   ..   end_lng = col_double(),
    ##   ..   member_casual = col_character()
    ##   .. )
    ##  - attr(*, "problems")=<externalptr> 
    ## NULL
    ## spc_tbl_ [224,073 × 13] (S3: spec_tbl_df/tbl_df/tbl/data.frame)
    ##  $ ride_id           : chr [1:224073] "C9BD54F578F57246" "CDBD92F067FA620E" "ABC0858E52CBFC84" "F44B6F0E8F76DC90" ...
    ##  $ rideable_type     : chr [1:224073] "electric_bike" "electric_bike" "electric_bike" "electric_bike" ...
    ##  $ started_at        : POSIXct[1:224073], format: "2023-12-02 18:44:01" "2023-12-02 18:48:19" ...
    ##  $ ended_at          : POSIXct[1:224073], format: "2023-12-02 18:47:51" "2023-12-02 18:54:48" ...
    ##  $ start_station_name: chr [1:224073] NA NA NA NA ...
    ##  $ start_station_id  : chr [1:224073] NA NA NA NA ...
    ##  $ end_station_name  : chr [1:224073] NA NA NA NA ...
    ##  $ end_station_id    : chr [1:224073] NA NA NA NA ...
    ##  $ start_lat         : num [1:224073] 41.9 41.9 41.9 42 41.9 ...
    ##  $ start_lng         : num [1:224073] -87.7 -87.7 -87.6 -87.7 -87.6 ...
    ##  $ end_lat           : num [1:224073] 41.9 41.9 41.9 41.9 41.9 ...
    ##  $ end_lng           : num [1:224073] -87.7 -87.6 -87.6 -87.7 -87.6 ...
    ##  $ member_casual     : chr [1:224073] "member" "member" "member" "member" ...
    ##  - attr(*, "spec")=
    ##   .. cols(
    ##   ..   ride_id = col_character(),
    ##   ..   rideable_type = col_character(),
    ##   ..   started_at = col_datetime(format = ""),
    ##   ..   ended_at = col_datetime(format = ""),
    ##   ..   start_station_name = col_character(),
    ##   ..   start_station_id = col_character(),
    ##   ..   end_station_name = col_character(),
    ##   ..   end_station_id = col_character(),
    ##   ..   start_lat = col_double(),
    ##   ..   start_lng = col_double(),
    ##   ..   end_lat = col_double(),
    ##   ..   end_lng = col_double(),
    ##   ..   member_casual = col_character()
    ##   .. )
    ##  - attr(*, "problems")=<externalptr> 
    ## NULL
    ## spc_tbl_ [144,873 × 13] (S3: spec_tbl_df/tbl_df/tbl/data.frame)
    ##  $ ride_id           : chr [1:144873] "C1D650626C8C899A" "EECD38BDB25BFCB0" "F4A9CE78061F17F7" "0A0D9E15EE50B171" ...
    ##  $ rideable_type     : chr [1:144873] "electric_bike" "electric_bike" "electric_bike" "classic_bike" ...
    ##  $ started_at        : POSIXct[1:144873], format: "2024-01-12 15:30:27" "2024-01-08 15:45:46" ...
    ##  $ ended_at          : POSIXct[1:144873], format: "2024-01-12 15:37:59" "2024-01-08 15:52:59" ...
    ##  $ start_station_name: chr [1:144873] "Wells St & Elm St" "Wells St & Elm St" "Wells St & Elm St" "Wells St & Randolph St" ...
    ##  $ start_station_id  : chr [1:144873] "KA1504000135" "KA1504000135" "KA1504000135" "TA1305000030" ...
    ##  $ end_station_name  : chr [1:144873] "Kingsbury St & Kinzie St" "Kingsbury St & Kinzie St" "Kingsbury St & Kinzie St" "Larrabee St & Webster Ave" ...
    ##  $ end_station_id    : chr [1:144873] "KA1503000043" "KA1503000043" "KA1503000043" "13193" ...
    ##  $ start_lat         : num [1:144873] 41.9 41.9 41.9 41.9 41.9 ...
    ##  $ start_lng         : num [1:144873] -87.6 -87.6 -87.6 -87.6 -87.7 ...
    ##  $ end_lat           : num [1:144873] 41.9 41.9 41.9 41.9 41.9 ...
    ##  $ end_lng           : num [1:144873] -87.6 -87.6 -87.6 -87.6 -87.6 ...
    ##  $ member_casual     : chr [1:144873] "member" "member" "member" "member" ...
    ##  - attr(*, "spec")=
    ##   .. cols(
    ##   ..   ride_id = col_character(),
    ##   ..   rideable_type = col_character(),
    ##   ..   started_at = col_datetime(format = ""),
    ##   ..   ended_at = col_datetime(format = ""),
    ##   ..   start_station_name = col_character(),
    ##   ..   start_station_id = col_character(),
    ##   ..   end_station_name = col_character(),
    ##   ..   end_station_id = col_character(),
    ##   ..   start_lat = col_double(),
    ##   ..   start_lng = col_double(),
    ##   ..   end_lat = col_double(),
    ##   ..   end_lng = col_double(),
    ##   ..   member_casual = col_character()
    ##   .. )
    ##  - attr(*, "problems")=<externalptr> 
    ## NULL

Sobre a credibilidade dos dados coletados:

Os dados são confiáveis, uma vez que um registro detalhado da população
foi mantido nos últimos doze meses em um sistema dedicado. O numero
consistente de viagens de bicicleta registradas, variando de um máximo
de 823.488 a um mínimo de 181.806 em diferentes meses, suporta a
confiabilidade da coleta de dados.

Os dados são originais, uma vez que provem diretamente dos dispositivos
incorporados nas bicicletas, o que garante a autenticidade e a
pontualidade dos dados. Ao obter os dados diretamente da empresa, são
evitadas possíveis manipula??es ou erros de terceiros.

Os dados são completos e bem estruturados, como todas as variáveis
relevantes para a análise estão incluídas, como identificação do
usuário, tipo de bicicleta, tempo de viagem e tipo de membro. Embora
existam dados adicionais de latitude e longitude, reconhece-se que eles
não são necessários para a análise específica realizada.

Os dados são atuais, desde que as viagens de bicicleta dos últimos doze
meses foram coletadas e analisadas, de julho de 2022 a junho de 2023.
Isso garante que a análise reflita a situa??o atual e recente dos
padrões de uso de bicicletas.

Processo Para começar a limpar os dados? necessário verificar os nomes
das colunas e os formatos usados. Isso me permitir? mesclar as
informa??es em um único dataframe e, assim, facilitar tanto o processo
de limpeza quanto a análise.

Verificando as colunas

``` r
## Iterar sobre a lista e obter os nomes das colunas
for (df in bike_trips_list) {
  
  print(colnames(df))
}
```

    ##  [1] "ride_id"            "rideable_type"      "started_at"        
    ##  [4] "ended_at"           "start_station_name" "start_station_id"  
    ##  [7] "end_station_name"   "end_station_id"     "start_lat"         
    ## [10] "start_lng"          "end_lat"            "end_lng"           
    ## [13] "member_casual"     
    ##  [1] "ride_id"            "rideable_type"      "started_at"        
    ##  [4] "ended_at"           "start_station_name" "start_station_id"  
    ##  [7] "end_station_name"   "end_station_id"     "start_lat"         
    ## [10] "start_lng"          "end_lat"            "end_lng"           
    ## [13] "member_casual"     
    ##  [1] "ride_id"            "rideable_type"      "started_at"        
    ##  [4] "ended_at"           "start_station_name" "start_station_id"  
    ##  [7] "end_station_name"   "end_station_id"     "start_lat"         
    ## [10] "start_lng"          "end_lat"            "end_lng"           
    ## [13] "member_casual"     
    ##  [1] "ride_id"            "rideable_type"      "started_at"        
    ##  [4] "ended_at"           "start_station_name" "start_station_id"  
    ##  [7] "end_station_name"   "end_station_id"     "start_lat"         
    ## [10] "start_lng"          "end_lat"            "end_lng"           
    ## [13] "member_casual"     
    ##  [1] "ride_id"            "rideable_type"      "started_at"        
    ##  [4] "ended_at"           "start_station_name" "start_station_id"  
    ##  [7] "end_station_name"   "end_station_id"     "start_lat"         
    ## [10] "start_lng"          "end_lat"            "end_lng"           
    ## [13] "member_casual"     
    ##  [1] "ride_id"            "rideable_type"      "started_at"        
    ##  [4] "ended_at"           "start_station_name" "start_station_id"  
    ##  [7] "end_station_name"   "end_station_id"     "start_lat"         
    ## [10] "start_lng"          "end_lat"            "end_lng"           
    ## [13] "member_casual"     
    ##  [1] "ride_id"            "rideable_type"      "started_at"        
    ##  [4] "ended_at"           "start_station_name" "start_station_id"  
    ##  [7] "end_station_name"   "end_station_id"     "start_lat"         
    ## [10] "start_lng"          "end_lat"            "end_lng"           
    ## [13] "member_casual"     
    ##  [1] "ride_id"            "rideable_type"      "started_at"        
    ##  [4] "ended_at"           "start_station_name" "start_station_id"  
    ##  [7] "end_station_name"   "end_station_id"     "start_lat"         
    ## [10] "start_lng"          "end_lat"            "end_lng"           
    ## [13] "member_casual"     
    ##  [1] "ride_id"            "rideable_type"      "started_at"        
    ##  [4] "ended_at"           "start_station_name" "start_station_id"  
    ##  [7] "end_station_name"   "end_station_id"     "start_lat"         
    ## [10] "start_lng"          "end_lat"            "end_lng"           
    ## [13] "member_casual"     
    ##  [1] "ride_id"            "rideable_type"      "started_at"        
    ##  [4] "ended_at"           "start_station_name" "start_station_id"  
    ##  [7] "end_station_name"   "end_station_id"     "start_lat"         
    ## [10] "start_lng"          "end_lat"            "end_lng"           
    ## [13] "member_casual"     
    ##  [1] "ride_id"            "rideable_type"      "started_at"        
    ##  [4] "ended_at"           "start_station_name" "start_station_id"  
    ##  [7] "end_station_name"   "end_station_id"     "start_lat"         
    ## [10] "start_lng"          "end_lat"            "end_lng"           
    ## [13] "member_casual"     
    ##  [1] "ride_id"            "rideable_type"      "started_at"        
    ##  [4] "ended_at"           "start_station_name" "start_station_id"  
    ##  [7] "end_station_name"   "end_station_id"     "start_lat"         
    ## [10] "start_lng"          "end_lat"            "end_lng"           
    ## [13] "member_casual"     
    ##  [1] "ride_id"            "rideable_type"      "started_at"        
    ##  [4] "ended_at"           "start_station_name" "start_station_id"  
    ##  [7] "end_station_name"   "end_station_id"     "start_lat"         
    ## [10] "start_lng"          "end_lat"            "end_lng"           
    ## [13] "member_casual"     
    ##  [1] "ride_id"            "rideable_type"      "started_at"        
    ##  [4] "ended_at"           "start_station_name" "start_station_id"  
    ##  [7] "end_station_name"   "end_station_id"     "start_lat"         
    ## [10] "start_lng"          "end_lat"            "end_lng"           
    ## [13] "member_casual"

Empilhando todos os dataframen em um

``` r
all_bike_trips <- bind_rows(bike_trips_list)
```

Um Único dataframe de 6.123.428 registros obtidos

Selecionando colunas de interesse

``` r
bike_trips_df <- all_bike_trips %>%
  select(-c(start_lat,start_lng,end_lat,end_lng))
```

Verificando os valores na, nas colunas start\_station\_name,
start\_station\_id, end\_station\_name e end\_station\_id

``` r
na_start_station_name <- bike_trips_df %>% 
  filter(is.na(start_station_name))
```

Embora existam valores nulos nas quatro colunas, isso não afeta a
análise, eu os mantenho.

Valores duplicados excluídos em juncos e atributos

``` r
all_bike_trips_df <- bike_trips_df %>%
  distinct(.keep_all = FALSE)
```

Nenhuma linha foi excluída porque cada registro é Único

Agregação de informações ride\_length em formato numérico

``` r
all_bike_trips_df <- all_bike_trips_df %>%
  mutate(ride_length_sec = difftime(ended_at, started_at, units = "secs" ) )
```

Converter a variável ride\_length do formato “time” para o formato
“numérico”

``` r
all_bike_trips_df <- all_bike_trips_df %>%
  mutate(ride_length_sec = as.numeric(ride_length_sec))
```

Estou procurando valores que não atendam aos valores esperados da coluna
ride\_length que devem ser positivos e numéricos.

``` r
negative_ride_length_df <- 
  all_bike_trips_df[!grepl("^[0-9*\\.?[0-9]+$", all_bike_trips_df$ride_length_sec), ]
```

Apareceram valores negativos que não cumprem a validação

Eu crio um novo df com o filtro aplicado, removendo os valores
negativos, chamados bike\_share\_data, este será o df para análise.

``` r
bike_share_data <- all_bike_trips_df %>%
  filter(ride_length_sec > 0)
```

Converter a duração das viagens de segundos para horas

``` r
bike_share_data <- bike_share_data %>%
  mutate(ride_length_min = ride_length_sec/60)
```

Analizar Qual é a porcentagem atual de ciclistas casuais e membros
anuais do total de usuários de bicicletas compartilhadas?

``` r
summary_bike_share_user_percet <- bike_share_data %>%
  group_by(member_casual) %>%
  summarize(num_user =  n(), percet = (n()/sum(nrow(bike_share_data)))*100, .groups = "drop" )
```

O percentual atual de ciclistas membros é de 64,5% e o percentual de
ciclistas casuais é de 35.5%

Quais são as principais diferenças no uso de bicicletas ciclísticas
entre motociclistas casuais e membros anuais? Em relação a:

Use o tempo por tipo de usuário.

Remover o tempo médio, máximo e mínimo de uso por membros e ciclistas
ocasionais

``` r
summary_bike_share_ride_length <- bike_share_data %>%
  group_by(member_casual) %>%
  summarize(avg_length_time = mean(ride_length_min), max_length_time = max(ride_length_min),
            min_lenght_time =  min(ride_length_min),median_length_min = median(ride_length_min) )
```

Aqui pode-se ver que os ciclistas casuais tem um tempo médio de uso
maior do que o dos ciclistas membros. Os valores máximos no grupo casual
são notavelmente altos, o que pode ser devido a casos atípicos ou
eventos excepcionais. Da mesma forma, deve-se considerar a possibilidade
de valores mínimos causados por situações acidentais.

? importante realizar uma análise de valores atípicos para avaliar a
influência desses casos extremos nas conclusões. Da mesma forma, pode-se
ver que menos de 50% dos ciclistas casuais tem tempos de uso de pelo
menos 11 minutos, enquanto no caso dos membros, 50% Tem um tempo de uso
de menos de 8,4 minutos, sugerindo uma clara diferença nos padrões de
uso entre os dois grupos.

O tempo de uso parece ser mais longo em ciclistas casuais em comparação
com os membros, o que poderia indicar que os primeiros usam bicicletas
compartilhadas por períodos mais longos, enquanto os membros podem fazer
uso de bicicletas para rotas mais curtas.

``` r
# Identificar linhas com valores ausentes em 'started_at'
missing_rows <- which(is.na(bike_share_data$started_at))

# Criar um novo conjunto de dados excluindo linhas com valores ausentes
bike_share_data_filtered <- bike_share_data[-missing_rows, ]

# Extrair o dia da semana (assumindo que 'started_at' é uma coluna de data e hora)
bike_share_data_filtered$day_of_week <- weekdays(bike_share_data_filtered$started_at)
```

Intervalo de tempo em que utilizam o serviço

Gerando uma nova coluna e reorganizando os dias

``` r
#Criando a columna
bike_share_data <- mutate(bike_share_data,day_of_week = weekdays(started_at))
```

’’’Esta parte do código apresenta falhas na hora de mostrar os dias da
semana de segunda a sexta, só mostra sábado e domingo na coluna
bike\_share\_data

\#ordenando
bike\_share\_data$day_of_week <- factor(bike_share_data$day\_of\_week,
levels = c(“domingo”, “segunda”, “ter?a”,
“quarta”,“quinta”,“sexta”,“s?bado”))’’’ O que eu fiz foi substituir esta
parte pelo código abaixo que após aparece os dias da semana
corretamente’’’

``` r
# Convertendo a coluna started_at para um objeto date
bike_share_data$started_at <- ymd_hms(bike_share_data$started_at)
```

    ## Warning: 24 failed to parse.

``` r
# Extraindo o dia da semana
bike_share_data$day_of_week <- weekdays(bike_share_data$started_at)

# Formatando o dia da semana em portugu?s, nao precisou fazer isso e tambem da erro 
#bike_share_data$day_of_week_pt <- format(bike_share_data$day_of_week, "%A", trim = FALSE)
```

Calculando a duração média, por dia da semana, por tipo de usuário

``` r
summary_bike_share_avg_time_day <- bike_share_data %>%
  group_by(member_casual, day_of_week) %>%
  summarize(avg_length_min = mean(ride_length_min), .groups = "drop") 
```

Pode-se ver que o tempo médio de uso para usuários casuais são maiores
aos Domingos, Sábados, Segundas e Sextas-feiras. Por outro lado, os
membros têm um maior tempo médio de uso aos Sábados, Domingos, Segunda e
Sextas-feiras.

Esta tendência sugere que os usuários casuais tendem a usar bicicletas
compartilhadas mais no fim de semana e nos primeiros dias da semana,
possivelmente para atividades recreativas ou turísticas. Enquanto isso,
os membros fazem uso mais constante durante os dias da semana e fins de
semana, o que pode estar relacionado ao seu uso para o deslocamento
diário ou atividades regulares.

Quais slots do dia, os clientes casuais e os membros usam?

``` r
# Definir função para obter o rótulo do intervalo de tempo
franja_dia <- function(hour) {
  case_when(
    hour >= 0 & hour < 6 ~ "madrugada",
    hour >= 6 & hour < 12 ~ "manha",
    hour >= 12 & hour < 18 ~ "tarde",
    TRUE ~ "noite"
  )
}


# Criar a coluna de horas com as horas do dia
bike_share_data <- bike_share_data %>%
  mutate(hour = hour(started_at))

# Criar a coluna time_slot com os rótulos de intervalo(franja) de tempo
bike_share_data <- bike_share_data %>%
  mutate(horario = franja_dia(hour))

#ordenadp
bike_share_data$horario <- factor(bike_share_data$horario , levels = c("madrugada", "manha", "tarde", "noite"))

# Calcular a viagem média por faixa horária e tipo de usuário
summary_bike_share_data_franja <- bike_share_data %>%
  group_by(member_casual,horario) %>%
  summarize(avg_ride_length_min = mean(ride_length_min), .groups = "drop")
```

Em relação ao dia, os ciclistas casuais têm um tempo médio de uso mais
longo pela madrugada, e a tarde. Por outro lado, os membros têm uma
duração média da viagem mais constante tendo pouca alteração no fluxo
independente do horário, com seu maior pico sendo durante a tarde.

Visualizar

Visualizando o numero de viagens por dia por tipo de usuário e Tipo de
Bicicleta

``` r
ggplot(data = bike_share_data) + 
  geom_bar(mapping = aes( x = day_of_week, fill = rideable_type )) + 
  facet_wrap(~member_casual) +
  theme(axis.text.x = element_text(angle = 45, hjust = 1, vjust = 1)) + 
  labs(title = "Numero de viagens por dia por tipo de usuário e Tipo de bicicleta", 
       x = "Dia da semana", y ="Numero de viagens", fill = "Tipo de Bicicleta") 
```

![](Vizualizacao-de-dados-Cyclitc-2024_files/figure-gfm/unnamed-chunk-23-1.png)<!-- -->
A análise dos dados mostra padrões interessantes no uso de bicicletas
compartilhadas por clientes e membros casuais. Pode-se ver que:

Os dias com o maior numero de viagens casuais de clientes são Sábados e
Domingos, enquanto os clientes membros fazem mais viagens ás Terça,
Quartas e Quintas-feiras. Essa diferença nos dias de pico sugere que os
clientes casuais tendem a usar bicicletas compartilhadas com mais
frequência em fins de semana não funcionais, possivelmente para
atividades recreativas ou turísticas, enquanto os clientes membros os
usam mais para o deslocamento durante a semana.

Clientes casuais mostram uma preferência por bicicletas elétricas em
comparação com bicicletas de estação e bicicletas clássicas. Por outro
lado, os clientes membros usam bicicletas clássicas e elétricas, mas não
usam bicicletas de estação. Essa diferença de preferencias pode estar
relacionada á maior flexibilidade que as bicicletas elétricas oferecem
para percorrer distancias maiores e facilitar a viagem em terrenos
difíceis.

A observação do uso de bicicletas de estação pode indicar que os
clientes membros preferem a conveniência de estacionar perto de seu
destino, o que é possível com bicicletas clássicas e elétricas que podem
ser deixadas em locais permitidos. Em vez disso, as bicicletas de
estação exigiriam retornar a uma estação específica, o que pode ser
menos conveniente para alguns usuários.

Visualizando o numero de viagens por dia e Tipo de usuário

``` r
ggplot(data = bike_share_data) + 
  geom_bar(mapping = aes( x = horario, fill = member_casual )) + 
  facet_wrap(~member_casual) +
  theme(axis.text.x = element_text(angle = 45, hjust = 1, vjust = 1)) + 
  labs(title = "Numero de viagens por Jornada do dia e Tipo de usuário",
       x = "Dia da semana", y ="Número de viagens", fill = "Tipo de Usuário") 
```

![](Vizualizacao-de-dados-Cyclitc-2024_files/figure-gfm/unnamed-chunk-24-1.png)<!-- -->

Pode-se afirmar que:

Clientes casuais tendem a fazer a maior parte de suas viagens á tarde,
seguidos de noite e manhã? Isso sugere que clientes casuais usam
bicicletas compartilhadas principalmente para lazer ou recreação durante
as horas da tarde e da noite.

Por outro lado, os clientes membros fazem a maioria de suas viagens?
tarde, seguidas de manhã? e noite. Essa diferença nos padrões de uso
entre clientes casuais e membros pode ser devido ao fato de que os
clientes membros usam bicicletas compartilhadas com mais frequência para
deslocamento e atividades diárias durante o horário de pico atividade de
trabalho e deslocamento.

Exibição do tempo de uso e tipo de usuário

``` r
ggplot(data = bike_share_data) +
  geom_jitter(mapping = aes(x=ride_length_sec, y = member_casual)) +
  labs(title = "Tempo de uso e Tipo de usuário", x = "Tempo de uso (Seg)",
       y = "Tipo de Usuário", caption = "Dados: Desde 01 2023 há 01 2024") 
```

![](Vizualizacao-de-dados-Cyclitc-2024_files/figure-gfm/unnamed-chunk-25-1.png)<!-- -->
Em geral, podemos ver que, embora a porcentagem atual de ciclistas
membros seja de 61,17% e a porcentagem de viajantes casuais seja de
38,83%, a%, os usuários casuais têm durações de viagem muito mais longas
em comparação com os ciclistas membros.

Ciclistas casuais:

Dados atípicos são identificados entre ciclistas casuais com uma duração
de viagem de aproximadamente 28 dias (2500000 segundos). Essa duração
extremamente longa pode ser o resultado de um erro de registro ou de uma
jornada excepcionalmente longa, e é necessária uma investigação mais
aprofundada desse valor para determinar sua validade.

Há outro grupo de dados com durações de viagem entre 12 dias (1000000
segundos) e 24 dias (2000000 segundos). Essas durações sugerem que
alguns usuários casuais usam bicicletas compartilhadas para viagens de
vários dias, o que pode estar relacionado a longas atividades turísticas
ou recreativas.

Há também um grupo considerável de ciclistas casuais que alugam
bicicletas para viagens de 6 dias (500.000 segundos) a 12 dias. Isso
indica que alguns usuários casuais preferem usar bicicletas
compartilhadas para viagens mais longas, mas não tanto quanto o grupo
anterior.

A maioria dos pontos de dados estão concentrada em durações de viagem
inferiores a 6 dias (500.000 segundos). Isso sugere que a maioria dos
usuários casuais fazem viagens mais curtas e rápidas, o que apoia a
ideia de que eles usam bicicletas compartilhadas para atividades de
lazer e deslocamento dentro da cidade.

Ciclistas membros:

Em contraste, a duração da viagem para os ciclistas membros á mais
curta, com um limite inferior de 3 dias (250.000 segundos). Isso indica
que os membros usam bicicletas compartilhadas principalmente para
viagens mais curtas e pontuais, como deslocamento para o trabalho ou
atividades diárias.

Destaca-se que a duração da viagem para os ciclistas membros está
concentrada principalmente em um único dia. Isso apoia a ideia de que os
membros usam bicicletas compartilhadas para deslocamentos diários e se
beneficiam da conveniência e eficiência do serviço para seus
deslocamentos.

Visualização do tempo médio de uso por dia por tipo de usuário:

``` r
ggplot(data = summary_bike_share_avg_time_day) +
  geom_col(mapping = aes(x=day_of_week, y=  avg_length_min )) + 
  facet_wrap(~member_casual) + 
  theme(axis.text.x = element_text(angle = 45, hjust = 1, vjust = 1)) +
  labs(x = "Dias da semana", y = "Tempo médio de uso (min)",
       title ="Tempo médio de uso por Dia por Tipo de usuário", 
       caption = "Dados: Desde 01 2023 há 01 2024")
```

![](Vizualizacao-de-dados-Cyclitc-2024_files/figure-gfm/unnamed-chunk-26-1.png)<!-- -->

A visualização mostra claramente que os ciclistas casuais têm um tempo
médio de uso mais longo aos domingos, sábados, segundas e sextas-feiras.
Por outro lado, os ciclistas membros tem um tempo médio de uso mais
longo aos sábados, domingos e sextas-feiras.

Essa análise nos permite inferir que ciclistas casuais tendem a usar
bicicletas compartilhadas nos finais de semana e no início da semana de
trabalho para fazer viagens mais longas e mais longas.

Para os ciclistas membros, uma tendência semelhante também à observada
nos finais de semana e nos dias de trabalho anteriores ao fim de semana.
Os membros também podem usar bicicletas compartilhadas para lazer ou
recreação durante os dias de descanso.

Lei Ver Apresentação para Partes Interessadas Principais descobertas
Distribuição de Usuários: Durante o período analisado, aproximadamente
39% dos usuários são ciclistas casuais (usuários ocasionais) e 61% são
associados anuais. Isso indica que a maioria dos usuários são membros
recorrentes, representando uma oportunidade para o Cyclistic aumentar a
base anual de membros.

Duração Média da Viagem: Os ciclistas casuais tendem a fazer viagens
mais longas, em média, com uma duração média de aproximadamente 28
minutos. Por outro lado, os membros anuais fazem viagens mais curtas, em
média, com uma duração média de aproximadamente 12 minutos. Esta
diferença sugere que os ciclistas ocasionais usam o serviço
principalmente para atividades de lazer ou deslocamento mais longo,
enquanto os membros fazem viagens mais curtas e mais frequentes,
possivelmente como parte de sua rotina diária.

Distribuição Semanal de Uso: Ciclistas casuais tendem a usar o serviço
mais nos fins de semana (Sábado e Domingo), com um pico de uso aos
sábados. Por outro lado, os associados anuais utilizam mais o serviço
durante os dias úteis (Segunda a Sexta-feira), com um aumento no uso às
Quintas-feiras. Esta diferença na distribuição de uso semanal pode estar
relacionada com as diferentes finalidades de uso dos dois grupos de
usuários: Ciclistas casuais usam mais para atividades de lazer nos fins
de semana, enquanto os membros usam mais para o deslocamento diário
durante os dias úteis.

Distribuição Diária de Uso: Ciclistas casuais mostram um padrão de uso
mais uniforme durante o dia, com um ligeiro aumento no uso durante a
tarde e á noite. Por outro lado, os membros anuais têm um uso mais
pronunciado durante as horas de pico da manhã e da tarde, com uma
diminuição no uso á noite. Isso sugere que os membros usam bicicletas
compartilhadas para seus deslocamentos diários, enquanto os ciclistas
casuais as usam mais dispersas ao longo do dia, possivelmente para
atividades recreativas.

Uso por Time Strip: Analisando o tempo médio de uso por intervalo de
tempo, observa-se que ciclistas casuais e membros anuais usam mais
bicicletas compartilhadas durante o início da manhã? e da tarde. Os
ciclistas casuais tem um tempo médio de uso mais longo no início da
manhã, seguido pela tarde e noite. Por outro lado, os membros têm um
tempo mio de uso mais longo á noite, seguido de manhã. Isso pode indicar
que ciclistas casuais tendem a usar bicicletas principalmente durante as
primeiras horas do dia e durante a tarde e a noite, possivelmente para
atividades de lazer ou viagens mais longas. Enquanto os membros fazem
mais uso de bicicletas compartilhadas á noite e no início do dia,
possivelmente para viagens diárias e atividades dirias.

Preferência de Ciclo: Ciclistas ocasionais mostram uma clara preferência
por bicicletas elétricas, seguidas por bicicletas clássicas, enquanto
mostram menor uso de bicicletas de estação. Por outro lado, os ciclistas
membros mostram uma preferência diversificada, usando bicicletas
elétricas e clássicas.

Recomendações Promoções Especiais para Ciclistas Ocasionais: A Cyclistic
pode oferecer promoções e descontos exclusivos para ciclistas casuais
nos fins de semana. Por exemplo, eles poderiam oferecer associações
anuais a uma taxa reduzida ou com benefícios adicionais, como minutos
gratuitos a cada mês. Essa estratégia visa incentivar os ciclistas
casuais a se envolverem no longo prazo e aproveitar os benefícios de
serem membros anuais.

Programa de Fidelidade: Implemente um programa de fidelidade que
recompense os ciclistas casuais por se tornarem membros anuais e por
usarem o serviço com frequência. Por exemplo, o Cyclistic pode oferecer
pontos de recompensa para cada viagem como um ciclista ocasional e
permitir que eles resgatem esses pontos para descontos em associação
anual ou viagens futuras.

Experiência do Usuário Melhorada: Certifique-se de que a experiência do
usuário para membros anuais seja excepcional. O ciclista deve garantir
que as bicicletas estejam em boas condições, bem conservadas e, o mais
importante, de acordo com os dados, elas estão melhorando a distribuição
dos locais das estações, Como as bicicletas de estação são pouco usadas,
isso pode ser melhorado, tornando uma melhor distribuição na cidade,
muito conveniente para os usuários.
