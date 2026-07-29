# Gambling-related Healthcare Visits in Brazil

**Project 3 for the Lede Program in Data Journalism at Columbia University**

🔗 **Live project: *https://alexameirelles.github.io/gambling-br/*

A data-driven story exploring outpatient visits related to gambling and betting disorders in Brazil between **2015 and 2025**, using data from Brazil's public healthcare system (SUS).

---

## Overview

This project investigates healthcare visits related to gambling and betting disorders recorded by Brazil's public healthcare system (SUS) between 2015 and 2025.

The analysis combines outpatient visits from the **Outpatient Information System (SIA)** and hospitalizations from the **Hospital Information System (SIH)** to examine how demand for gambling-related healthcare has evolved over time and where these visits are concentrated across the country.

The story uses a scrollytelling format that guides readers from a national overview to increasingly detailed geographic views, moving from:

- Brazil
- Rondônia
- São Paulo state
- São Paulo city districts

The project focuses on combining geographic datasets with **Mapbox GL JS** and **D3.js**, including animated transitions between map scales.

---

## Data

### Healthcare data

The analysis uses records from:

- **SIA (Outpatient Information System)**
- **SIH (Hospital Information System)**
- **CNES (National Registry of Health Facilities)**

Both datasets were accessed through **Base dos Dados** using SQL queries executed in Python.

The study focuses on records associated with the following ICD-10 codes:

- **F63.0** — Pathological gambling
- **Z72.6** — Gambling and betting behavior

### Geographic data

Additional datasets include:

- IBGE state boundaries
- IBGE municipality boundaries
- IBGE São Paulo district boundaries

The geographic datasets were originally distributed as Shapefiles and converted to GeoJSON using **Mapshaper** before being incorporated into the interactive maps.

---

## Methodology

### 1. Data collection

Healthcare records were queried directly from Base dos Dados using SQL within Python notebooks.

Separate queries were developed for:

- Outpatient visits (SIA) + Health facilities information (CNES)
- Hospitalizations (SIH)

### Defining the study period

The project was initially designed to analyze healthcare records between **2020 and 2025**, focusing on the years during which online betting became widespread in Brazil.

After retrieving the first results, however, I decided to expand the analysis to **2015–2025**. Restricting the study to the pandemic and post-pandemic years could have introduced bias, since COVID-19 substantially affected healthcare utilization throughout the country, particularly between 2020 and 2022.

The longer time series provides important historical context, showing that gambling-related healthcare visits were already relatively uncommon before the pandemic and then increased sharply in the following years. While the data alone do not establish a causal relationship, this acceleration coincided with the rapid expansion of online betting platforms in Brazil, making the broader historical perspective more informative.

---

### 2. Geographic processing

Healthcare facilities were geocoded using their ZIP codes (CEP).

- Address information was retrieved through **ViaCEP**.
- Geographic coordinates were obtained using **OpenStreetMap Nominatim**.

Healthcare facilities located within São Paulo city were spatially joined with official district boundaries using **GeoPandas**, allowing outpatient visits to be aggregated by district.

My initial hypothesis was that gambling-related healthcare visits might be more concentrated in lower-income neighborhoods. The district-level analysis revealed a different pattern: most outpatient visits were concentrated in **Jardim Paulista** because they were associated with a single healthcare facility — the **Hospital das Clínicas of the University of São Paulo Faculty of Medicine**.

According to the facility's official records, its Institute of Psychiatry operates a specialized outpatient program for people with gambling addiction, largely explaining the geographic concentration observed in the data.

---

### 3. Data analysis

The analysis was conducted in Python using **pandas**.

The work focused primarily on:

- temporal trends
- geographic distribution
- outpatient visits versus hospitalizations
- municipality-level aggregation
- district-level aggregation

Intermediate datasets were exported as CSV files for use in the interactive visualizations.

---

### 4. Visualization

The final story combines several custom visualizations built with **D3.js** and **Mapbox GL JS**, including:

- animated line chart
- waffle chart
- scrollytelling maps
- choropleth maps at multiple geographic levels
- animated transitions between maps

---

## Main findings

- Gambling-related outpatient visits increased dramatically between 2015 and 2025.
- Hospitalizations remained substantially less frequent than outpatient visits throughout the period.
- São Paulo accounted for the largest share of outpatient visits nationwide.
- Rondônia recorded the second-highest number of outpatient visits despite being one of Brazil's least populous states.
- Within São Paulo state, healthcare visits were highly concentrated in the capital.
- Nearly three-quarters of São Paulo's outpatient visits occurred in the Jardim Paulista district, primarily at the Hospital das Clínicas of the University of São Paulo Faculty of Medicine.

---

## Skills and learning

This project allowed me to deepen my experience working with healthcare microdata, geospatial analysis, and interactive cartography.

Throughout the project, I learned how to:

- query large healthcare datasets using SQL and Base dos Dados
- build multi-step scrollytelling experiences with Mapbox GL JS
- coordinate D3.js and Mapbox visualizations
- geocode healthcare facilities using ViaCEP and Nominatim
- perform spatial joins with GeoPandas
- convert Shapefiles to GeoJSON using Mapshaper
- design choropleth maps at multiple geographic scales
- improve map styling, transitions, and storytelling through JavaScript

The official documentation for Mapbox GL JS, GeoPandas, D3.js, pandas, and Base dos Dados served as my primary references throughout development.

AI-assisted explanations also played an important role, particularly while building the interactive maps, debugging JavaScript, and learning unfamiliar geospatial concepts.

---

## Future improvements

Given more time, I would like to:

- incorporate interviews with psychiatrists, addiction specialists, and patients
- expand the analysis using additional mental health datasets
- investigate regional differences in access to specialized treatment
- improve the mobile experience
- further enhance accessibility for screen readers and keyboard navigation
- update the project as new healthcare records become available

---

## Tools

- Python
- SQL
- Google BigQuery
- Base dos Dados
- pandas
- Geopy
- GeoPandas
- Mapbox GL JS
- D3.js
- Mapshaper
- HTML
- CSS
- JavaScript

---

## Sources

- Base dos Dados
- Brazilian Ministry of Health (SIA and SIH)
- IBGE (state, municipality, and district boundaries)
- ViaCEP
- OpenStreetMap Nominatim