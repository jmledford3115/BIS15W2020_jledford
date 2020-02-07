---
title: "Lab 4 Homework"
author: "Key"
date: "Winter 2020"
output:
  html_document: 
    keep_md: yes
    theme: spacelab
---



## Instructions
Answer the following questions and complete the exercises in RMarkdown. Please embed all of your code and push your final work to your repository. Your final lab report should be organized, clean, and run free from errors. Remember, you must remove any `#` for included code chunks to run.  

## Load the tidyverse

```r
library(tidyverse)
```

For this assignment we are going to work with a large dataset from the [United Nations Food and Agriculture Organization](http://www.fao.org/about/en/) on world fisheries. First, load the data.  

**1. Load the data `FAO_1950to2012_111914.csv` as a new object titled `fisheries`.**

```r
fisheries <- 
  readr::read_csv(file = "data/FAO_1950to2012_111914.csv")
```

```
## Parsed with column specification:
## cols(
##   .default = col_character(),
##   `ISSCAAP group#` = col_double(),
##   `FAO major fishing area` = col_double()
## )
```

```
## See spec(...) for full column specifications.
```

**2. What are the names of the columns? Do you see any potential problems with the column names?**

```r
names(fisheries)
```

```
##  [1] "Country"                 "Common name"            
##  [3] "ISSCAAP group#"          "ISSCAAP taxonomic group"
##  [5] "ASFIS species#"          "ASFIS species name"     
##  [7] "FAO major fishing area"  "Measure"                
##  [9] "1950"                    "1951"                   
## [11] "1952"                    "1953"                   
## [13] "1954"                    "1955"                   
## [15] "1956"                    "1957"                   
## [17] "1958"                    "1959"                   
## [19] "1960"                    "1961"                   
## [21] "1962"                    "1963"                   
## [23] "1964"                    "1965"                   
## [25] "1966"                    "1967"                   
## [27] "1968"                    "1969"                   
## [29] "1970"                    "1971"                   
## [31] "1972"                    "1973"                   
## [33] "1974"                    "1975"                   
## [35] "1976"                    "1977"                   
## [37] "1978"                    "1979"                   
## [39] "1980"                    "1981"                   
## [41] "1982"                    "1983"                   
## [43] "1984"                    "1985"                   
## [45] "1986"                    "1987"                   
## [47] "1988"                    "1989"                   
## [49] "1990"                    "1991"                   
## [51] "1992"                    "1993"                   
## [53] "1994"                    "1995"                   
## [55] "1996"                    "1997"                   
## [57] "1998"                    "1999"                   
## [59] "2000"                    "2001"                   
## [61] "2002"                    "2003"                   
## [63] "2004"                    "2005"                   
## [65] "2006"                    "2007"                   
## [67] "2008"                    "2009"                   
## [69] "2010"                    "2011"                   
## [71] "2012"
```

**3. What is the structure of the data? Show the classes of each variable.**

```r
glimpse(fisheries)
```

```
## Observations: 17,692
## Variables: 71
## $ Country                   <chr> "Albania", "Albania", "Albania", "Albania",…
## $ `Common name`             <chr> "Angelsharks, sand devils nei", "Atlantic b…
## $ `ISSCAAP group#`          <dbl> 38, 36, 37, 45, 32, 37, 33, 45, 38, 57, 33,…
## $ `ISSCAAP taxonomic group` <chr> "Sharks, rays, chimaeras", "Tunas, bonitos,…
## $ `ASFIS species#`          <chr> "10903XXXXX", "1750100101", "17710001XX", "…
## $ `ASFIS species name`      <chr> "Squatinidae", "Sarda sarda", "Sphyraena sp…
## $ `FAO major fishing area`  <dbl> 37, 37, 37, 37, 37, 37, 37, 37, 37, 37, 37,…
## $ Measure                   <chr> "Quantity (tonnes)", "Quantity (tonnes)", "…
## $ `1950`                    <chr> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA,…
## $ `1951`                    <chr> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA,…
## $ `1952`                    <chr> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA,…
## $ `1953`                    <chr> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA,…
## $ `1954`                    <chr> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA,…
## $ `1955`                    <chr> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA,…
## $ `1956`                    <chr> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA,…
## $ `1957`                    <chr> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA,…
## $ `1958`                    <chr> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA,…
## $ `1959`                    <chr> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA,…
## $ `1960`                    <chr> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA,…
## $ `1961`                    <chr> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA,…
## $ `1962`                    <chr> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA,…
## $ `1963`                    <chr> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA,…
## $ `1964`                    <chr> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA,…
## $ `1965`                    <chr> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA,…
## $ `1966`                    <chr> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA,…
## $ `1967`                    <chr> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA,…
## $ `1968`                    <chr> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA,…
## $ `1969`                    <chr> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA,…
## $ `1970`                    <chr> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA,…
## $ `1971`                    <chr> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA,…
## $ `1972`                    <chr> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA,…
## $ `1973`                    <chr> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA,…
## $ `1974`                    <chr> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA,…
## $ `1975`                    <chr> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA,…
## $ `1976`                    <chr> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA,…
## $ `1977`                    <chr> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA,…
## $ `1978`                    <chr> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA,…
## $ `1979`                    <chr> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA,…
## $ `1980`                    <chr> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA,…
## $ `1981`                    <chr> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA,…
## $ `1982`                    <chr> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA,…
## $ `1983`                    <chr> NA, NA, NA, NA, NA, NA, "559", NA, NA, NA, …
## $ `1984`                    <chr> NA, NA, NA, NA, NA, NA, "392", NA, NA, NA, …
## $ `1985`                    <chr> NA, NA, NA, NA, NA, NA, "406", NA, NA, NA, …
## $ `1986`                    <chr> NA, NA, NA, NA, NA, NA, "499", NA, NA, NA, …
## $ `1987`                    <chr> NA, NA, NA, NA, NA, NA, "564", NA, NA, NA, …
## $ `1988`                    <chr> NA, NA, NA, NA, NA, NA, "724", NA, NA, NA, …
## $ `1989`                    <chr> NA, NA, NA, NA, NA, NA, "583", NA, NA, NA, …
## $ `1990`                    <chr> NA, NA, NA, NA, NA, NA, "754", NA, NA, NA, …
## $ `1991`                    <chr> NA, NA, NA, NA, NA, NA, "283", NA, NA, NA, …
## $ `1992`                    <chr> NA, NA, NA, NA, NA, NA, "196", NA, NA, NA, …
## $ `1993`                    <chr> NA, NA, NA, NA, NA, NA, "150 F", NA, NA, NA…
## $ `1994`                    <chr> NA, NA, NA, NA, NA, NA, "100 F", NA, NA, NA…
## $ `1995`                    <chr> "0 0", "1", NA, "0 0", "0 0", NA, "52", "30…
## $ `1996`                    <chr> "53", "2", NA, "3", "2", NA, "104", "8", NA…
## $ `1997`                    <chr> "20", "0 0", NA, "0 0", "0 0", NA, "65", "4…
## $ `1998`                    <chr> "31", "12", NA, NA, NA, NA, "220", "18", NA…
## $ `1999`                    <chr> "30", "30", NA, NA, NA, NA, "220", "18", NA…
## $ `2000`                    <chr> "30", "25", "2", NA, NA, NA, "220", "20", N…
## $ `2001`                    <chr> "16", "30", NA, NA, NA, NA, "120", "23", NA…
## $ `2002`                    <chr> "79", "24", NA, "34", "6", NA, "150", "84",…
## $ `2003`                    <chr> "1", "4", NA, "22", NA, NA, "84", "178", NA…
## $ `2004`                    <chr> "4", "2", "2", "15", "1", "2", "76", "285",…
## $ `2005`                    <chr> "68", "23", "4", "12", "5", "6", "68", "150…
## $ `2006`                    <chr> "55", "30", "7", "18", "8", "9", "86", "102…
## $ `2007`                    <chr> "12", "19", NA, NA, NA, NA, "132", "18", NA…
## $ `2008`                    <chr> "23", "27", NA, NA, NA, NA, "132", "23", NA…
## $ `2009`                    <chr> "14", "21", NA, NA, NA, NA, "154", "20", NA…
## $ `2010`                    <chr> "78", "23", "7", NA, NA, NA, "80", "228", N…
## $ `2011`                    <chr> "12", "12", NA, NA, NA, NA, "88", "9", NA, …
## $ `2012`                    <chr> "5", "5", NA, NA, NA, NA, "129", "290", NA,…
```

**4. Think about the classes. Will any present problems? Make any changes you think are necessary below.**

```r
fisheries$Country <- as.factor(fisheries$Country)
fisheries$`ISSCAAP group#` <- as.factor(fisheries$`ISSCAAP group#`)
fisheries$`ASFIS species#` <- as.factor(fisheries$`ASFIS species#`)
fisheries$`FAO major fishing area` <- as.factor(fisheries$`FAO major fishing area`)
```


```r
glimpse(fisheries)
```

```
## Observations: 17,692
## Variables: 71
## $ Country                   <fct> Albania, Albania, Albania, Albania, Albania…
## $ `Common name`             <chr> "Angelsharks, sand devils nei", "Atlantic b…
## $ `ISSCAAP group#`          <fct> 38, 36, 37, 45, 32, 37, 33, 45, 38, 57, 33,…
## $ `ISSCAAP taxonomic group` <chr> "Sharks, rays, chimaeras", "Tunas, bonitos,…
## $ `ASFIS species#`          <fct> 10903XXXXX, 1750100101, 17710001XX, 2280203…
## $ `ASFIS species name`      <chr> "Squatinidae", "Sarda sarda", "Sphyraena sp…
## $ `FAO major fishing area`  <fct> 37, 37, 37, 37, 37, 37, 37, 37, 37, 37, 37,…
## $ Measure                   <chr> "Quantity (tonnes)", "Quantity (tonnes)", "…
## $ `1950`                    <chr> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA,…
## $ `1951`                    <chr> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA,…
## $ `1952`                    <chr> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA,…
## $ `1953`                    <chr> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA,…
## $ `1954`                    <chr> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA,…
## $ `1955`                    <chr> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA,…
## $ `1956`                    <chr> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA,…
## $ `1957`                    <chr> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA,…
## $ `1958`                    <chr> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA,…
## $ `1959`                    <chr> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA,…
## $ `1960`                    <chr> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA,…
## $ `1961`                    <chr> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA,…
## $ `1962`                    <chr> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA,…
## $ `1963`                    <chr> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA,…
## $ `1964`                    <chr> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA,…
## $ `1965`                    <chr> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA,…
## $ `1966`                    <chr> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA,…
## $ `1967`                    <chr> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA,…
## $ `1968`                    <chr> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA,…
## $ `1969`                    <chr> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA,…
## $ `1970`                    <chr> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA,…
## $ `1971`                    <chr> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA,…
## $ `1972`                    <chr> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA,…
## $ `1973`                    <chr> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA,…
## $ `1974`                    <chr> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA,…
## $ `1975`                    <chr> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA,…
## $ `1976`                    <chr> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA,…
## $ `1977`                    <chr> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA,…
## $ `1978`                    <chr> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA,…
## $ `1979`                    <chr> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA,…
## $ `1980`                    <chr> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA,…
## $ `1981`                    <chr> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA,…
## $ `1982`                    <chr> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA,…
## $ `1983`                    <chr> NA, NA, NA, NA, NA, NA, "559", NA, NA, NA, …
## $ `1984`                    <chr> NA, NA, NA, NA, NA, NA, "392", NA, NA, NA, …
## $ `1985`                    <chr> NA, NA, NA, NA, NA, NA, "406", NA, NA, NA, …
## $ `1986`                    <chr> NA, NA, NA, NA, NA, NA, "499", NA, NA, NA, …
## $ `1987`                    <chr> NA, NA, NA, NA, NA, NA, "564", NA, NA, NA, …
## $ `1988`                    <chr> NA, NA, NA, NA, NA, NA, "724", NA, NA, NA, …
## $ `1989`                    <chr> NA, NA, NA, NA, NA, NA, "583", NA, NA, NA, …
## $ `1990`                    <chr> NA, NA, NA, NA, NA, NA, "754", NA, NA, NA, …
## $ `1991`                    <chr> NA, NA, NA, NA, NA, NA, "283", NA, NA, NA, …
## $ `1992`                    <chr> NA, NA, NA, NA, NA, NA, "196", NA, NA, NA, …
## $ `1993`                    <chr> NA, NA, NA, NA, NA, NA, "150 F", NA, NA, NA…
## $ `1994`                    <chr> NA, NA, NA, NA, NA, NA, "100 F", NA, NA, NA…
## $ `1995`                    <chr> "0 0", "1", NA, "0 0", "0 0", NA, "52", "30…
## $ `1996`                    <chr> "53", "2", NA, "3", "2", NA, "104", "8", NA…
## $ `1997`                    <chr> "20", "0 0", NA, "0 0", "0 0", NA, "65", "4…
## $ `1998`                    <chr> "31", "12", NA, NA, NA, NA, "220", "18", NA…
## $ `1999`                    <chr> "30", "30", NA, NA, NA, NA, "220", "18", NA…
## $ `2000`                    <chr> "30", "25", "2", NA, NA, NA, "220", "20", N…
## $ `2001`                    <chr> "16", "30", NA, NA, NA, NA, "120", "23", NA…
## $ `2002`                    <chr> "79", "24", NA, "34", "6", NA, "150", "84",…
## $ `2003`                    <chr> "1", "4", NA, "22", NA, NA, "84", "178", NA…
## $ `2004`                    <chr> "4", "2", "2", "15", "1", "2", "76", "285",…
## $ `2005`                    <chr> "68", "23", "4", "12", "5", "6", "68", "150…
## $ `2006`                    <chr> "55", "30", "7", "18", "8", "9", "86", "102…
## $ `2007`                    <chr> "12", "19", NA, NA, NA, NA, "132", "18", NA…
## $ `2008`                    <chr> "23", "27", NA, NA, NA, NA, "132", "23", NA…
## $ `2009`                    <chr> "14", "21", NA, NA, NA, NA, "154", "20", NA…
## $ `2010`                    <chr> "78", "23", "7", NA, NA, NA, "80", "228", N…
## $ `2011`                    <chr> "12", "12", NA, NA, NA, NA, "88", "9", NA, …
## $ `2012`                    <chr> "5", "5", NA, NA, NA, NA, "129", "290", NA,…
```

**5. How many countries are represented in the data? Provide a count.**

```r
fisheries %>% 
  summarize(ncountries = n_distinct(Country))
```

```
## # A tibble: 1 x 1
##   ncountries
##        <int>
## 1        204
```

**6. What are the names of the countries?**

```r
levels(fisheries$Country)
```

```
##   [1] "Albania"                   "Algeria"                  
##   [3] "American Samoa"            "Angola"                   
##   [5] "Anguilla"                  "Antigua and Barbuda"      
##   [7] "Argentina"                 "Aruba"                    
##   [9] "Australia"                 "Bahamas"                  
##  [11] "Bahrain"                   "Bangladesh"               
##  [13] "Barbados"                  "Belgium"                  
##  [15] "Belize"                    "Benin"                    
##  [17] "Bermuda"                   "Bonaire/S.Eustatius/Saba" 
##  [19] "Bosnia and Herzegovina"    "Brazil"                   
##  [21] "British Indian Ocean Ter"  "British Virgin Islands"   
##  [23] "Brunei Darussalam"         "Bulgaria"                 
##  [25] "Cabo Verde"                "Cambodia"                 
##  [27] "Cameroon"                  "Canada"                   
##  [29] "Cayman Islands"            "Channel Islands"          
##  [31] "Chile"                     "China"                    
##  [33] "China, Hong Kong SAR"      "China, Macao SAR"         
##  [35] "Colombia"                  "Comoros"                  
##  [37] "Congo, Dem. Rep. of the"   "Congo, Republic of"       
##  [39] "Cook Islands"              "Costa Rica"               
##  [41] "Croatia"                   "Cuba"                     
##  [43] "Cura\xe7ao"                "Cyprus"                   
##  [45] "C\xf4te d'Ivoire"          "Denmark"                  
##  [47] "Djibouti"                  "Dominica"                 
##  [49] "Dominican Republic"        "Ecuador"                  
##  [51] "Egypt"                     "El Salvador"              
##  [53] "Equatorial Guinea"         "Eritrea"                  
##  [55] "Estonia"                   "Ethiopia"                 
##  [57] "Falkland Is.(Malvinas)"    "Faroe Islands"            
##  [59] "Fiji, Republic of"         "Finland"                  
##  [61] "France"                    "French Guiana"            
##  [63] "French Polynesia"          "French Southern Terr"     
##  [65] "Gabon"                     "Gambia"                   
##  [67] "Georgia"                   "Germany"                  
##  [69] "Ghana"                     "Gibraltar"                
##  [71] "Greece"                    "Greenland"                
##  [73] "Grenada"                   "Guadeloupe"               
##  [75] "Guam"                      "Guatemala"                
##  [77] "Guinea"                    "GuineaBissau"             
##  [79] "Guyana"                    "Haiti"                    
##  [81] "Honduras"                  "Iceland"                  
##  [83] "India"                     "Indonesia"                
##  [85] "Iran (Islamic Rep. of)"    "Iraq"                     
##  [87] "Ireland"                   "Isle of Man"              
##  [89] "Israel"                    "Italy"                    
##  [91] "Jamaica"                   "Japan"                    
##  [93] "Jordan"                    "Kenya"                    
##  [95] "Kiribati"                  "Korea, Dem. People's Rep" 
##  [97] "Korea, Republic of"        "Kuwait"                   
##  [99] "Latvia"                    "Lebanon"                  
## [101] "Liberia"                   "Libya"                    
## [103] "Lithuania"                 "Madagascar"               
## [105] "Malaysia"                  "Maldives"                 
## [107] "Malta"                     "Marshall Islands"         
## [109] "Martinique"                "Mauritania"               
## [111] "Mauritius"                 "Mayotte"                  
## [113] "Mexico"                    "Micronesia, Fed.States of"
## [115] "Monaco"                    "Montenegro"               
## [117] "Montserrat"                "Morocco"                  
## [119] "Mozambique"                "Myanmar"                  
## [121] "Namibia"                   "Nauru"                    
## [123] "Netherlands"               "Netherlands Antilles"     
## [125] "New Caledonia"             "New Zealand"              
## [127] "Nicaragua"                 "Nigeria"                  
## [129] "Niue"                      "Norfolk Island"           
## [131] "Northern Mariana Is."      "Norway"                   
## [133] "Oman"                      "Other nei"                
## [135] "Pakistan"                  "Palau"                    
## [137] "Palestine, Occupied Tr."   "Panama"                   
## [139] "Papua New Guinea"          "Peru"                     
## [141] "Philippines"               "Pitcairn Islands"         
## [143] "Poland"                    "Portugal"                 
## [145] "Puerto Rico"               "Qatar"                    
## [147] "Romania"                   "Russian Federation"       
## [149] "R\xe9union"                "Saint Barth\xe9lemy"      
## [151] "Saint Helena"              "Saint Kitts and Nevis"    
## [153] "Saint Lucia"               "Saint Vincent/Grenadines" 
## [155] "SaintMartin"               "Samoa"                    
## [157] "Sao Tome and Principe"     "Saudi Arabia"             
## [159] "Senegal"                   "Serbia and Montenegro"    
## [161] "Seychelles"                "Sierra Leone"             
## [163] "Singapore"                 "Sint Maarten"             
## [165] "Slovenia"                  "Solomon Islands"          
## [167] "Somalia"                   "South Africa"             
## [169] "Spain"                     "Sri Lanka"                
## [171] "St. Pierre and Miquelon"   "Sudan"                    
## [173] "Sudan (former)"            "Suriname"                 
## [175] "Svalbard and Jan Mayen"    "Sweden"                   
## [177] "Syrian Arab Republic"      "Taiwan Province of China" 
## [179] "Tanzania, United Rep. of"  "Thailand"                 
## [181] "TimorLeste"                "Togo"                     
## [183] "Tokelau"                   "Tonga"                    
## [185] "Trinidad and Tobago"       "Tunisia"                  
## [187] "Turkey"                    "Turks and Caicos Is."     
## [189] "Tuvalu"                    "Ukraine"                  
## [191] "Un. Sov. Soc. Rep."        "United Arab Emirates"     
## [193] "United Kingdom"            "United States of America" 
## [195] "Uruguay"                   "US Virgin Islands"        
## [197] "Vanuatu"                   "Venezuela, Boliv Rep of"  
## [199] "Viet Nam"                  "Wallis and Futuna Is."    
## [201] "Western Sahara"            "Yemen"                    
## [203] "Yugoslavia SFR"            "Zanzibar"
```

**7. Use `rename()` to rename the columns and make them easier to use. The new column names should be:**  
+ country
+ commname
+ ASFIS_sciname
+ ASFIS_spcode
+ ISSCAAP_spgroup
+ ISSCAAP_spgroupname
+ FAO_area
+ unit


```r
fisheries_rename <- fisheries %>% 
  rename(country=Country,
         commname=`Common name`,
         ASFIS_sciname=`ASFIS species name`,
         ASFIS_spcode=`ASFIS species#`,
         ISSCAAP_spgroup=`ISSCAAP group#`,
         ISSCAAP_spgroupname=`ISSCAAP taxonomic group`,
         FAO_area=`FAO major fishing area`,
         unit=Measure)
names(fisheries_rename)
```

```
##  [1] "country"             "commname"            "ISSCAAP_spgroup"    
##  [4] "ISSCAAP_spgroupname" "ASFIS_spcode"        "ASFIS_sciname"      
##  [7] "FAO_area"            "unit"                "1950"               
## [10] "1951"                "1952"                "1953"               
## [13] "1954"                "1955"                "1956"               
## [16] "1957"                "1958"                "1959"               
## [19] "1960"                "1961"                "1962"               
## [22] "1963"                "1964"                "1965"               
## [25] "1966"                "1967"                "1968"               
## [28] "1969"                "1970"                "1971"               
## [31] "1972"                "1973"                "1974"               
## [34] "1975"                "1976"                "1977"               
## [37] "1978"                "1979"                "1980"               
## [40] "1981"                "1982"                "1983"               
## [43] "1984"                "1985"                "1986"               
## [46] "1987"                "1988"                "1989"               
## [49] "1990"                "1991"                "1992"               
## [52] "1993"                "1994"                "1995"               
## [55] "1996"                "1997"                "1998"               
## [58] "1999"                "2000"                "2001"               
## [61] "2002"                "2003"                "2004"               
## [64] "2005"                "2006"                "2007"               
## [67] "2008"                "2009"                "2010"               
## [70] "2011"                "2012"
```

**8. Are these data tidy? Why or why not, and, how do you know? Use the appropriate pivot function to tidy the data. Remove the NA's. Put the tidy data frame into a new object `fisheries_tidy`.**  

```r
fisheries_tidy <- fisheries_rename %>% 
  pivot_longer(-c(country,commname,ASFIS_sciname,ASFIS_spcode,ISSCAAP_spgroup,ISSCAAP_spgroupname,FAO_area,unit),
               names_to = "year",
               values_to = "catch",
               values_drop_na = TRUE)
fisheries_tidy
```

```
## # A tibble: 376,771 x 10
##    country commname ISSCAAP_spgroup ISSCAAP_spgroup… ASFIS_spcode ASFIS_sciname
##    <fct>   <chr>    <fct>           <chr>            <fct>        <chr>        
##  1 Albania Angelsh… 38              Sharks, rays, c… 10903XXXXX   Squatinidae  
##  2 Albania Angelsh… 38              Sharks, rays, c… 10903XXXXX   Squatinidae  
##  3 Albania Angelsh… 38              Sharks, rays, c… 10903XXXXX   Squatinidae  
##  4 Albania Angelsh… 38              Sharks, rays, c… 10903XXXXX   Squatinidae  
##  5 Albania Angelsh… 38              Sharks, rays, c… 10903XXXXX   Squatinidae  
##  6 Albania Angelsh… 38              Sharks, rays, c… 10903XXXXX   Squatinidae  
##  7 Albania Angelsh… 38              Sharks, rays, c… 10903XXXXX   Squatinidae  
##  8 Albania Angelsh… 38              Sharks, rays, c… 10903XXXXX   Squatinidae  
##  9 Albania Angelsh… 38              Sharks, rays, c… 10903XXXXX   Squatinidae  
## 10 Albania Angelsh… 38              Sharks, rays, c… 10903XXXXX   Squatinidae  
## # … with 376,761 more rows, and 4 more variables: FAO_area <fct>, unit <chr>,
## #   year <chr>, catch <chr>
```

**9. Refocus the data only to include country, ISSCAAP_spgroupname, ASFIS_spcode, ASFIS_sciname, year, and catch.**

```r
fisheries_tidy2 <- fisheries_tidy %>% 
  select(-c(commname, ISSCAAP_spgroup, unit, FAO_area))
fisheries_tidy2
```

```
## # A tibble: 376,771 x 6
##    country ISSCAAP_spgroupname     ASFIS_spcode ASFIS_sciname year  catch
##    <fct>   <chr>                   <fct>        <chr>         <chr> <chr>
##  1 Albania Sharks, rays, chimaeras 10903XXXXX   Squatinidae   1995  0 0  
##  2 Albania Sharks, rays, chimaeras 10903XXXXX   Squatinidae   1996  53   
##  3 Albania Sharks, rays, chimaeras 10903XXXXX   Squatinidae   1997  20   
##  4 Albania Sharks, rays, chimaeras 10903XXXXX   Squatinidae   1998  31   
##  5 Albania Sharks, rays, chimaeras 10903XXXXX   Squatinidae   1999  30   
##  6 Albania Sharks, rays, chimaeras 10903XXXXX   Squatinidae   2000  30   
##  7 Albania Sharks, rays, chimaeras 10903XXXXX   Squatinidae   2001  16   
##  8 Albania Sharks, rays, chimaeras 10903XXXXX   Squatinidae   2002  79   
##  9 Albania Sharks, rays, chimaeras 10903XXXXX   Squatinidae   2003  1    
## 10 Albania Sharks, rays, chimaeras 10903XXXXX   Squatinidae   2004  4    
## # … with 376,761 more rows
```

**10. Re-check the classes of `fisheries_tidy2`. Notice that "catch" is shown as a character! This is a problem because we will want to treat it as a numeric. How will you deal with this?**

```r
glimpse(fisheries_tidy2)
```

```
## Observations: 376,771
## Variables: 6
## $ country             <fct> Albania, Albania, Albania, Albania, Albania, Alba…
## $ ISSCAAP_spgroupname <chr> "Sharks, rays, chimaeras", "Sharks, rays, chimaer…
## $ ASFIS_spcode        <fct> 10903XXXXX, 10903XXXXX, 10903XXXXX, 10903XXXXX, 1…
## $ ASFIS_sciname       <chr> "Squatinidae", "Squatinidae", "Squatinidae", "Squ…
## $ year                <chr> "1995", "1996", "1997", "1998", "1999", "2000", "…
## $ catch               <chr> "0 0", "53", "20", "31", "30", "30", "16", "79", …
```


```r
fisheries_tidy2$catch <- as.numeric(fisheries_tidy2$catch)
```

```
## Warning: NAs introduced by coercion
```

**11. Based on the ASFIS_spcode, how many distinct taxa were caught as part of these data?**

```r
fisheries_tidy2 %>% 
  summarize(n_taxa=n_distinct(ASFIS_spcode))
```

```
## # A tibble: 1 x 1
##   n_taxa
##    <int>
## 1   1551
```

**12. Which country had the largest overall catch in the year 2000?**

```r
fisheries_tidy2 %>% 
  filter(year==2000) %>%
  group_by(country) %>% 
  summarize(catch_total=sum(catch, na.rm=T)) %>% 
  arrange(desc(catch_total))
```

```
## # A tibble: 193 x 2
##    country                  catch_total
##    <fct>                          <dbl>
##  1 Peru                        10625010
##  2 Japan                        4921013
##  3 United States of America     4692229
##  4 Chile                        4297928
##  5 Indonesia                    3761769
##  6 Russian Federation           3678828
##  7 Thailand                     2795719
##  8 India                        2760632
##  9 Norway                       2698506
## 10 Iceland                      1982369
## # … with 183 more rows
```

**13. Which country caught the most sardines (_Sardina_) between the years 1990-2000?**

```r
fisheries_tidy2$year <- as.numeric(fisheries_tidy2$year)
```


```r
fisheries_tidy2 %>% 
  filter(str_detect(ASFIS_sciname, "Sardina")) %>% 
  filter(year>=1990 & year<=2000) %>% 
  group_by(country) %>% 
  summarize(catch_total=sum(catch, na.rm=T)) %>% 
  arrange(desc(catch_total))
```

```
## # A tibble: 37 x 2
##    country            catch_total
##    <fct>                    <dbl>
##  1 Morocco                4785190
##  2 Spain                  1425317
##  3 Russian Federation     1035139
##  4 Portugal                926318
##  5 Ukraine                 784730
##  6 Italy                   377907
##  7 Algeria                 311733
##  8 Turkey                  273565
##  9 France                  263871
## 10 Denmark                 242017
## # … with 27 more rows
```

**14. Which five countries caught the most cephalopods between 2008-2012?**

```r
fisheries_tidy2 %>% 
  filter(str_detect(ISSCAAP_spgroupname, "Squids")) %>% 
  filter(year>=2008 & year<=2012) %>% 
  group_by(country) %>% 
  summarize(catch_total=sum(catch, na.rm=T)) %>% 
  arrange(desc(catch_total))
```

```
## # A tibble: 122 x 2
##    country                  catch_total
##    <fct>                          <dbl>
##  1 China                        4785139
##  2 Peru                         2274232
##  3 Korea, Republic of           1535454
##  4 Japan                        1394041
##  5 Chile                         723186
##  6 Indonesia                     684567
##  7 United States of America      613400
##  8 Thailand                      603529
##  9 Taiwan Province of China      593638
## 10 Argentina                     587238
## # … with 112 more rows
```

**15. Given the top five countries from question 14 above, which species was the highest catch total? The lowest?**

```r
fisheries_tidy2 %>% 
  filter(str_detect(ISSCAAP_spgroupname, "Squids")) %>% 
  filter(year>=2008 & year<=2012) %>% 
  group_by(ASFIS_sciname) %>% 
  summarize(catch_total=sum(catch, na.rm=T)) %>% 
  arrange((catch_total))
```

```
## # A tibble: 31 x 2
##    ASFIS_sciname           catch_total
##    <chr>                         <dbl>
##  1 Todarodes filippovae              1
##  2 Martialia hyadesi                 4
##  3 Moroteuthis ingens              194
##  4 Loligo vulgaris                 398
##  5 Eledone cirrhosa                920
##  6 Loligo duvauceli               1843
##  7 Loligo forbesi                 2567
##  8 Todarodes sagittatus           5073
##  9 Illex coindetii               20209
## 10 Sepioteuthis lessoniana       28547
## # … with 21 more rows
```

**16. In some cases, the taxonomy of the fish being caught is unclear. Make a new data frame called `coastal_fish` that shows the taxonomic composition of "Miscellaneous coastal fishes" within the ISSCAAP_spgroupname column.**

```r
coastal_fish <- fisheries_tidy2 %>% 
  filter(ISSCAAP_spgroupname=="Miscellaneous coastal fishes") %>%
  group_by(ASFIS_sciname) %>% 
  summarise(total_catch=sum(catch, na.rm=T)) %>% 
  arrange(desc(total_catch))
coastal_fish
```

```
## # A tibble: 412 x 2
##    ASFIS_sciname        total_catch
##    <chr>                      <dbl>
##  1 Ammodytes spp           30431666
##  2 Sciaenidae              20725344
##  3 Ariidae                 11412132
##  4 Pleurogrammus azonus     9988904
##  5 Nemipterus spp           9535807
##  6 Mugilidae                8593998
##  7 Leiognathidae            8463735
##  8 Harpadon nehereus        8307468
##  9 Ammodytes personatus     7654776
## 10 Sparidae                 7073772
## # … with 402 more rows
```

**17. Use the data to do at least one exploratory analysis of your choice. What can you learn?**

## Push your final code to GitHub!
Please be sure that you check the `keep md` file in the knit preferences.   
