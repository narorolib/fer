# Fer

[Fer](https://fer.ee) is a free API service that tracks current and historical foreign exchange rates [published by the European Central Bank](https://www.ecb.europa.eu/stats/policy_and_exchange_rates/euro_reference_exchange_rates/html/index.en.html).

A public instance of the API lives at `api.fer.ee`.

Rates are updated every working day.

## Getting Started

Get the latest foreign exchange rates.

```http
GET https://api.fer.ee/latest
```


Rates are quoted against the Euro by default. You can quote against a different currency by setting the `from` *or* `base` parameter.

```http
GET https://api.fer.ee/latest?from=USD
```

```http
GET https://api.fer.ee/latest?base=USD
```


Request specific exchange rates by setting the `to` *or* `symbols`  parameter in your request to limits returned rates to specified values.

```http
GET https://api.fer.ee/latest?to=USD,JPY
```

```http
GET https://api.fer.ee/latest?symbols=USD,JPY
```


Get historical rates for any day since 1999.

```http
GET https://api.fer.ee/2000-01-01
```


Get rates for a period.

```http
GET https://api.fer.ee/2010-01-01..2010-01-31
```


Limit results to specific foreign exchange rates with the `to` *or* `symbols` parameter.
```http
GET https://api.fer.ee/2000-01-01?to=USD,JPY
```
```http
GET https://api.fer.ee/2000-01-01?symbols=USD,JPY
```


Quote the historical rates against a different currency with the `from` *or* `base` parameter.
```http
GET https://api.fer.ee/2000-01-01..2010-01-01?from=USD
```
```http
GET https://api.fer.ee/2000-01-01..2010-01-01?base=USD
```
Fer returns all data points for up to 90 days. Beyond this period, it starts sampling by week or month based on the breadth of the date range.



You can convert any value between currencies using the above endpoints in combination with the `amount` parameter.
```http
GET https://api.fer.ee/latest?amount=100&from=USD&to=CNY
```



Get a list of available currency symbols and their full names.
```http
GET https://api.fer.ee/currencies
```


###### The Fer API is ~~almost~~ entirely borrowed from [Frankfurter](https://www.frankfurter.app/)'s simple and straightforward API design. If you prefer to self-host, you should go to [Frankfurter's documentation](https://www.frankfurter.app/docs/) for details.
