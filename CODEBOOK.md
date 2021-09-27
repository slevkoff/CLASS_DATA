#CODEBOOK for NOXSO2 Coal-Fired Electric Power Plant RAW Data Set (Panel_8595.txt)

We have measurements on 92 decision making units (DMUs) across 11 years from 1985-1995.  
Each DMU observation is a coal-fired electric plant that generates multiple outputs using multiple inputs.

##The three outputs are:
* `(Y) Energy`, electrical generation measured in kWh
* `(Z1) SO2`, sulphur dioxide emissions measured in short tons
* `(Z2) NOX`, mono-nitrogen oxide (nitric oxide, NO, and nitrogen dioxide, NO2) emissions measured in short tons

The first output, Energy, is an intended output.  The SO2 and NOX are unintended by-products of the production process.

##The five inputs are:
* `(X1) Capital Stock`, measured as change in investment / replacing P&E deflating expenditures to 1973 base year USD using the HWI
* `(X2) Labor`, employees per plant as an annualized average
* `(X3) Heat content of coal`, measured in Btus
* `(X4) Heat content of oil`, measured in Btus
* `(X5) Heat content of natural gas`, measured in Btus

The first two inputs are non-fuel inputs.  The last three inputs are fuel inputs.

There are also two more data columns (F1) and (F2) which represent some type of fuel input, not to be used in the analysis.

There is also a column labeled `PhaseI` in the tidy data in/after version `cleaned102615.2.txt` which identifies whether or not a plant was required to comply
with Phase I SO2 reductions which became binding in 1995 (but were announced in 1990).

#CODEBOOK for NOXSO2 Coal-Fired Electric Power Plant TIDY Data (cleaned103115.txt)

This is a tidy version of the RAW data set above.  A few variables have been added, some removed, and others re-scaled by unit conversions.

We have measurements on 92 decision making units (DMUs), over 11 years from 1985-1995.  An important regulatory policy was annouced at the end of 1990.
The policy, Title IV of the 1990 CAA, mandated Phase I reductions by some plants effective in 1995.
Each DMU observation is a coal-fired electric plant that generates multiple outputs using multiple inputs.

##Observations by:
* `Year`
* `PlantID`
* `PlantName`

##The three outputs are:
* `(Y) Energy`, electrical generation measured in GWh scaled as daily average
* `(Z1) SO2`, sulphur dioxide emissions measured in short tons scaled as daily average
* `(Z2) NOX`, mono-nitrogen oxide (nitric oxide, NO, and nitrogen dioxide, NO2) emissions measured in short tons scaled as daily average

The first output, Energy, is an intended output.  The SO2 and NOX are unintended by-products of the production process.

##The five inputs are:
* `(X1) Capital`, stock measured as aggregated changes in annual net investment on P&E expenditures converted to 1973 base year USD using the HWI
* `(X2) Labor`, employees per plant as an annualized average
* `(X3) CoalHeat`, measured in Gwh scaled as daily average
* `(X4) OilHeat`, measured in Gwh scaled as daily average
* `(X5) GasHeat`, measured in Gwh scaled as daily average

The first two inputs are non-fuel inputs.  The last three inputs are fuel inputs.

##Added Features
* `Phase I`, dummy feature identifying whether or not plant was required to comply with Phase I SO2 reductions via Title IV of 1990 CAA (coded 1 for regulated)
* `PolYr`, dummy feature identifying whether the CAA Phase I policy was announced already (coded 1 for post 1990)
* `GrossCons`, gross consumption of heat energy summed over coal, oil, and natural gas sources measured in Mwh (thousands) scaled as daily average
* `NetCons`, net consumption of heat energy summed over coal, oil, and natural gas sources minus energy generated measured in Mwh (thousands) scaled as daily average