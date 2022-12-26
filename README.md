# PredictorPesoPinguinos2022

Pingüinos palmerinos
El objetivo de los pingüinos palmeres es proporcionar un gran conjunto de datos para la exploración y visualización de datos, como alternativa a .iris

![image](https://user-images.githubusercontent.com/100862089/209541931-10eb21ef-faf5-4c23-b6a9-69ca319e15a2.png)

Instalación
Puede instalar la versión lanzada de palmerpenguins de CRAN con:

install.packages("palmerpenguins")
Para instalar la versión de desarrollo desde GitHub, use:

# install.packages("remotes")
remotes::install_github("allisonhorst/palmerpenguins")
Acerca de los datos
Kristen Gorman y la Estación Palmer, Antártida LTER, miembro de la Red de Investigación Ecológica a Largo Plazo.

El paquete palmerpenguins contiene dos conjuntos de datos.

library(palmerpenguins)
data(package = 'palmerpenguins')
Uno se llama , y es una versión simplificada de los datos sin procesar; Consulte para obtener más información:penguins?penguins

head(penguins)
#> # A tibble: 6 × 8
#>   species island bill_length_mm bill_depth_mm flipper_length_… body_mass_g sex  
#>   <fct>   <fct>           <dbl>         <dbl>            <int>       <int> <fct>
#> 1 Adelie  Torge…           39.1          18.7              181        3750 male 
#> 2 Adelie  Torge…           39.5          17.4              186        3800 fema…
#> 3 Adelie  Torge…           40.3          18                195        3250 fema…
#> 4 Adelie  Torge…           NA            NA                 NA          NA <NA> 
#> 5 Adelie  Torge…           36.7          19.3              193        3450 fema…
#> 6 Adelie  Torge…           39.3          20.6              190        3650 male 
#> # … with 1 more variable: year <int>
El segundo conjunto de datos es , y contiene todas las variables y nombres originales tal como se descargaron; Consulte para obtener más información.penguins_raw?penguins_raw

head(penguins_raw)
#> # A tibble: 6 × 17
#>   studyName `Sample Number` Species          Region Island Stage `Individual ID`
#>   <chr>               <dbl> <chr>            <chr>  <chr>  <chr> <chr>          
#> 1 PAL0708                 1 Adelie Penguin … Anvers Torge… Adul… N1A1           
#> 2 PAL0708                 2 Adelie Penguin … Anvers Torge… Adul… N1A2           
#> 3 PAL0708                 3 Adelie Penguin … Anvers Torge… Adul… N2A1           
#> 4 PAL0708                 4 Adelie Penguin … Anvers Torge… Adul… N2A2           
#> 5 PAL0708                 5 Adelie Penguin … Anvers Torge… Adul… N3A1           
#> 6 PAL0708                 6 Adelie Penguin … Anvers Torge… Adul… N3A2           
#> # … with 10 more variables: `Clutch Completion` <chr>, `Date Egg` <date>,
#> #   `Culmen Length (mm)` <dbl>, `Culmen Depth (mm)` <dbl>,
#> #   `Flipper Length (mm)` <dbl>, `Body Mass (g)` <dbl>, Sex <chr>,
#> #   `Delta 15 N (o/oo)` <dbl>, `Delta 13 C (o/oo)` <dbl>, Comments <chr>
Ambos conjuntos de datos contienen datos de 344 pingüinos. Hay 3 especies diferentes de pingüinos en este conjunto de datos, recolectados de 3 islas en el archipiélago Palmer, Antártida.

str(penguins)
#> tibble [344 × 8] (S3: tbl_df/tbl/data.frame)
#>  $ species          : Factor w/ 3 levels "Adelie","Chinstrap",..: 1 1 1 1 1 1 1 1 1 1 ...
#>  $ island           : Factor w/ 3 levels "Biscoe","Dream",..: 3 3 3 3 3 3 3 3 3 3 ...
#>  $ bill_length_mm   : num [1:344] 39.1 39.5 40.3 NA 36.7 39.3 38.9 39.2 34.1 42 ...
#>  $ bill_depth_mm    : num [1:344] 18.7 17.4 18 NA 19.3 20.6 17.8 19.6 18.1 20.2 ...
#>  $ flipper_length_mm: int [1:344] 181 186 195 NA 193 190 181 195 193 190 ...
#>  $ body_mass_g      : int [1:344] 3750 3800 3250 NA 3450 3650 3625 4675 3475 4250 ...
#>  $ sex              : Factor w/ 2 levels "female","male": 2 1 1 NA 1 2 1 2 NA NA ...
#>  $ year             : int [1:344] 2007 2007 2007 2007 2007 2007 2007 2007 2007 2007 ...
Agradecemos a Palmer Station LTER y a la red LTER de EE. UU. Un agradecimiento especial a Marty Downs (Director, LTER Network Office) por su ayuda con respecto a la licencia y el uso de datos.

Ejemplos
Puede encontrar estos y más ejemplos de código para explorar los pingüinos palmereros en .vignette("examples")

¡Los pingüinos son divertidos de resumir! Por ejemplo:

library(tidyverse)
penguins %>% 
  count(species)
#> # A tibble: 3 × 2
#>   species       n
#>   <fct>     <int>
#> 1 Adelie      152
#> 2 Chinstrap    68
#> 3 Gentoo      124
penguins %>% 
  group_by(species) %>% 
  summarize(across(where(is.numeric), mean, na.rm = TRUE))
#> # A tibble: 3 × 6
#>   species   bill_length_mm bill_depth_mm flipper_length_mm body_mass_g  year
#>   <fct>              <dbl>         <dbl>             <dbl>       <dbl> <dbl>
#> 1 Adelie              38.8          18.3              190.       3701. 2008.
#> 2 Chinstrap           48.8          18.4              196.       3733. 2008.
#> 3 Gentoo              47.5          15.0              217.       5076. 2008.

