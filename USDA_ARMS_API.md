# USDA_ARMS API Documentation

**Base URL:** `https://api.ers.usda.gov/data/arms`

**Description:** The USDA Agricultural Resource Management Survey (ARMS) API provides detailed agricultural data, which is crucial for understanding the usage and demand of fertilizers across different states and time periods.

## Endpoints and Usage

### /arms/state
- **Description:** Gets all States and the metadata and variables available for each of the States.
- **Method:** GET
- **URL Example:**
  ```sh
  GET https://api.ers.usda.gov/data/arms/state?api_key=YOUR_API_KEY
  ```

### /arms/year
- **Description:** Gets all available years for which data are available.
- **Method:** GET
- **URL Example:**
  ```sh
  GET https://api.ers.usda.gov/data/arms/year?api_key=YOUR_API_KEY
  ```

### /arms/surveydata
- **Description:** Retrieves survey data based on specified criteria. Year is a required field; at least one of the two input fields (report or variable) is also required.
- **Method:** GET and POST
- **URL Example (GET):**
  ```sh
  GET https://api.ers.usda.gov/data/arms/surveydata?api_key=YOUR_API_KEY&year=2015,2016&state=all&report=income+statement&farmtype=operator+households&category=collapsed+farm+typology&category_value=commercial
  ```
- **URL Example (POST):**
  ```sh
  POST https://api.ers.usda.gov/data/arms/surveydata?api_key=YOUR_API_KEY
  {
    "year": [2011, 2012, 2013, 2014, 2015, 2016],
    "state": "all",
    "variable": "igcfi",
    "category": "NASS Regions",
    "category2": "Collapsed Farm Typology"
  }
  ```

### /arms/category
- **Description:** Lists categories and subcategories within each category, providing relevant metadata and variables available for each of the categories and subcategories.
- **Method:** GET and POST
- **URL Example (GET):**
  ```sh
  GET https://api.ers.usda.gov/data/arms/category?api_key=YOUR_API_KEY
  ```
- **URL Example (POST):**
  ```sh
  POST https://api.ers.usda.gov/data/arms/category?api_key=YOUR_API_KEY
  {
    "name": "Collapsed Farm Typology"
  }
  ```

### /arms/report
- **Description:** Gets available reports with relevant metadata and variables available for each report.
- **Method:** GET and POST
- **URL Example (GET):**
  ```sh
  GET https://api.ers.usda.gov/data/arms/report?api_key=YOUR_API_KEY
  ```
- **URL Example (POST):**
  ```sh
  POST https://api.ers.usda.gov/data/arms/report?api_key=YOUR_API_KEY
  {
    "name": "balance sheet"
  }
  ```

### /arms/variable
- **Description:** Gets variables with relevant information and metadata for each variable used in ARMS.
- **Method:** GET and POST
- **URL Example (GET):**
  ```sh
  GET https://api.ers.usda.gov/data/arms/variable?api_key=YOUR_API_KEY
  ```
- **URL Example (POST):**
  ```sh
  POST https://api.ers.usda.gov/data/arms/variable?api_key=YOUR_API_KEY
  {
    "report": "Business Balance Sheet",
    "name": "Liabilities current debt"
  }
  ```

### /arms/farmtype
- **Description:** Retrieves all Farm Types or searches by keyword, name, or ID.
- **Method:** GET and POST
- **URL Example (GET):**
  ```sh
  GET https://api.ers.usda.gov/data/arms/farmtype?api_key=YOUR_API_KEY
  ```
- **URL Example (POST):**
  ```sh
  POST https://api.ers.usda.gov/data/arms/farmtype?api_key=YOUR_API_KEY
  {
    "name": "operator households"
  }
  ```

### GraphQL API
- **Endpoint:** `https://api.ers.usda.gov/data/arms/graphql`
- **Description:** GraphQL is a modern method to easily interact with the API. A GraphQL client, such as ChromeiQL, is needed to interact with the ARMS API.

## Example Usage
```yaml
data_sources:
  USDA_ARMS:
    base_url: https://api.ers.usda.gov/data/arms
    description: >
      The USDA Agricultural Resource Management Survey (ARMS) API provides detailed agricultural data, which is crucial for understanding the usage and demand of fertilizers across different states and time periods.
    endpoints:
      - name: State Data
        path: /arms/state
        params:
          api_key: YOUR_API_KEY
        description: >
          Retrieves all States and the metadata and variables available for each of the States.
      - name: Yearly Data
        path: /arms/year
        params:
          api_key: YOUR_API_KEY
        description: >
          Retrieves all available years for which data are available.
      - name: Survey Data
        path: /arms/surveydata
        params:
          api_key: YOUR_API_KEY
          year: 2020
          state: all
          variable: igcfi
          category: NASS Regions
        description: >
          Retrieves "Gross Farm Income" for the year 2020 for "All States" and broken by Category = NASS regions.
```

## Reports and Variables

ARMS reports are a collection of financial data points about U.S.-based farms that can be sorted and viewed in various ways, including at the national level or state level, and by farmer type or farmer age.

### Available Reports
- Farm Business Balance Sheet
- Farm Business Income Statement
- Farm Business Financial Ratios
- Structural Characteristics
- Farm Business Debt Repayment Capacity
- Government Payments
- Operator Household Income
- Operator Household Balance Sheet

### Available Categories
Categories are meta tags that provide context for the data. The available categories include:
- Residence farms
- Intermediate farms
- Commercial farms
- Economic Class (sal)
- Farm Typology (ftyppl)
- Operator age (age)
- Farm Resource Region (reg)
- NASS region (n5reg)
- Production Specialty (spec)
