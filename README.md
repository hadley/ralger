
<!-- README.md is generated from README.Rmd. Please edit that file -->

# ralger <a><img src='man/figures/hex.png' align="right" height="200" /></a>

<!-- badges: start -->

<!-- badges: end -->

The goal of **ralger** is to facilitate web scraping in R.

## Installation

You can install the development version from
[GitHub](https://github.com/) with:

``` r
# install.packages("devtools")
devtools::install_github("feddelegrand7/ralger")
```

## Example

This is an example which shows how to extract firms’ denomination from
the website of the Algerian Chamber of Commerce and Industry (CACI). For
simplicity, we’ll focus on firms operating within the capital (Alger).

``` r
library(ralger)

my_link <- "http://elmouchir.caci.dz/search_results.php?keyword=&category=&location=Alger&submit=Trouver"

my_node <- ".listing_default" # see SelectorGadget

scrap_this(my_link, my_node)
#>  [1] "Adjerid Hanifa"                                                               
#>  [2] "Dar Chamila"                                                                  
#>  [3] "SAMRIA AUTO / Salon Algerian du Materiel Roulant et de L'industrie Automobile"
#>  [4] "YOUKAIS"                                                                      
#>  [5] "EDIMETAL"                                                                     
#>  [6] "SYRIAN AIR LINES"                                                             
#>  [7] "Turkish Airlines / Direction Générale"                                        
#>  [8] "Aigle Azur / Agence Didouche Mourad"                                          
#>  [9] "British Airways"                                                              
#> [10] "DELTA"                                                                        
#> [11] "Cabinet Ammiche Amer"                                                         
#> [12] "VERITEX"                                                                      
#> [13] "Kermiche Partener"                                                            
#> [14] "Entreprise d'Architecture Aurea"                                              
#> [15] "PROGOS"                                                                       
#> [16] "Ambassade du Royaume d'Arabie Saoudite"                                       
#> [17] "Ambassade de la République d'Argentine"                                       
#> [18] "Ambassade du Burkina Faso"                                                    
#> [19] "Ambassade du Canada"                                                          
#> [20] "Ambassade de la République de Corée"
```

If you want to scrap multiple list pages, just use `scrap_this()` in
conjunction with `paste()`. Suppose, we want to extract the above
information from the first 3 pages (starts from 0):

``` r
my_link <- "http://elmouchir.caci.dz/search_results.php?keyword=&category=&location=Alger&submit=Trouver&page=" 

my_node <- ".listing_default"

scrap_this(paste(my_link, 0:2), my_node)
#>  [1] "ALTRUCK"                                                                    
#>  [2] "GFC Négoce"                                                                 
#>  [3] "Esasoud Welding And Cutting"                                                
#>  [4] "Huan Yu"                                                                    
#>  [5] "HRLI"                                                                       
#>  [6] "Dar El Hikma"                                                               
#>  [7] "Trans Canal Centre / Khemis El Khechna"                                     
#>  [8] "Direction Régionale Centre / Ex Trans Canal Centre"                         
#>  [9] "Egt Sidi Fredj / Club Azur Plage"                                           
#> [10] "EGT Zeralda / Entreprise de Gestion Touristique de Zeralda"                 
#> [11] "SPE / Sociéte Algérienne de Production d’Electricité"                       
#> [12] "GRTG / Société Algérienne de Gestion du Réseau de Transport  de Gaz"        
#> [13] "GRTE  / Société Algérienne de Gestion du Réseau de Transport de Electricité"
#> [14] "Clef du Sud"                                                                
#> [15] "Adrien.Dz"                                                                  
#> [16] "MPV"                                                                        
#> [17] "SCAL / La Société des Ciments de l'Algérois"                                
#> [18] "EVSM / Entreprise de Viabilisation de Sidi Moussa"                          
#> [19] "Chambre d'Agriculture de la Wilaya d'Alger / CNA"                           
#> [20] "VERITAL/ Direction Générale"                                                
#> [21] "ALTRUCK"                                                                    
#> [22] "GFC Négoce"                                                                 
#> [23] "Esasoud Welding And Cutting"                                                
#> [24] "Huan Yu"                                                                    
#> [25] "HRLI"                                                                       
#> [26] "Dar El Hikma"                                                               
#> [27] "Trans Canal Centre / Khemis El Khechna"                                     
#> [28] "Direction Régionale Centre / Ex Trans Canal Centre"                         
#> [29] "Egt Sidi Fredj / Club Azur Plage"                                           
#> [30] "EGT Zeralda / Entreprise de Gestion Touristique de Zeralda"                 
#> [31] "SPE / Sociéte Algérienne de Production d’Electricité"                       
#> [32] "GRTG / Société Algérienne de Gestion du Réseau de Transport  de Gaz"        
#> [33] "GRTE  / Société Algérienne de Gestion du Réseau de Transport de Electricité"
#> [34] "Clef du Sud"                                                                
#> [35] "Adrien.Dz"                                                                  
#> [36] "MPV"                                                                        
#> [37] "SCAL / La Société des Ciments de l'Algérois"                                
#> [38] "EVSM / Entreprise de Viabilisation de Sidi Moussa"                          
#> [39] "Chambre d'Agriculture de la Wilaya d'Alger / CNA"                           
#> [40] "VERITAL/ Direction Générale"                                                
#> [41] "ALTRUCK"                                                                    
#> [42] "GFC Négoce"                                                                 
#> [43] "Esasoud Welding And Cutting"                                                
#> [44] "Huan Yu"                                                                    
#> [45] "HRLI"                                                                       
#> [46] "Dar El Hikma"                                                               
#> [47] "Trans Canal Centre / Khemis El Khechna"                                     
#> [48] "Direction Régionale Centre / Ex Trans Canal Centre"                         
#> [49] "Egt Sidi Fredj / Club Azur Plage"                                           
#> [50] "EGT Zeralda / Entreprise de Gestion Touristique de Zeralda"                 
#> [51] "SPE / Sociéte Algérienne de Production d’Electricité"                       
#> [52] "GRTG / Société Algérienne de Gestion du Réseau de Transport  de Gaz"        
#> [53] "GRTE  / Société Algérienne de Gestion du Réseau de Transport de Electricité"
#> [54] "Clef du Sud"                                                                
#> [55] "Adrien.Dz"                                                                  
#> [56] "MPV"                                                                        
#> [57] "SCAL / La Société des Ciments de l'Algérois"                                
#> [58] "EVSM / Entreprise de Viabilisation de Sidi Moussa"                          
#> [59] "Chambre d'Agriculture de la Wilaya d'Alger / CNA"                           
#> [60] "VERITAL/ Direction Générale"
```

I appreciate any feedback, please reach out or DM at
[ihaddadenfodil](https://twitter.com/IhaddadenFodil).
