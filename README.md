# Crime_in_Urban_Context: Analyzing Area-Level Characteristics and NYC Crime
CUSP-GX 7033: Machine Learning for Cities Final Project

This project examines the relationships between area-level characteristics (subway transit, built environment, and socioeconomic factors) and different types of crime patterns in New York City, comparing area-standardized and population-standardized approaches.

## Research Background

Crime in urban areas is not randomly distributed, with patterns influenced by various area-level characteristics. This research draws on three criminological theoretical frameworks:

- **Routine Activity Theory**: Explains crime as the convergence of motivated offenders, suitable targets, and absent guardians
- **Crime Opportunity Theory**: Analyzes how environmental features structure criminal opportunities
- **Social Disorganization Theory**: Examines how socioeconomic conditions influence crime rates

## Research Question

Primary question: **Which factors - Subway Transit, Built Environment, and Socioeconomic - are most strongly associated with crime rates at census tract level in NYC?**

### Specific Objectives
1. **Identify key drivers:** Compare how subway transit, built environmental, and socioeconomic variables relate to each crime type.
2. **Build interpretable models:** Use Random Forests for nonlinear effects and Gaussian Processes for spatial dependence, combining the strengths of both.
3. **Predict area-level crime risk:** Model total, property, and violent crime separately to expose different mechanisms.

## Data & Methods

### Data Sources
- Crime data (2022-2024): Total, property, and violent crime at census tract level
- MTA subway data: Station locations, ridership, entrances
- POI and Street data: Locations of commercial, cultural, educational, residential, and other facilities, and NYC street information
- Socioeconomic data: Population, age, income, and other indicators at census tract level
- Spatial boundary data: Census tract vector boundaries

### Standardization Methods Comparison

This research innovatively compares two different crime rate standardization methods and their impact on analytical results:

1. **Area Standardization (Crime Density)**
   - Measure: Crime incidents per square kilometer
   - Implicit assumption: Crime is spatially homogeneous
   - Perspective: Reflects crime concentration in specific geographic areas, answering "Where do most crime incidents occur?"
   - Application: Police resource allocation, hotspot patrol areas

2. **Population Standardization (Crime Rate)**
   - Measure: Crime incidents per population
   - Implicit assumption: Crime is related to population size
   - Perspective: Reflects actual crime risk faced by residents, answering "Where are people more likely to experience crime?"
   - Application: Intervention measures, risk assessment, resident safety perception

### Modeling Approaches
- **Random Forest Models**: Capturing non-linear relationships and variable importance
- **Gaussian Process Models**: Capturing spatial correlations and providing uncertainty estimates
- **Spatial Autocorrelation Analysis**: Measuring spatial clustering of crime (Moran's I)

## Key Findings

### Crime Type Differences (Area normalized)

1. **Property Crime**:
   - Primarily influenced by transit accessibility (ridership, subway coverage) and commercial environment
   - Highly consistent with Routine Activity Theory and Crime Opportunity Theory
   - Shows moderate spatial autocorrelation in area-standardized analysis (Moran's I ≈ 0.39)

2. **Violent Crime**:
   - Primarily influenced by socioeconomic characteristics (income level, youth population percentage) and residential environment
   - Highly consistent with Social Disorganization Theory
   - Shows strong spatial autocorrelation in area-standardized analysis (Moran's I = 0.65)

### Standardization Method Comparison

1. **Model Performance Differences**:
   - Random Forest performs better on population-standardized data (R² increased by ~0.2)
   - Gaussian Process models perform more consistently on area-standardized data
   - Spatial autocorrelation almost disappears after population standardization (Moran's I close to 0)

2. **Predictor Importance Changes**:
   - Area standardization: Neighboring crime density, average ridership, subway coverage rank highly
   - Population standardization: Population density becomes the dominant factor (R² > 0.7)
   - Transit features significantly decrease in importance after population standardization

3. **Theoretical Interpretation Shift**:
   - Area-standardized results support environmental and opportunity theories
   - Population-standardized results emphasize social disorganization theory

## Policy Implications

### Differentiated Prevention Strategies
- **Property Crime Prevention**: Enhance monitoring and patrol in high subway coverage and high ridership areas
- **Violent Crime Prevention**: Implement community intervention programs in socioeconomically vulnerable areas

### Integrated Recommendations
- Combine both standardization perspectives for comprehensive planning
- Apply environmental design and place management for property crime
- Implement social interventions and support for violent crime

## Project File Structure

- `Crime_Density(Area_normalized)/`: Files related to area-standardized analysis
- `Crime_Rate(Population_normalized)/`: Files related to population-standardized analysis
- `README.md`: Project overview and documentation

## References

- Cohen, L. E., & Felson, M. (1979). Social change and crime rate trends: A routine activity approach. American Sociological Review, 44(4), 588–608. 
https://doi.org/10.2307/2094589

- Clarke, R. V. (1995). Situational crime prevention. In M. Tonry & D. P. Farrington (Eds.), Building a safer society: Strategic approaches to crime prevention (pp. 91–150). University of Chicago Press.
Felson, M. (1987). Routine activities and crime prevention in the developing metropolis. Criminology, 25(4), 911–932.
https://doi.org/10.1111/j.1745-9125.1987.tb00825.x

- Hakyemez, T. C., & Badur, B. (2021). Crime Risk Stations: Examining Spatiotemporal Influence of Urban Features through Distance-Aware Risk Signal Functions. ISPRS International Journal of Geo-Information, 10(7), 472. 
https://doi.org/10.3390/ijgi10070472

- Kim, J., & Hipp, J. R. (2022). Subway station and neighborhood crime: An egohood analysis using subway ridership and crime data in New York City. SafetyLit. https://www.safetylit.org/citations/index.php?citationIds%5B%5D=citjournalarticle_768216_37&fuseaction=citations.viewdetailsSafetyLit

- Newton, A. D., Partridge, H., & Gill, A. (2014). Above and below: Measuring crime risk in and around underground mass transit systems. Crime Science, 3(1), 1–14.
https://doi.org/10.1186/2193-7680-3-1

- Smith, M. J., & Clarke, R. V. (2000). Crime and public transport. Crime and Justice, 27, 169–233. https://doi.org/10.1086/652200

- Shaw, C. R., & McKay, H. D. (1942). Juvenile delinquency and urban areas. University of Chicago Press.

- Sampson, R. J., & Groves, W. B. (1989). Community structure and crime: Testing social-disorganization theory. American Journal of Sociology, 94(4), 774–802.  
https://doi.org/10.1086/229068

- Vital City. (2023). Just the facts on New York City subway crime. Vital City. https://www.vitalcitynyc.org/articles/just-the-facts-on-new-york-city-subway-crime
