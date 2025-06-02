# Queries

Here are queries from https://api.simplywall.st/docs/#introduction-item-0
These will be used to access the data on the simply wall str website

Use this token:
sws:YzVlNGI5M2YtY2JhMi00MzhhLThjMGQtYWRjZThmYTAxN2QxOjI1ZjY0MDNmM2I2NDJlNTA=

**Simply Wall St’s API is designed to provide an aggregated view of a company’s fundamentals rather than raw, granular balance sheet numbers (like total assets, liabilities, and equity).**
These aggregated and processed fundamental data is used to produce their visual(the snowflake) it is also only in 

## Get UUID of a company:

curl --location 'https://api.simplywall.st/graphql' \
--header 'Authorization: Bearer <pro-api-token>' \
--header 'Content-Type: application/json' \
--data '{"query":"query searchCompanies($query: String!) {searchCompanies(query: $query) {id,name,exchangeSymbol,tickerSymbol}}","variables":{"query":"tesla"}}'

## Get basic company information using UUID (company id):

curl --location 'https://api.simplywall.st/graphql' \
--header 'Authorization: Bearer <pro-api-token>' \
--header 'Content-Type: application/json' \
--data '{"query":"query Query($id: ID!) {company (id: $id) {id,name,tickerSymbol}}","variables":{"id":"65dce5ea-70d6-417f-9cac-1eaa92fb7f1c"}}'

## List exchanges supported:

curl --location 'https://api.simplywall.st/graphql' \
--header 'Authorization: Bearer <pro-api-token>' \
--header 'Content-Type: application/json' \
--data '{"query":"query {exchanges {symbol}}","variables":{}}'

## Get company info through ticker

curl --location 'https://api.simplywall.st/graphql' \
--header 'Authorization: Bearer <pro-api-token>' \
--header 'Content-Type: application/json' \
--data '{"query":"query companyByExchangeAndTickerSymbol($exchange: String!,$symbol:String!) {\n  companyByExchangeAndTickerSymbol(exchange: $exchange,tickerSymbol:$symbol) {id,name,exchangeSymbol,tickerSymbol}\n}\n","variables":{"exchange":"NasdaqGS","symbol":"TSLA"}}'

## Breakdown of a sample JSON returned by the company query:
### id:
A unique identifier for the company within Simply Wall St’s system. It stays constant even if the company changes ticker symbols.

### exchangeSymbol:
The short abbreviation for the exchange where the company is listed (e.g., "NasdaqGS" for the Nasdaq Global Select Market).

### tickerSymbol:
The unique stock symbol used for trading the company’s shares (e.g., "AAPL" for Apple Inc.).

### name:
The full name of the company.

### marketCapUSD:
The total market capitalization of the company expressed in U.S. dollars. This represents the company’s total value as determined by the stock market.

### primaryIndustry, secondaryIndustry, tertiaryIndustry:
These fields indicate the industries the company is categorized under, arranged in levels of relevance or specificity. For instance, the primary industry might be “Technology”, while the secondary could be “Consumer Electronics.”

### market:
A nested object representing details about the market in which the company operates. This can include market name, country (often in ISO code format), and other market-specific information.

### closingPrices:
A collection (often a JSON object) of the company’s historical closing stock prices. This data can be used to analyze trends over time.

### statements: (Belangrik)
An array of evaluated opinions or analysis results about the company. This may include risk assessments, rewards, and other qualitative or quantitative evaluations.

### listings:
An array that may contain additional listings of the company if it’s traded on multiple exchanges or in multiple forms. Each element is typically a mini company object with similar details.

### owners:
An array containing information about the company’s major shareholders or owners. This may include their names, the percentage of shares they hold, and other relevant ownership details.

### insiderTransactions:
An array of transactions made by insiders (such as executives or board members) that give insight into how those with intimate knowledge of the company are trading its shares.

### members:
An array listing key members of the company’s management or board of directors. This might include names, titles, and sometimes compensation or tenure data.

### active:
A Boolean flag indicating whether the company’s listing is currently active on the exchange.

### classificationStatus:
A status label (e.g., "ACTIVE") that indicates the current state or classification of the company’s listing according to Simply Wall St’s internal criteria.