# Interactive Dashboard for Argentina Treaty Data Analysis

## Project Overview: ##

This project is designed to provide an interactive, web-based dashboard for exploring and analyzing Argentina's treaty data (spanning from 1810 to 2023). Built using `Python`, `Dash`, and `Plotly`, the application offers a rich set of visualizations and interactive filtering options, enabling users to gain insights into treaty trends over time, regional distributions, and other key aspects of the data. The code is organized into the following main sections:

## 1. DATA LOADING AND PREPROCESSING ##

**Purpose:**

To load the raw data from a CSV file, clean it, and create additional columns that facilitate further analysis.

**Key Activities:**
- ***Data Import:*** Reads the dataset containing treaty information, which includes columns like `Sign_year`, `Counterpart_ENG`, `Region_ENG`, and `Tags`.
- ***Cleaning:*** Removes duplicate records and filters out rows missing essential information (e.g., missing `Counterpart_ENG`).
- ***Column Standardization:*** Strips extra whitespace from column names to ensure consistency.
- ***Feature Engineering:***
    - Creates a new `Year` column derived from the provided `Sign_year` for uniformity.
    - Computes a `Decade` column by grouping each year into its respective decade (e.g., 1995 becomes 1990).
## 2. REGION SETUP ##
**Purpose:**

To standardize and enhance regional information from the dataset so that visualizations and filters can work with consistent region names.

**Key Activities:**
- ***Data Extraction:*** Uses the `Region_ENG` column from the dataset to extract regional information.
- ***Data Cleaning:*** Strips extra spaces from the region names.
- ***Mapping:*** Optionally applies a dictionary-based mapping to standardize region names (for example, mapping "USA" to "North America").
This ensures that all treaties are correctly categorized by region, which is crucial for regional analysis and filtering.
## 3. AGGREGATIONS AND BASE VISUALIZATIONS ##
**Purpose:**

To generate key aggregated metrics from the dataset and create base visualizations that provide an initial understanding of treaty trends.

**Key Activities:**
- ***Aggregations:***
    - Computes the number of treaties signed per year.
    - Calculates the number of treaties per decade.
    - Identifies the top 20 counterparts (countries) by treaty count.
- ***Visualizations:***
    - Bar Charts: Display the top counterparts and treaty counts by decade.
    - Line Charts: Illustrate the trend of treaty signings over the years.
- ***Styling:***
    - All visualizations are styled using an Argentine color theme (featuring sky blue and dark blue tones along with a white background) to create a visually cohesive experience.
## 4. DASH APP SETUP AND LAYOUT ##

**Purpose:**

To set up the interactive web dashboard layout using Dash, integrating filters, multiple tabs, and the previously created visualizations.

**Key Activities:**
- ***User Interface Layout:***
    - Implements a year range slider for filtering data by signing year.
    - Provides dropdown menus for selecting one or more counterparts and regions.
    - Organizes the interface into several tabs that display different aspects of the analysis:
        - Table: Shows the filtered raw data.
        - Visualizations: Displays the basic charts (line and bar charts) reflecting overall trends.
        - Decade Analysis: Focuses on aggregated data by decade.
        - Regional Analysis: Presents regional trends using area and bar charts.
        - Deep Analytics: Offers additional advanced visualizations like treemaps and heatmaps.
        - Tags Analysis: Analyzes the Tags column to visualize the frequency of various tags.
- ***Color Theme Integration:***
    - Uses a helper function to apply the Argentine color theme across all visual components, ensuring a consistent visual style.
## 5. CALLBACK TO UPDATE TABS BASED ON FILTERS ##

**Purpose:**

To implement interactivity in the dashboard by dynamically updating the visualizations and data displays based on user input.

**Key Activities:**
- ***Dynamic Updates:***
    - A central callback function listens for changes in the filters (year range, counterparts, and regions) and updates the content displayed in the various tabs accordingly.
- ***Interdependent Dropdowns:***
    - A specialized callback is implemented to update the options in the "Counterpart(s)" dropdown based on the selected regions. This ensures that when a region is chosen, only the counterparts (countries) within that region are available for selection.
- ***Visualization Updates:***
    - Depending on the active tab, the callback recalculates aggregations and refreshes the corresponding visualizations (charts and tables) with the filtered data.
