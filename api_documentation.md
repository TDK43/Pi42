# Change Log – Pi42 API Reference Documentation

# Change Log

- 21-4-2025
- 23-1-2025
- 19-12-2024
- 25-10-2024
- 17-09-2024
- 17-07-2024
- 9-07-2024
- 19-06-2024
- 06-06-2024
- 28-05-2024
- 20-05-2024
- 10-05-2024

# Introduction

# API Rate Limits

# Orders

# Public Endpoints

- Ticker Update (24Hr)
- Aggregate Trade Update
- Depth Update
- Get Klines
- Exchange

# Web Sockets

# Error Codes

# Change Log

# 21-4-2025

- New Endpoint: Edit an existing open order (PATCH /v1/order/edit-order)

# 23-1-2025

- New fields: leverage and lockedMargin in /v1/order/open-orders api response.
- leverage in /v1/order/place-order api response.

# 19-12-2024

- New FAWSS_UDS to emit user specific events:

https://lightningnodes.github.io/slate/?python#change-log
---
# Change Log – Pi42 API Reference Documentation

FAWSS_UDS Link: https://fawss-uds.pi42.com/auth-stream

FAWSS will only send market data events.

# 25-10-2024

1. New Endpoints to get wallet balance:
- Get futures wallet details (GET /v1/wallet/futures-wallet/details)
- Get funding wallet details (GET /v1/wallet/funding-wallet/details)
2. New Endpoints for close all positions and open orders:
- Cancel all the orders (DELETE /v1/order/cancel-all-orders)
- Close all the positions (DELETE /v1/positions/close-all-positions)
3. New update preference endpoint:
- To Update leverage and margin-mode (POST /v1/exchange/update/preference)

# 17-09-2024

1. Additional authentication method with private web socket using listen key.
2. New Endpoints for listen key
- Create new listen key for web-socket connection (POST /v1/retail/listen-key)
- Update expiry time for listen key (PUT /v1/retail/listen-key)
- Delete listen key (DELETE /v1/retail/listen-key)
3. Endpoints for CRUD Operations on api-key which are typically done through UI
- Create a new api-key (POST /v1/retail/create-api-key)
- Get all api-keys for user (GET /v1/retail/all-api-keys)
- Delete api-key for user (DELETE /v1/retail/delete-api-key)
- Update api-key trading permissions (POST /v1/retail/update-api-key-permissions)
- Whitelist IPs for api-key (POST /v1/retail/add-allowed-ips)
- Remove whitelisted IPs for api-key (POST /v1/retail/remove-allowed-ips)

# 17-07-2024

1. Added Enum Value GST_ON_FUNDING_FEE in TransactionType
2. Exchange Info
- Added optional query param market
- Added markets, tags, assetPrecisions, conversionRates in the response
- For each contract, from the response:
- Removed: marginAsset, maintMarginPercent
- Added: market, marginAssetsSupported, fundingFeeInterval
3. Open Orders, Order History, Linked Orders
- Added baseAsset, quoteAsset in response
- Added lockedMarginInMarginAsset, lockedMargin, stopPrice, marginAsset, leveragedQty in Order History response
4. Add Margin/ Reduce Margin
- Added asset in response
5. Get order using client order ID, Get order using ref ID
- Added lockedMarginInMarginAsset (optional), baseAsset, quoteAsset, marginAsset in response
6. Place Order
- Added optional field marginAsset in body
- Added lockedMarginInMarginAsset, baseAsset, quoteAsset, marginAsset in response
---
# Change Log – Pi42 API Reference Documentation

# 5/26/25

# 7. Transaction History, Get Transaction using ID

Added baseAsset, quoteAsset in response

# 8. Trade History, Get Trade using ID

Added baseAsset, quoteAsset, marginAsset, feeInMarginAsset (optional), realizedProfitInMarginAsset (optional) in response

# 9. Get Positions, Get Position using position id

Added baseAsset, quoteAsset, marginAsset, marginInMarginAsset (optional), realizedProfitInMarginAsset (optional) in response

# 10. Web Socket Updates

New Events Added:

- Market Info (marketInfo)
- Mark Price Stream for All market (markPriceArr)
- All Market Tickers Streams (tickerArr)

Added new fields in the Response of following events:

- Order Events: marginAsset, market, baseAsset, quoteAsset
- Position Events: market, marginAsset, marginConversionRate, marginSettlementRate, marginInMarginAsset, realizedProfitInMarginAsset
- Trade Events: feeInMarginAsset

# 9-07-2024

# 1. Pagination update of following APIs:

orderHistory, tradeHistory, transactionHistory, openOrders, positions

Removed timestamp query param.

Added optional query params namely:

- startTimestamp (lower bound)
- endTimestamp (upper bound)
- sortOrder (asc or desc)

Response: nextTimestamp which is used in the next paginated API call.

Examples added in the API descriptions section in the doc.

# 2. New Endpoint

Margin History (GET /v1/order/fetch-margin-history)

# 19-06-2024

# 1. Updated Pagination of following APIs:

orderHistory, tradeHistory, transactionHistory, openOrders

Pagination changed from page basis to timestamp basis.

Introduced timestamp basis pagination in positions API.

Response gives a field nextTimestamp, which is used for next API call.

# 06-06-2024

# 1. New Endpoints added

- Get Depth Update (GET /v1/market/depth/:contractPair)
- Get Aggregate trade update (GET /v1/market/aggTrade/:contractPair)
- Get order details using ref ID (GET /v1/order/ref-id)
- Get user id and account ID using ref ID (GET /v1/integration/user)
- Get fiat order details using reference ID (GET /v1/integration/fiat-order-details)
- Get 24hr ticker update (GET /v1/market/ticker24Hr/:contractPair)
- Get trade history based on trade ID (GET /v1/user-data/trade-history/{id})
- Get transaction history based on transaction ID (GET /v1/user-data/transaction-history/{id})

# 2. Updated Endpoints

Two new optional query params (tradeId and positionId) added in (GET /v1/user-data/transaction-history).
---
# Change Log – Pi42 API Reference Documentation

# Updates in body of ( POST /v1/integration/event-replay )

1. Added optional field refId in the responses of place order, get order details using client order id, order history, open orders, linked orders endpoints.
2. Secure Web Socket Updates:
1. In each event, eventTime will be in nanoseconds and type will be string.

# 28-05-2024

1. New Endpoints
- Get Order ( GET /v1/order?clientOrderId=abc )
- Get Position ( GET /v1/positions?positionId=abc )
- Event Replay ( POST /v1/integration/event-replay ): This is just endpoint, we're still deploying the changes.
2. Secure Web Socket Updates:
1. Added new event for Funding Fee named fundingFee

# 20-05-2024

1. Added lockedMargin field in the place-order API response

# 10-05-2024

1. New Endpoint: INR Deposit and Withdraw History ( GET /v1/integration/deposit-withdraw-history )
2. New enums: PaymentType, PaymentStatus
3. Added optional query params for pagination for the following endpoints
- Order History
- Open Orders
- Transaction History
- Trade History
4. Updated public key sharing under Authenticated endpoints.
5. Secure Web Socket Updates:
1. Added eventTime field in all the events.
2. Updated response of order events. In case of orderPartiallyFilled event, use filledAmount instead of cumQty for total filled quantity.
3. New Events:
- Margin Call (marginCallAlert)
- Liquidation (liquidationAlert)
- Trade stream (newTrade)

# Introduction

Pi42 offers a suite of public-facing APIs designed to facilitate integration with various applications and systems, particularly within the domains it specializes in. Here is a high-level introduction to the key features and functionalities of Pi42's public-facing APIs:

1. Authentication and Authorization:
- OAuth 2.0 Support: Pi42 APIs utilize OAuth 2.0 for secure authentication and authorization, ensuring that only authorized users and applications can access the data.
- API Keys: For simpler integrations, Pi42 also supports API keys, allowing developers to authenticate their requests with a unique key.

https://lightningnodes.github.io/slate/?python#change-log
---
# Change Log – Pi42 API Reference Documentation

# 2. Data Access and Management:

Data Retrieval: APIs provide endpoints for retrieving various types of data, such as user information, transaction history, and analytics reports.

Data Insertion and Updates: Developers can use the APIs to insert new data or update existing records in the Pi42 system.

Search and Filtering: Advanced search and filtering capabilities allow developers to query the data efficiently, using parameters like date ranges, status filters, and more.

# 3. Analytics and Reporting:

Real-time Analytics: Access real-time analytics data, enabling applications to display up-to-the-minute information.

Custom Reports: APIs allow the generation of custom reports based on specified criteria, providing flexibility in data analysis.

# 4. Developer Resources:

Comprehensive Documentation: Detailed API documentation, including endpoint descriptions, request and response formats, error codes, and usage examples.

# 5. Compliance and Security:

Data Encryption: All data transmitted via the APIs is encrypted to ensure security and privacy.

Compliance: Pi42 APIs adhere to industry standards and regulations, such as GDPR making them suitable for use in regulated industries like finance.

# Getting Started with Pi42 APIs

APIs provided by Pi42 classifications ensure that only authorized users can access sensitive functionalities, while still allowing open access to non-sensitive information or system statuses.

# AUTHENTICATED APIS

The Authenticated endpoints require users to provide valid credentials before access is granted. These endpoints are secured, ensuring that only authorized users can interact with sensitive data or perform privileged operations. Authentication typically involves the use of tokens, API keys, or OAuth, which must be included in the request header. These endpoints are designed for operations that involve personal data, secure transactions, or actions that could impact the system's state or other users.

# APIs that require trade permissions:

- /v1/order/place-order
- /v1/order/delete-order
- /v1/order/add-margin
- /v1/order/reduce-margin
- /v1/exchange/update/leverage
- /v1/order/cancel-all-orders
- /v1/positions/close-all-positions

# PUBLIC APIS

https://lightningnodes.github.io/slate/?python#change-log
---
# Change Log – Pi42 API Reference Documentation

The Public endpoints are accessible without any authentication, allowing open access to certain resources or information. These endpoints are designed to handle requests that do not require user identification or secure access, such as fetching general information, retrieving publicly available data, or providing status updates. While public, these endpoints are still subject to rate limiting and monitoring to prevent abuse or misuse of the system.

# Endpoints which DO NOT require api-key and signature authentication:

- /v1/market/klines
- /v1/market/depth
- /v1/market/aggTrade
- /v1/market/ticker24Hr

# Base URLs for:

- Authenticated endpoints: https://fapi.pi42.com/
- Public endpoints: https://api.pi42.com/

# To begin using Pi42 Authenticated APIs, follow these steps:

1. API Key Creation
Users can create an API key, which will be associated with a secret. The secret will be shown only once during the creation process.
2. Signature Generation
For each authenticated request, users need to generate a signature using their secret key.

- For GET requests: The data to be signed is the query string, which includes the timestamp and any other query parameters.
- For POST/PUT/DELETE requests: The data to be signed is the body of the request, which includes the timestamp, and any other fields.
- The signature is generated by applying HMAC-SHA256 to the data (query string or body) using the user's secret key.
- The generated signature is sent in the request headers along with the API key.

# getRequest Function

The getRequest function sends a GET request to an API endpoint, handling both market and non-market endpoints differently. It adds a timestamp to the parameters for request uniqueness, generates a signature for authentication, and processes the response.

Sends a GET request to the specified endpoint with the given parameters:

- endpoint (string): The API endpoint to which the request is sent.
- params (Object, optional): Query parameters to include in the request. Defaults to an empty object.

# RESPONSE

- Returns: A Promise that resolves to the response data from the API.
- Error Handling: If an error occurs during the request, it logs the error message or response data to the console.

# postRequest Function

The function sends POST requests to an API endpoint, handling both authenticated and public requests based on the endpoint URL.
---
# Change Log – Pi42 API Reference Documentation

# patchRequest Function

The function sends PATCH requests to an API endpoint.

- endpoint (string): The API endpoint to which the PATCH request is sent.
- params (object): The parameters to be included in the PATCH request body. This is optional and defaults to an empty object.

# RESPONSE

console.log("Response:", response.data);

Logs the response data to the console.

return response.data;

Returns the response data for further use.

# putRequest Function

This function, putRequest, is an asynchronous JavaScript function designed to send a signed PUT HTTP request to a specified API endpoint. Here's a breakdown of its components and behavior:

- endpoint: A string representing the API endpoint to which the request will be sent. It is appended to a base URL to form the complete request URL.
- params: An optional object containing the parameters to be included in the request body. If no parameters are provided, an empty object is used by default.

# RESPONSE

If the request is successful, the response data is logged to the console and returned by the function.

# deleteRequest Function

This deleteRequest function is an asynchronous JavaScript function designed to send a signed DELETE HTTP request to a specified API endpoint. Below is a detailed explanation of its components and behavior:

- endpoint: A string representing the API endpoint to which the DELETE request will be sent. It is appended to a base URL to form the complete request URL.
- params: An optional object containing the parameters to be included in the request. If no parameters are provided, an empty object is used by default.
---
# Change Log – Pi42 API Reference Documentation

# API Rate Limits

Rate limits are mechanisms used to control the frequency of requests that can be made to an API. These rate limits are essential for maintaining optimal performance and avoiding server overloads, ensuring a smooth and reliable user experience across all API interactions.

Different endpoints may have varying rate limits depending on their purpose and the resources they consume.

| Endpoint              | Interval      | Limit       |
| --------------------- | ------------- | ----------- |
| v1/order/place-order  | 1 second (1s) | 20 requests |
| v1/order/delete-order | 1 minute (1m) | 30 requests |
| All other endpoints   | 1 minute (1m) | 60 requests |

# Orders

# Place an Order

def generate_signature(api_secret, data_to_sign):
return hmac.new(api_secret.encode('utf-8'), data_to_sign.encode('utf-8'), hashlib.sha256).hexdigest()

POST /v1/order/place-order

Place an order (either a market order or a limit order) on Pi42's trading platform. It allows users to submit an order to buy or sell a specific asset.

Note:

- Price is compulsory to place a limit order.
- To successfully place an order from a position, you need to pass the placeType as POSITION and positionId in the request payload, which can be obtained calling the Get Positions API.

def place_order():
# Generate the current timestamp in milliseconds
timestamp =  str(int(time.time() * 1000))
# Define the order parameters
params = {
'timestamp':  timestamp,       # Current timestamp in milliseconds
'placeType':  'ORDER_FORM',    # Type of order placement, e.g., 'ORDER_FORM'
'quantity': 0.002,             # Quantity of the asset to trade
'side':  'BUY',                # Order side, either 'BUY' or 'SELL'
'symbol': 'BTCUSDT',           # Trading pair, e.g., Bitcoin to USDT
'type':  'MARKET',             # Order type, either 'MARKET' or 'LIMIT'
'reduceOnly':  False,          # Whether to reduce an existing position only
'marginAsset': 'INR',          # The asset used as margin (INR in this case)
'deviceType':  'WEB',          # Device type (e.g., WEB, MOBILE)
'userCategory': 'EXTERNAL',    # User category (e.g., EXTERNAL, INTERNAL)
---
# Change Log – Pi42 API Reference Documentation

'price': 50000,                # Price for the limit order (included here but irrelevant for market orders)

# Convert the parameters to a JSON string to sign
data_to_sign  = json.dumps(params, separators=(',', ':'))
# Generate the signature for authentication
signature =  generate_signature(api_secret, data_to_sign)
# Define the headers including the API key and the signature
headers = {
'api-key': api_key,
'signature': signature,
}
try:
# Send the POST request to place the order
response  = requests.post(f'{base_url}/v1/order/place-order', json=params, headers=headers)
# Raise an HTTPError if the response status is 4xx or 5xx
response.raise_for_status()
# Parse the JSON response data
response_data = response.json()
# Print the success message with the order details
print('Order placed successfully:', json.dumps(response_data, indent=4))
except requests.exceptions.HTTPError as err:
# Handle HTTP errors specifically
print(f"Error: {err.response.text if err.response else err}")
except Exception  as e:
# Handle any other unexpected errors
print(f"An unexpected error occurred: {str(e)}")

| Parameter       | Type    | Required    | Description                                                                                                          |
| --------------- | ------- | ----------- | -------------------------------------------------------------------------------------------------------------------- |
| quantity        | number  | No          | The amount of the asset to be ordered. Specify the desired quantity.                                                 |
| price           | number  | Conditional | The price at which to place the LIMIT/STOP\_LIMIT order. Must be specified if orderType is "LIMIT" or "STOP\_LIMIT". |
| placeType       | string  | Yes         | Can be either "ORDER\_FORM" or "POSITION". Indicates the type of order placement.                                    |
| side            | string  | Yes         | The side of the order, which is "BUY" in this case.                                                                  |
| symbol          | string  | Yes         | The trading pair symbol, for example, "GRTINR".                                                                      |
| reduceOnly      | boolean | No          | Indicates whether the order should only reduce the position. Default is false.                                       |
| marginAsset     | string  | Yes         | The asset used for margin, such as "INR".                                                                            |
| orderType       | string  | Yes         | The type of the order. It can be MARKET, LIMIT, STOP\_MARKET or STOP\_LIMIT.                                         |
| takeProfitPrice | number  | No          | Price at which take profit order should be executed.                                                                 |
| stopLossPrice   | number  | No          | Price at which stop loss order should be executed.                                                                   |
| stopPrice       | number  | No          | Compulsory for STOP\_MARKET and STOP\_LIMIT orders                                                                   |

# RESPONSE

The response parameters are described below:

https://lightningnodes.github.io/slate/?python#change-log
---
# Change Log – Pi42 API Reference Documentation

# Response

{
"clientOrderId": "19db8caf3cd3e5a08cfa-6895-ext",
"time": "2024-09-13T08:19:18.029Z",
"symbol": "BTCUSDT",
"contractType": "PERPETUAL",
"type": "MARKET",
"side": "BUY",
"price": 58002,
"orderAmount": 0.003,
"filledAmount": 0,
"availableBalance": 8564.64,
"linkId": "19db8caf3cd3e5a08cfa-6895-ext",
"linkType":  "ORDER",
"subType": "PRIMARY",
"placeType": "ORDER_FORM",
"lockedMargin": 19.5274,
"baseAsset": "BTC",
"quoteAsset": "USDT",
"marginAsset": "INR",
"lockedMarginInMarginAsset": 1698.88,
"leverage":  10
}

| Parameter        | Description                                                                                      |
| ---------------- | ------------------------------------------------------------------------------------------------ |
| clientOrderId    | Unique identifier for the client order (19db8caf3cd3e5a08cfa-6895-ext).                          |
| time             | Timestamp when the order was placed (2024-09-13T08:19:18.029Z).                                  |
| symbol           | The trading pair for the order (BTCUSDT), indicating Bitcoin (BTC) traded against USDT (Tether). |
| contractType     | The type of contract for the order (PERPETUAL), indicating a perpetual futures contract.         |
| type             | The type of order (MARKET), indicating a market order.                                           |
| side             | The side of the order (BUY).                                                                     |
| price            | The price at which the order is to be executed (58002 USDT).                                     |
| orderAmount      | The amount of the order (0.003 BTC).                                                             |
| filledAmount     | The amount of the order that has been filled (0, indicating no amount has been filled yet).      |
| availableBalance | The available balance for the order (8564.64 INR).                                               |
| linkId           | Link identifier associated with the order (19db8caf3cd3e5a08cfa-6895-ext).                       |
| linkType         | The type of link for the order (ORDER).                                                          |
| subType          | Subtype of the order (PRIMARY).                                                                  |
| placeType        | The method used to place the order (ORDER\_FORM).                                                |
| lockedMargin     | The amount of margin locked for the order (19.5274 INR).                                         |
| baseAsset        | The base asset being traded (BTC).                                                               |
| quoteAsset       | The currency used for the transaction (USDT).                                                    |
| marginAsset      | The asset used for margin (INR).                                                                 |

https://lightningnodes.github.io/slate/?python#change-log
---
# Change Log – Pi42 API Reference Documentation

| Parameter                 | Description                                                    |
| ------------------------- | -------------------------------------------------------------- |
| lockedMarginInMarginAsset | The amount of margin locked in the margin asset (1698.88 INR). |
| leverage                  | Leverage set for contract pair.                                |

# Edit an Order

# PATCH /v1/order/edit-order

Edit a LIMIT or STOP order.

Note: When the new quantity, price or stopPrice does not satisfy validations, or there is not enough available balance for editing order, the edit request will be rejected and the order will stay as it is.

# # Function to edit/update order

def edit_order(client_order_id, quantity=None, stop_price=None, price=None):
# Generate the current timestamp
timestamp = str(int(time.time() * 1000))
# Prepare the request body (JSON)
params = {
'clientOrderId': str(client_order_id),
'timestamp': timestamp
}
if(quantity):
params['quantity'] = int(quantity)
if(stop_price):
params['stopPrice'] = int(stop_price)
if(price):
params['price'] = int(price)
# Convert the request body to a JSON string for signing
data_to_sign = json.dumps(params, separators=(',', ':'))
# Generate the signature
signature = generate_signature(api_secret, data_to_sign)
# Headers for the PATCH request
headers = {
'api-key': api_key,
'Content-Type': 'application/json',
'signature': signature
}
# Construct the full URL
edit_order_url = f"{base_url}/v1/order/edit-order"
try:
# Send the PATCH request to edit the order
response = requests.patch(edit_order_url, json=params, headers=headers)
response.raise_for_status()   # Raises an error for 4xx/5xx responses
response_data = response.json()
print('Order edit request sent', json.dumps(response_data, indent=4), "for:", quantity)
except requests.exceptions.HTTPError as err:
print(response)
https://lightningnodes.github.io/slate/?python#change-log
---
# Change Log – Pi42 API Reference Documentation

# print(f"Error: {err.response.text if err.response else err}")
except Exception  as e:
print(f"An unexpected error occurred: {str(e)}")

# Parameter

| Parameter     | Type   | Required | Description                                                             |
| ------------- | ------ | -------- | ----------------------------------------------------------------------- |
| clientOrderId | string | Yes      | The clientOrderId of the “LIMIT”, “STOP\_LIMIT” or “STOP\_MARKET” order |
| quantity      | number | No       | The amount of the asset to be ordered. Specify the desired quantity.    |
| price         | number | No       | Can only be sent if order is “LIMIT” or “STOP\_LIMIT”                   |
| stopPrice     | number | No       | Can only be sent if order is “STOP\_LIMIT” or “STOP\_MARKET”            |

# RESPONSE

# Response

{
status: "Edit request submitted successfully",
availableBalance: 700,
lockedMargin: 200,
lockedMarginInMarginAsset: 200
}

# Parameter

| Parameter                 | Description                                                                                                   |
| ------------------------- | ------------------------------------------------------------------------------------------------------------- |
| status                    | Information about the submitted request (Edit request submitted successfully).                                |
| availableBalance          | Updated available balance if extra margin is locked for the edit request (700 INR).                           |
| lockedMargin              | Updated locked margin for the order if extra margin is locked for the edit request (300 INR)                  |
| lockedMarginInMarginAsset | Updated locked margin in margin asset for the order if extra margin is locked for the edit request. (300 INR) |

# Add Margin

# POST /v1/order/add-margin

Add margin to a specific position. It requires a unique position ID and the amount of margin to be added. This operation helps in increasing the margin available for a given position, which can be used for trading or managing positions.

def add_margin():
position_id  = input("Enter the positionId: ")
amount_input = input("Enter the amount: ")
add_margin_url = "https://fapi.pi42.com/v1/order/add-margin"
try:
amount  = int(amount_input)
except ValueError:
amount  = float(amount_input)
timestamp =  str(int(time.time() * 1000))
params = {
'positionId': position_id,

https://lightningnodes.github.io/slate/?python#change-log
---
# Change Log – Pi42 API Reference Documentation

'amount': amount,
'timestamp':  timestamp
}
data_to_sign  = json.dumps(params, separators=(',', ':'))
signature =  generate_signature(api_secret, data_to_sign)
headers = {
'api-key': api_key,
'Content-Type': 'application/json',
'signature':  signature,
}
try:
response  = requests.post(add_margin_url, json=params, headers=headers)
response.raise_for_status()
response_data = response.json()
print('Margin added successfully:', json.dumps(response_data, indent=4))
except requests.exceptions.HTTPError as  err:
print(f"Failed {response.status_code}: {response.text}")
except Exception  as e:
print(f"An unexpected error occurred: {str(e)}")

# Parameter

| positionId | string | Yes | Unique identifier for the position to which margin is being added |
| ---------- | ------ | --- | ----------------------------------------------------------------- |
| amount     | number | Yes | Amount of margin to be added to the specified position            |

The required positionId can be obtained calling the Get Positions API

# RESPONSE

# Response

{
"lockedBalance": 870,
"withdrawableBalance": 9393.52,
"asset": "INR",
"message": "Margin added successfully"
}

# Parameter

| lockedBalance       | The amount of balance that is locked and cannot be withdrawn (870 INR). |
| ------------------- | ----------------------------------------------------------------------- |
| withdrawableBalance | The amount of balance available for withdrawal (9393.52 INR).           |
| asset               | The asset or currency being used (INR).                                 |
| message             | A confirmation message indicating that margin was added successfully.   |

# Reduce Margin

POST /v1/order/reduce-margin

Reduce the margin on an existing trading position.

https://lightningnodes.github.io/slate/?python#change-log
---
# Change Log – Pi42 API Reference Documentation

def reduce_margin():
# Collect position ID and amount to reduce from user input
position_id  = input("Enter the positionId: ")
amountInput  = input("Enter the amount to reduce: ")
try:
# Convert input to integer or float as necessary
amount  = int(amountInput)
except ValueError:
amount  = float(amountInput)
# Generate current timestamp in milliseconds
timestamp =  str(int(time.time() *  1000))
# Prepare the request payload (JSON)
params = {
'positionId': position_id,
'amount': amount,
'timestamp':  timestamp
}
# Convert the payload to a JSON string for signature
data_to_sign  = json.dumps(params,  separators=(',', ':'))
# Generate the signature using a helper function
signature =  generate_signature(api_secret, data_to_sign)
# Set the headers for the POST request
headers = {
'api-key': api_key,
'Content-Type': 'application/json',
'signature':  signature
}
# Construct the full API endpoint URL
reduce_margin_url  =  f"{base_url}/v1/order/reduce-margin"
try:
# Send the POST request to reduce margin
response  = requests.post(reduce_margin_url, json=params, headers=headers)
response.raise_for_status()  # Raises an error for HTTP responses with 4xx/5xx status codes
response_data  = response.json()
print('Margin reduced successfully:',  json.dumps(response_data, indent=4))
except requests.exceptions.HTTPError as  err:
print(f"Error: {err.response.text if  err.response else err}")
except Exception  as  e:
print(f"An unexpected error occurred: {str(e)}")

| Parameter  | Type   | Required | Description                                                           |
| ---------- | ------ | -------- | --------------------------------------------------------------------- |
| positionId | string | Yes      | Unique identifier for the position from which margin is being reduced |
| amount     | number | Yes      | Amount of margin to reduce from the specified position                |

The required positionId can be obtained calling the Get Positions API

# RESPONSE

The JSON body returned in the response is as follows:

{
"lockedBalance": 870,
"withdrawableBalance": 9393.52,

https://lightningnodes.github.io/slate/?python#change-log
---
# Change Log – Pi42 API Reference Documentation

"asset": "INR",
"message": "Margin reduced successfully"

| Parameter           | Description                                                             |
| ------------------- | ----------------------------------------------------------------------- |
| lockedBalance       | The amount of balance that is locked and cannot be withdrawn (870 INR). |
| withdrawableBalance | The amount of balance available for withdrawal (9393.52 INR).           |
| asset               | The asset or currency being used (INR).                                 |
| message             | A confirmation message indicating that margin was reduced successfully. |

# Get Open Orders

GET /v1/order/open-orders

Retrieves the open orders for a given account. It supports filtering results based on optional parameters such as page size, sorting order, and timestamps. The symbol parameter can be used to filter the results to a specific trading pair. This endpoint is useful for fetching the current active orders and managing them accordingly.

def get_open_orders():
# Generate the current timestamp
timestamp =  str(int(time.time() * 1000))
# Prepare parameters with the current timestamp
params  = f"timestamp={timestamp}"
# Generate the signature using the current timestamp
signature =  generate_signature(api_secret, params)
# Prepare headers
headers = {
'api-key':  api_key,
'signature': signature,
}
open_orders_url = f"{base_url}/v1/order/open-orders"
try:
# Send GET request to fetch open orders with the timestamp parameter
response =  requests.get(open_orders_url, headers=headers, params={'timestamp': timestamp})
response.raise_for_status() # Raises an error for bad HTTP responses
response_data = response.json()
print('Open orders fetched successfully:', json.dumps(response_data, indent=4))
except requests.exceptions.HTTPError as  err:
print(f"Failed {response.status_code}: {response.text}")
except Exception as e:
print(f"An unexpected error occurred: {str(e)}")

| Parameter      | Type   | Required | Description                                                     |
| -------------- | ------ | -------- | --------------------------------------------------------------- |
| pageSize       | string | No       | The number of results to return per page                        |
| sortOrder      | string | No       | The sorting order for the results (e.g., "asc" or "desc")       |
| startTimestamp | string | No       | The start timestamp (in milliseconds) for filtering open orders |
| endTimestamp   | string | No       | The end timestamp (in milliseconds) for filtering open orders   |

https://lightningnodes.github.io/slate/?python#change-log
---
# Change Log – Pi42 API Reference Documentation

| Parameter | Type   | Required | Description                                                  |
| --------- | ------ | -------- | ------------------------------------------------------------ |
| symbol    | string | No       | The trading pair symbol to filter the orders (e.g., BTCUSDT) |

# RESPONSE

The response parameters are described below:

[
{
"clientOrderId": "ccef6a84a5cf6a463353-6238-ext",
"time": "2024-09-13T07:57:15.305Z",
"symbol": "BTCINR",
"contractType": "PERPETUAL",
"type": "MARKET",
"side": "BUY",
"price": 5170418,
"orderAmount": 0.002,
"filledAmount": 0,
"linkId": "ccef6a84a5cf6a463353-6238-ext",
"linkType":  "ORDER",
"subType": "PRIMARY",
"placeType": "ORDER_FORM",
"baseAsset": "BTC",
"quoteAsset": "INR",
"leverage":  10,
"lockedMargin": 1034.8
}
]

| Parameter     | Description                                                                                                       |
| ------------- | ----------------------------------------------------------------------------------------------------------------- |
| clientOrderId | Unique identifier for the client's order (ccef6a84a5cf6a463353-6238-ext).                                         |
| time          | Timestamp when the order was placed (2024-09-13T07:57:15.305Z).                                                   |
| symbol        | Trading pair involved (BTCINR), indicating Bitcoin (BTC) traded against Indian Rupees (INR).                      |
| contractType  | Type of contract (PERPETUAL), suggests a perpetual futures contract.                                              |
| type          | The order type (MARKET), meaning the order will be executed immediately at the current market price.              |
| side          | Indicates whether the order is to buy or sell (BUY).                                                              |
| price         | The price per unit of Bitcoin at the time the order was placed (5170418 INR per BTC).                             |
| orderAmount   | The amount of Bitcoin to be purchased (0.002 BTC).                                                                |
| filledAmount  | Amount of the order that has been filled so far (0, indicating it hasn't been executed yet).                      |
| linkId        | Additional reference that ties this order to a broader system or linked entities (ccef6a84a5cf6a463353-6238-ext). |
| linkType      | The type of link (ORDER).                                                                                         |
| subType       | Order classification (PRIMARY), indicating the main order type.                                                   |
| placeType     | Describes where the order was placed from (ORDER\_FORM).                                                          |
| baseAsset     | The asset being bought (Bitcoin).                                                                                 |
| quoteAsset    | The currency used for the transaction (INR).                                                                      |

https://lightningnodes.github.io/slate/?python#change-log
---
# Change Log – Pi42 API Reference Documentation

| Parameter    | Description                     |
| ------------ | ------------------------------- |
| leverage     | Leverage set for contract pair. |
| lockedMargin | Margin locked in the order.     |

# Get Order History

# GET /v1/order/order-history

Provides historical order data for a given account. It supports optional filtering by page size, sorting order, and timestamps to narrow down the results. The symbol parameter allows filtering the results to a specific trading pair. This endpoint is helpful for reviewing past orders and analyzing historical trading activity.

# Function to fetch and display order history
def order_history():
timestamp  = str(int(time.time() * 1000))
order_history_url = "https://fapi.pi42.com/v1/order/order-history"
params = {
'sortOrder': 'desc',
'pageSize': 100,
'timestamp': timestamp
}
query_string = f"sortOrder={params['sortOrder']}&pageSize={params['pageSize']}&timestamp={params['timestamp']}"
signature  = generate_signature(api_secret, query_string)
headers =  {
'api-key': api_key,
'signature': signature,
}
try:
response = requests.get(f"{order_history_url}?{query_string}", headers=headers)
response.raise_for_status()
response_data = response.json()
print('Order history fetched successfully:', json.dumps(response_data, indent=4))
except requests.exceptions.HTTPError as err:
print(f"Failed {response.status_code}: {response.text}")

| Parameter      | Type   | Required | Description                                                       |
| -------------- | ------ | -------- | ----------------------------------------------------------------- |
| pageSize       | string | No       | The number of results to return per page                          |
| sortOrder      | string | No       | The sorting order for the results (e.g., "asc" or "desc")         |
| startTimestamp | string | No       | The start timestamp (in milliseconds) for filtering order history |
| endTimestamp   | string | No       | The end timestamp (in milliseconds) for filtering order history   |
| symbol         | string | No       | The trading pair symbol to filter the orders (e.g., BTCUSDT)      |

# RESPONSE

The details of the JSON object returned in the response body are as follows:

https://lightningnodes.github.io/slate/?python#change-log
---
# Change Log – Pi42 API Reference Documentation

[
{
"clientOrderId": "c707985129f41a13ab40-6238-ext",
"updatedAt": "2024-09-13T10:48:57.630Z",
"symbol": "BTCINR",
"type": "MARKET",
"isIsolated": true,
"side": "SELL",
"price": "5182995",
"avgPrice":  "5182656",
"origQty":  "10365.31",
"cumQty": "0.002",
"executedQty": "0.002",
"reduceOnly": false,
"status": "FILLED",
"leverage":  25,
"subType":  "PRIMARY",
"stopPrice": null,
"lockedMargin": 0,
"lockedMarginInMarginAsset": 0,
"marginAsset": "INR",
"contractType": "PERPETUAL",
"iconUrl":  "https://storage.googleapis.com/pi42-dev-static/contract-icons/btc.png",
"quoteAsset": "INR",
"baseAsset": "BTC",
"leveragedQty": 0.002
}
]

| Parameter     | Description                                                                                        |
| ------------- | -------------------------------------------------------------------------------------------------- |
| clientOrderId | Unique identifier for the client's order ( c707985129f41a13ab40-6238-ext ).                        |
| updatedAt     | The timestamp when the order was last updated ( 2024-09-13T10:48:57.630Z ).                        |
| symbol        | The trading pair involved ( BTCINR ), indicating Bitcoin (BTC) traded against Indian Rupees (INR). |
| type          | The order type ( MARKET ), meaning the order was executed at the current market price.             |
| isIsolated    | Indicates whether the order is isolated ( true ), meaning it's an isolated margin trade.           |
| side          | Indicates whether the order is to buy or sell ( SELL ).                                            |
| price         | The price per unit of Bitcoin at the time the order was placed ( 5182995 INR per BTC ).            |
| avgPrice      | The average price at which the order was executed ( 5182656 INR per BTC ).                         |
| origQty       | The original quantity in INR before conversion to BTC ( 10365.31 INR ).                            |
| cumQty        | The cumulative amount of Bitcoin executed so far ( 0.002 BTC ).                                    |
| executedQty   | The total executed quantity of the order ( 0.002 BTC ).                                            |
| reduceOnly    | A flag indicating if the order is only to reduce an existing position ( false ).                   |
| status        | The current status of the order ( FILLED ), meaning the order is completely executed.              |
| leverage      | The leverage applied to the trade ( 25x ).                                                         |
| subType       | The order classification ( PRIMARY ), indicating the main order type.                              |
| stopPrice     | The stop price associated with the order ( null ), as this is not a stop order.                    |

https://lightningnodes.github.io/slate/?python#change-log
---
# Change Log – Pi42 API Reference Documentation

| Parameter                 | Description                                                                |
| ------------------------- | -------------------------------------------------------------------------- |
| lockedMargin              | The amount of margin locked in INR (0 INR).                                |
| lockedMarginInMarginAsset | The amount of margin locked in the margin asset (0 INR).                   |
| marginAsset               | The asset used for margin (INR).                                           |
| contractType              | The type of contract (PERPETUAL), indicating a perpetual futures contract. |
| iconUrl                   | The URL of the contract icon (BTC Icon).                                   |
| quoteAsset                | The currency used for the transaction (INR).                               |
| baseAsset                 | The asset being traded (Bitcoin).                                          |
| leveragedQty              | The quantity of Bitcoin being traded with leverage (0.002 BTC).            |

# Get Linked Orders

# GET /v1/order/linked-orders

Retrieves orders that are linked by a specific link ID. It is used to fetch all orders associated with a given link ID, which can help in tracking related orders or managing linked order groups.

# Function to fetch linked orders based on linkId
def linked_orders():
link_id  =  input("Enter the Link Id: ")
timestamp   = str(int(time.time() * 1000))
linked_orders_url = "https://fapi.pi42.com/v1/order/linked-orders"
url = f"{linked_orders_url}/{link_id}"
params =  {
'timestamp': timestamp
}
query_string =  f"timestamp={params['timestamp']}"
signature   = generate_signature(api_secret, query_string)
headers  =  {
'api-key': api_key,
'signature': signature,
'accept':   '*/*'
}
try:
response  = requests.get(f"{url}?{query_string}", headers=headers)
response.raise_for_status()
response_data = response.json()
print('Linked orders fetched successfully:',  json.dumps(response_data, indent=4))
except requests.exceptions.HTTPError as  err:
print(f"Failed  {response.status_code}: {response.text}")

| Parameter | Type   | Required | Description                                 |
| --------- | ------ | -------- | ------------------------------------------- |
| linkId    | string | Yes      | The unique identifier for the linked orders |

https://lightningnodes.github.io/slate/?python#change-log
---
# Change Log – Pi42 API Reference Documentation

Requires linkId that can be obtained from Place Order API response.

# RESPONSE

The details returned in the response body as are as follows:

// Response
[
{
"clientOrderId":  "m2l-1f04cd91efa7ebe09cad-6238-ext",
"time": "2024-09-11T12:14:03.706Z",
"symbol": "BTCINR",
"contractType": "PERPETUAL",
"type": "MARKET",
"side": "BUY",
"price": 5054068,
"orderAmount": 0.002,
"filledAmount": 0,
"linkId": "m2l-1f04cd91efa7ebe09cad-6238-ext",
"subType": "PRIMARY",
"linkType": "ORDER_SL",
"takeProfitPrice": null,
"stopLossPrice":  null,
"status": "NEW",
"placeType": "ORDER_FORM",
"baseAsset": "BTC",
"quoteAsset": "INR"
}
]

| Parameter       | Description                                                                                        |
| --------------- | -------------------------------------------------------------------------------------------------- |
| clientOrderId   | Unique identifier for the client's order ( m2l-1f04cd91efa7ebe09cad-6238-ext ).                    |
| time            | The timestamp when the order was created ( 2024-09-11T12:14:03.706Z ).                             |
| symbol          | The trading pair involved ( BTCINR ), indicating Bitcoin (BTC) traded against Indian Rupees (INR). |
| contractType    | The type of contract ( PERPETUAL ), indicating a perpetual futures contract.                       |
| type            | The order type (MARKET ), meaning the order was executed at the current market price.              |
| side            | Indicates whether the order is to buy or sell ( BUY ).                                             |
| price           | The price per unit of Bitcoin at the time the order was placed ( 5054068 INR ).                    |
| orderAmount     | The total amount of Bitcoin to be bought (0.002 BTC ).                                             |
| filledAmount    | The amount of Bitcoin that has been filled so far ( 0 BTC ).                                       |
| linkId          | Unique identifier for the linked order ( m2l-1f04cd91efa7ebe09cad-6238-ext ).                      |
| subType         | The order classification ( PRIMARY ), indicating the main order type.                              |
| linkType        | Indicates the link type of the order ( ORDER\_SL ), possibly linking to a stop-loss order.         |
| takeProfitPrice | The take-profit price associated with the order ( null ), indicating no take-profit price set.     |
| stopLossPrice   | The stop-loss price associated with the order ( null ), indicating no stop-loss price set.         |

https://lightningnodes.github.io/slate/?python#change-log
---
# Change Log – Pi42 API Reference Documentation

| Parameter  | Description                                                                                     |
| ---------- | ----------------------------------------------------------------------------------------------- |
| status     | The current status of the order ( NEW ), meaning the order has been placed but not filled.      |
| placeType  | The method by which the order was placed ( ORDER\_FORM ), likely using an order form interface. |
| baseAsset  | The base asset being traded (BTC ).                                                             |
| quoteAsset | The currency used for the transaction ( INR ).                                                  |

# Fetch Margin History

# GET /v1/order/fetch-margin-history

Retrieves the margin history for an account. It supports optional filtering parameters like page size, sorting order, timestamps, and trading symbol. This endpoint is useful for analyzing past margin activities and historical changes in margin levels.

def fetch_margin_history():
endpoint   =  "/v1/order/fetch-margin-history"
symbol  = input("Enter the symbol (e.g., BTCUSDT): ").upper()
pageSize   =  100
sortOrder =    "desc"
# Generate current timestamp for signing
timestamp  = str(int(time.time() * 1000))
# Prepare query parameters
params  =  {
'pageSize':    str(pageSize),
'sortOrder': sortOrder,
'symbol': symbol,
'timestamp': timestamp
}
# Convert params to query string
query_string   = '&'.join([f"{key}={value}" for key, value in params.items()])
# Generate signature
signature =    generate_signature(api_secret, query_string)
# Headers for the request
headers =   {
'api-key':    api_key,
'signature': signature,
'accept': '*/*'
}
full_url  = f"{base_url}{endpoint}?{query_string}"
try:
# Send the GET request to fetch margin history
response  = requests.get(full_url,    headers=headers)
response.raise_for_status()  # Raises an error for 4xx/5xx responses
response_data   =  response.json()
print('Margin history fetched successfully:',  json.dumps(response_data, indent=4))
except requests.exceptions.HTTPError as  err:
print(f"Error:    {err.response.text  if err.response else err}")
except Exception   as e:
print(f"An unexpected error occurred:  {str(e)}")
https://lightningnodes.github.io/slate/?python#change-log
---
# Change Log – Pi42 API Reference Documentation

| Parameter      | Type   | Required | Description                                                          |
| -------------- | ------ | -------- | -------------------------------------------------------------------- |
| pageSize       | string | No       | The number of results to return per page                             |
| sortOrder      | string | No       | The sorting order for the results (e.g., "asc" or "desc")            |
| startTimestamp | string | No       | The start timestamp (in milliseconds) for filtering margin history   |
| endTimestamp   | string | No       | The end timestamp (in milliseconds) for filtering margin history     |
| symbol         | string | No       | The trading pair symbol to filter the margin history (e.g., BTCUSDT) |

# RESPONSE

The response details are as follows:

// Response
{
"data": [
{
"id": 549,
"amount": 0.1,
"refId": null,
"marginInMarginAsset": 8.7,
"marginAsset": "INR",
"positionId": "90483119-0c3a-4cc0-9afa-25366f907fca",
"operation": "REDUCE_MARGIN",
"createdAt": "2024-09-12T08:59:57.707Z",
"updatedAt": "2024-09-12T08:59:57.707Z"
}
],
"totalCount": 45,
"nextTimestamp": "1725624883814"
}

| Parameter           | Description                                                                                                     |
| ------------------- | --------------------------------------------------------------------------------------------------------------- |
| id                  | Unique identifier for the margin operation (549).                                                               |
| amount              | The amount involved in the margin operation (0.1).                                                              |
| refId               | Reference ID associated with the operation (null, indicating no reference ID).                                  |
| marginInMarginAsset | Margin in the margin asset (8.7 INR).                                                                           |
| marginAsset         | The asset used for margin (INR).                                                                                |
| positionId          | Unique identifier for the position associated with the margin operation (90483119-0c3a-4cc0-9afa-25366f907fca). |
| operation           | The type of operation performed (REDUCE\_MARGIN).                                                               |
| createdAt           | Timestamp when the margin operation was created (2024-09-12T08:59:57.707Z).                                     |
| updatedAt           | Timestamp when the margin operation was last updated (2024-09-12T08:59:57.707Z).                                |
| totalCount          | The total number of margin operations recorded (45).                                                            |
| nextTimestamp       | The next timestamp for fetching data (1725624883814).                                                           |

https://lightningnodes.github.io/slate/?python#change-log
---
# Change Log – Pi42 API Reference Documentation

# Get Positions

# GET /v1/positions

Retrieves positions based on their status. It allows filtering positions by their status (e.g., "OPEN") and supports additional optional parameters such as timestamps, sorting order, page size, and trading symbol. This endpoint is useful for fetching current or historical positions and managing your trading portfolio.

# Function to fetch positions

def fetch_positions():
position_status = input("Enter position status (open, closed, liquidated): ").upper()
symbol  =  input("Enter the trading pair (e.g., BTCINR): ").upper()
if position_status not  in ["OPEN", "CLOSED", "LIQUIDATED"]:
print("Invalid position status. Please enter 'open', 'closed', or 'liquidated'.")
return
# Optional parameters
sort_order  = "desc" # Default sort order
page_size   = 100 # Default page size
# Prepare the query parameters
params  =  {
'sortOrder': sort_order,
'pageSize': str(page_size),
'symbol':   symbol,
}
# Generate current timestamp
timestamp   = str(int(time.time() * 1000))
params['timestamp'] =  timestamp
# Generate signature based on the parameters
query_string =  '&'.join([f"{key}={value}" for key, value in params.items()])
signature   = generate_signature(api_secret, query_string)
# Headers for the GET request
headers =   {
'api-key': api_key,
'signature': signature,
'accept':   '*/*'
}
# Construct the full URL including the path parameter for position status
full_url   = f"{base_url}/v1/positions/{position_status}?{query_string}"
try:
# Send the GET request to fetch positions
response   = requests.get(full_url,  headers=headers)
response.raise_for_status()  # Raises an error for 4xx/5xx responses
response_data = response.json()
print('Positions fetched successfully:', json.dumps(response_data, indent=4))
except requests.exceptions.HTTPError as  err:
print(f"Error:  {err.response.text   if err.response else err}")
except Exception as e:
print(f"An unexpected error occurred:  {str(e)}")

# Parameters

| Parameter      | Type   | Required | Description                                                   |
| -------------- | ------ | -------- | ------------------------------------------------------------- |
| positionStatus | string | Yes      | The status of the positions to retrieve (e.g., "OPEN")        |
| startTimestamp | string | No       | The start timestamp (in milliseconds) for filtering positions |

https://lightningnodes.github.io/slate/?python#change-log
---
# Change Log – Pi42 API Reference Documentation

# Parameters

| Parameter    | Type   | Required | Description                                                 |
| ------------ | ------ | -------- | ----------------------------------------------------------- |
| endTimestamp | string | No       | The end timestamp (in milliseconds) for filtering positions |
| sortOrder    | string | No       | The sorting order for the results (e.g., "asc" or "desc")   |
| pageSize     | string | No       | The number of results to return per page                    |
| symbol       | string | No       | The trading pair symbol to filter positions (e.g., BTCINR)  |

# RESPONSE

The response parameters are described below:

{
"id": 5454,
"contractPair": "GRTINR",
"contractType": "PERPETUAL",
"entryPrice":  12.541,
"leverage":  10,
"liquidationPrice": 11.4,
"marginType":  "ISOLATED",
"margin": 45.6,
"marginInMarginAsset": 45.6,
"positionAmount": 36,
"positionId":  "8b56348d-0d5d-4de1-85e1-3325bdf84087",
"positionSize": 451.48,
"positionStatus": "OPEN",
"positionType": "LONG",
"realizedProfit": null,
"quantity":  36,
"baseAsset": "GRT",
"marginAsset": "INR",
"quoteAsset":  "INR",
"createdTime": "2024-09-16T09:39:41.689Z",
"updatedTime": "2024-09-16T09:39:41.689Z"
}

# Parameter Descriptions

| Parameter           | Description                                                                    |
| ------------------- | ------------------------------------------------------------------------------ |
| id                  | Unique identifier for the position (5454).                                     |
| contractPair        | The trading pair for the contract (GRTINR), indicating GRT traded against INR. |
| contractType        | The type of contract (PERPETUAL), indicating a perpetual futures contract.     |
| entryPrice          | The price at which the position was entered (12.541 INR per GRT).              |
| leverage            | The leverage applied to the trade (10x).                                       |
| liquidationPrice    | The price at which the position would be liquidated (11.4 INR per GRT).        |
| marginType          | The type of margin used for the position (ISOLATED).                           |
| margin              | The amount of margin allocated to the position (45.6 INR).                     |
| marginInMarginAsset | The amount of margin in the margin asset (45.6 INR).                           |
| positionAmount      | The amount of the position (36 GRT).                                           |
| positionId          | Unique identifier for the position (8b56348d-0d5d-4de1-85e1-3325bdf84087).     |

https://lightningnodes.github.io/slate/?python#change-log
---
# Change Log – Pi42 API Reference Documentation

| Parameter      | Description                                                                        |
| -------------- | ---------------------------------------------------------------------------------- |
| positionSize   | The size of the position in terms of value ( 451.48 INR).                          |
| positionStatus | The current status of the position ( OPEN ).                                       |
| positionType   | The type of position ( LONG ).                                                     |
| realizedProfit | The profit realized from the position ( null , indicating no realized profit yet). |
| quantity       | The quantity of the asset involved ( 36 GRT).                                      |
| baseAsset      | The base asset being traded ( GRT ).                                               |
| marginAsset    | The asset used for margin ( INR ).                                                 |
| quoteAsset     | The currency used for the transaction ( INR ).                                     |
| createdTime    | The timestamp when the position was created ( 2024-09-16T09:39:41.689Z ).          |
| updatedTime    | The timestamp when the position was last updated ( 2024-09-16T09:39:41.689Z ).     |

# Get Position Status

GET /v1/positions/{positionStatus}

Retrieves details for a specific position identified by its unique position ID. It returns information related to the specified position, such as current status, asset details, and other relevant data.

def get_positions():
position_status = input("Enter position status (open, closed, liquidated): ").upper()
if position_status not in ["OPEN", "CLOSED", "LIQUIDATED"]:
print("Invalid position status. Please enter 'open', 'closed', or 'liquidated'.")
return
# Generate the current timestamp
timestamp = str(int(time.time() * 1000))
# Prepare the query parameters
params = {
'sortOrder': 'desc',
'pageSize': 100,
'timestamp': timestamp
}
# Convert the params into a query string to sign
query_string = f"sortOrder={params['sortOrder']}&pageSize={params['pageSize']}&timestamp={params['timestamp']}"
# Generate the signature
signature = generate_signature(api_secret, query_string)
# Headers for the GET request
headers = {
'api-key': api_key,
'signature': signature,
'accept': '*/*'
}

https://lightningnodes.github.io/slate/?python#change-log
---
# Change Log – Pi42 API Reference Documentation

# Construct the full URL including the path parameter for position status

full_url  = f"{base_url}/v1/positions/{position_status}?sortOrder={params['sortOrder']}&pageSize=
{params['pageSize']}&timestamp={params['timestamp']}"

try:

# Send the GET request to fetch positions

response  = requests.get(full_url,  headers=headers)
response.raise_for_status()  # Raises an error for 4xx/5xx responses
response_data = response.json()
print('Positions fetched successfully:', json.dumps(response_data, indent=4))

except requests.exceptions.HTTPError as  err:

print(f"Error:  {err.response.text  if err.response else err}")

except Exception  as e:

print(f"An unexpected error occurred:  {str(e)}")

| Parameter  | Type   | Required | Description                                        |
| ---------- | ------ | -------- | -------------------------------------------------- |
| positionId | string | Yes      | The unique identifier for the position to retrieve |

# RESPONSE

[
{
"contractPair": "BTCUSDT",
"entryPrice":  58003.7,
"leverage": 9,
"liquidationPrice":  52173.1,
"marginType":  "ISOLATED",
"marginAsset": "INR",
"margin": 19.404,
"marginInMarginAsset": 1688.15,
"positionAmount": 0.003,
"positionId":  "dd89732b-3a9d-4500-acec-64e1384c7149",
"positionSize": 174.0111,
"positionStatus": "OPEN",
"positionType": "LONG",
"realizedProfit": 0,
"quantity": 0.003,
"createdAt":  "2024-09-13T08:19:18.642Z",
"contractType": "PERPETUAL",
"iconUrl": "https://storage.googleapis.com/pi42-dev-static/contract-icons/btc.png",
"baseAsset":  "BTC",
"quoteAsset":  "USDT"
}
]

| Parameter           | Description                                                                                           |
| ------------------- | ----------------------------------------------------------------------------------------------------- |
| contractPair        | The trading pair for the contract ( BTCUSDT ), indicating Bitcoin (BTC) traded against USDT (Tether). |
| entryPrice          | The price at which the position was entered ( 58003.7 USDT ).                                         |
| leverage            | The leverage applied to the trade ( 9x ).                                                             |
| liquidationPrice    | The price at which the position would be liquidated ( 52173.1 USDT ).                                 |
| marginType          | The type of margin used for the position ( ISOLATED ).                                                |
| marginAsset         | The asset used for margin ( INR ).                                                                    |
| margin              | The amount of margin allocated to the position ( 19.404 INR ).                                        |
| marginInMarginAsset | The amount of margin in the margin asset ( 1688.15 INR).                                              |

https://lightningnodes.github.io/slate/?python#change-log
---
# Change Log – Pi42 API Reference Documentation

| Parameter      | Description                                                                                             |
| -------------- | ------------------------------------------------------------------------------------------------------- |
| positionAmount | The amount of the position (0.003 BTC).                                                                 |
| positionId     | Unique identifier for the position (dd89732b-3a9d-4500-acec-64e1384c7149).                              |
| positionSize   | The size of the position in terms of value (174.0111 USDT).                                             |
| positionStatus | The current status of the position (OPEN).                                                              |
| positionType   | The type of position (LONG).                                                                            |
| realizedProfit | The profit realized from the position (0, indicating no realized profit yet).                           |
| quantity       | The quantity of the asset involved (0.003 BTC).                                                         |
| createdAt      | The timestamp when the position was created (2024-09-13T08:19:18.642Z).                                 |
| contractType   | The type of contract (PERPETUAL), indicating a perpetual futures contract.                              |
| iconUrl        | The URL for the contract icon (https\://storage.googleapis.com/pi42-dev-static/contract-icons/btc.png). |
| baseAsset      | The base asset being traded (BTC).                                                                      |
| quoteAsset     | The currency used for the transaction (USDT).                                                           |

# Get User's Trade History

GET /v1/user-data/trade-history

Retrieves the trade history for a user. It supports optional filtering parameters such as timestamps, sorting order, page size, and trading symbol to help users access their historical trade data efficiently.

# Function to fetch trade history

def trade_history():
timestamp = str(int(time.time() * 1000))
trade_history_url = "https://fapi.pi42.com/v1/user-data/trade-history"
params = {
'sortOrder': 'desc',
'pageSize': 100,
'timestamp': timestamp
}
query_string = f"sortOrder={params['sortOrder']}&pageSize={params['pageSize']}&timestamp={params['timestamp']}"
signature = generate_signature(api_secret, query_string)
headers = {
'api-key': api_key,
'signature': signature,
'accept': '*/*'
}
try:
response = requests.get(f"{trade_history_url}?{query_string}", headers=headers)
response.raise_for_status()

https://lightningnodes.github.io/slate/?python#change-log
---
# Change Log – Pi42 API Reference Documentation

response_data = response.json()
print('Trade history fetched successfully:', json.dumps(response_data, indent=4))

# Parameters

| Parameter      | Type   | Required | Description                                                       |
| -------------- | ------ | -------- | ----------------------------------------------------------------- |
| startTimestamp | string | No       | The start timestamp (in milliseconds) for filtering trade history |
| endTimestamp   | string | No       | The end timestamp (in milliseconds) for filtering trade history   |
| sortOrder      | string | No       | The sorting order for the results (e.g., "asc" or "desc")         |
| pageSize       | string | No       | The number of results to return per page                          |
| symbol         | string | No       | The trading pair symbol to filter trade history (e.g., BTCINR)    |

# Response

The response parameters are as follows:

[
{
"id": 26260,
"time": "2024-09-16T09:39:41.675Z",
"symbol": "GRTINR",
"type": "LIMIT",
"side": "BUY",
"price": 12.541,
"quantity": 36,
"role": "MAKER",
"fee": 0,
"realizedProfit": 0,
"contractType": "PERPETUAL",
"clientOrderId":  "8acc0af94a3516126cdf-6238-ext",
"baseAsset": "GRT",
"quoteAsset": "INR",
"marginAsset": "INR"
}
]

# Response Parameters

| Parameter      | Description                                                                                            |
| -------------- | ------------------------------------------------------------------------------------------------------ |
| id             | Unique identifier for the order (26260).                                                               |
| time           | Timestamp when the order was placed (2024-09-16T09:39:41.675Z).                                        |
| symbol         | The trading pair for the order (GRTINR), indicating GRT (The Graph) traded against INR (Indian Rupee). |
| type           | The type of order (LIMIT), indicating a limit order.                                                   |
| side           | The side of the order (BUY).                                                                           |
| price          | The price at which the order is to be executed (12.541 INR).                                           |
| quantity       | The quantity of the order (36 GRT).                                                                    |
| role           | The role of the order in the trade (MAKER), indicating the order added liquidity to the market.        |
| fee            | The fee charged for the order (0, indicating no fee).                                                  |
| realizedProfit | The profit realized from the order (0, indicating no realized profit yet).                             |

https://lightningnodes.github.io/slate/?python#change-log
---
# Change Log – Pi42 API Reference Documentation

| Parameter     | Description                                                                              |
| ------------- | ---------------------------------------------------------------------------------------- |
| contractType  | The type of contract for the order (PERPETUAL), indicating a perpetual futures contract. |
| clientOrderId | Unique identifier for the client order (8acc0af94a3516126cdf-6238-ext).                  |
| baseAsset     | The base asset being traded (GRT).                                                       |
| quoteAsset    | The currency used for the transaction (INR).                                             |
| marginAsset   | The asset used for margin (INR).                                                         |

# Get User's Transaction History

# GET/v1/user-data/transaction-history

Retrieves the transaction history for a user, allowing filtering and sorting based on optional parameters. It provides detailed records of transactions within the specified time range and can be filtered by trading symbol, trade ID, and position ID.

def get_transaction_history():
# Default values for optional parameters
start_timestamp = None
end_timestamp  = None
sort_order    = 'desc'
page_size =    100
symbol  = None
trade_id   =  None
position_id    = None
# Generate the current timestamp (used as part of the authentication/signing process)
timestamp =    str(int(time.time() * 1000))
# Prepare query parameters with required and optional fields
params  =  {
'sortOrder':  sort_order,
'pageSize': page_size,
'timestamp':  timestamp
}
# Include optional parameters only if they are provided
if start_timestamp:
params['startTimestamp']  = start_timestamp
if end_timestamp:
params['endTimestamp'] =  end_timestamp
if symbol:
params['symbol'] = symbol
if trade_id:
params['tradeId'] = trade_id
if position_id:
params['positionId'] = position_id
# Convert the parameters to a query string to be signed
query_string    = '&'.join([f"{key}={value}" for key, value in params.items()])
# Generate the signature (assuming `generate_signature` is defined)
signature =    generate_signature(api_secret, query_string)
# Headers for the GET request
headers =  {
'api-key': api_key,
'signature': signature,
}

https://lightningnodes.github.io/slate/?python#change-log
---
# Change Log – Pi42 API Reference Documentation

'accept': '*/*'

# Construct the full URL with the query string
full_url = f"{base_url}/v1/user-data/transaction-history?{query_string}"

try:
# Send the GET request to fetch transaction history
response = requests.get(full_url, headers=headers)
response.raise_for_status()  # Raises an error for HTTP 4xx/5xx responses
response_data = response.json()
print('Transaction history fetched successfully:', json.dumps(response_data, indent=4))

except requests.exceptions.HTTPError as  err:
# Handle specific HTTP errors
print(f"HTTP Error: {err.response.text  if err.response else 'No response text'}")

except Exception as e:
# Handle any other exceptions
print(f"Failed {response.status_code}: {response.text}")

| Parameter      | Type   | Required | Description                                                             |
| -------------- | ------ | -------- | ----------------------------------------------------------------------- |
| startTimestamp | string | No       | The start timestamp (in milliseconds) for filtering transaction history |
| endTimestamp   | string | No       | The end timestamp (in milliseconds) for filtering transaction history   |
| sortOrder      | string | No       | The sorting order for the results (e.g., "asc" or "desc")               |
| pageSize       | string | No       | The number of records to return per page                                |
| symbol         | string | No       | The trading symbol to filter the transaction history (e.g., BTCINR)     |
| tradeId        | number | No       | The specific trade ID to filter the transaction history                 |
| positionId     | string | No       | The specific position ID to filter the transaction history              |

# RESPONSE

[
{
"id": 109884,
"time": "2024-09-16T09:39:28.754Z",
"type": "COMMISSION",
"amount": -2.1,
"asset": "INR",
"symbol": "BTCINR",
"contractType": "PERPETUAL",
"baseAsset": "BTC",
"quoteAsset": "INR"
}
]

| Parameter | Description                                                            |
| --------- | ---------------------------------------------------------------------- |
| id        | Unique identifier for the transaction (109884).                        |
| time      | Timestamp when the transaction occurred (2024-09-16T09:39:28.754Z).    |
| type      | The type of the transaction (COMMISSION), indicating a commission fee. |
| amount    | The amount of the commission fee (-2.1 INR).                           |
| asset     | The asset for the commission fee (INR).                                |

https://lightningnodes.github.io/slate/?python#change-log
---
# Change Log – Pi42 API Reference Documentation

| Parameter    | Description                                                                                                            |
| ------------ | ---------------------------------------------------------------------------------------------------------------------- |
| symbol       | The trading pair associated with the transaction (BTCINR), indicating Bitcoin (BTC) traded against Indian Rupee (INR). |
| contractType | The type of contract for the transaction (PERPETUAL), indicating a perpetual futures contract.                         |
| baseAsset    | The base asset in the trading pair (BTC).                                                                              |
| quoteAsset   | The currency used for the transaction (INR).                                                                           |

# Update Preference

POST /v1/exchange/update/preference

Updates the leverage and margin-mode (Cross or Isolated) for a specified contract. It allows setting the leverage level and margin-mode for trading a particular asset or trading pair.

# Notes:

1. Update Leverage and Margin Mode for Specific Symbols
Users can adjust the leverage and margin mode for individual symbols using the /update/preference endpoint. This adjustment applies only to the specified symbol.
2. Placing Orders
Orders will be executed with the leverage and margin mode that was previously set for the symbol. To use a different leverage or margin mode for an order, users must first update the leverage or margin mode for the symbol via the /update/preference endpoint.

import time
import json
import requests

def update_preference():
endpoint  =  "/v1/exchange/update/preference"
leverage  =  10  # Ensure leverage is an integer
contract_name = "BTCINR"  # Replace with the appropriate contract name
margin_mode   = "CROSS"  # Ensure marginMode is either 'ISOLATED' or 'CROSS'
# Generate the current timestamp
timestamp =   str(int(time.time() *  1000))
# Prepare the request body (JSON)
params =  {
'leverage': leverage,
'marginMode': margin_mode,
'contractName': contract_name,
'timestamp':  timestamp
}
# Convert the request body to a JSON string for signing
data_to_sign  = json.dumps(params,   separators=(',', ':'))
# Generate the signature (ensure `generate_signature` is properly defined)
signature =   generate_signature(api_secret, data_to_sign)
# Headers for the POST request
---
# Change Log – Pi42 API Reference Documentation

headers = {
'api-key': api_key,
'Content-Type': 'application/json',
'signature':  signature
}
# Construct the full URL
update_preference_url = f"{base_url}{endpoint}"
try:
# Send the POST request to update the preference
response = requests.post(update_preference_url,  json=params, headers=headers)
response.raise_for_status()  # Raises an error for 4xx/5xx responses
response_data = response.json()
print('Preference updated successfully:', json.dumps(response_data, indent=4))
except requests.exceptions.HTTPError as  err:
print(f"Error: {err.response.text if  err.response else err}")
except Exception  as e:
print(f"An unexpected error occurred: {str(e)}")

| Parameter    | Type   | Required | Description                                                                    |
| ------------ | ------ | -------- | ------------------------------------------------------------------------------ |
| leverage     | number | Yes      | The leverage level to set for the contract (e.g., 10). Must be an integer.     |
| marginMode   | string | Yes      | Margin mode to set for the contract (CROSS/ISOLATED). Must be a string         |
| contractName | string | Yes      | The trading pair or contract name to which the leverage applies (e.g., BTCINR) |

# RESPONSE

The response parameters are described below:
//  Response
{
"contractName": "ETHINR",
"marginMode": "CROSS",
"updatedLeverage":  10
}

| Parameter       | Description                                                                                       |
| --------------- | ------------------------------------------------------------------------------------------------- |
| contractName    | The name of the contract ( ETHINR ), indicating Ethereum (ETH) traded against Indian Rupee (INR). |
| marginMode      | Updated margin mode for ( ETHINR ) is (CROSS)                                                     |
| updatedLeverage | The updated leverage for the contract ( 10 ).                                                     |

# Update Leverage

POST /v1/exchange/update/leverage

Updates the leverage for a specified contract. It allows setting the leverage level for trading a particular asset or trading pair.

This endpoint is used to adjust the leverage settings for risk management and trading strategies.

# Notes:

1. Update Leverage for Specific Symbols
Users can adjust the leverage for individual symbols using the /update/leverage endpoint.

https://lightningnodes.github.io/slate/?python#change-log
---
# Change Log – Pi42 API Reference Documentation

This adjustment applies only to the specified symbol.

# 2. Placing Orders

Orders will be executed with the leverage that was previously set for the symbol. To use a different leverage for an order, users must first update the leverage for the symbol via the /update/leverage endpoint.

def update_leverage():
leverage  = int(input("Enter the leverage value: "))
contract_name = input("Enter the contract name: ")
# Generate the current timestamp
timestamp  = str(int(time.time() * 1000))
# Prepare the request body (JSON)
params =  {
'leverage': int(leverage),
'contractName':   contract_name,
'timestamp': timestamp
}
# Convert the request body to a JSON string for signing
data_to_sign  = json.dumps(params, separators=(',', ':'))
# Generate the signature
signature  = generate_signature(api_secret, data_to_sign)
# Headers for the POST request
headers =  {
'api-key': api_key,
'Content-Type':   'application/json',
'signature': signature
}
# Construct the full URL
update_leverage_url   = f"{base_url}/v1/exchange/update/leverage"
try:
# Send the POST request to update the leverage
response  = requests.post(update_leverage_url, json=params, headers=headers)
response.raise_for_status()  # Raises an error for 4xx/5xx responses
response_data =   response.json()
print('Leverage updated successfully:',  json.dumps(response_data, indent=4))
except  requests.exceptions.HTTPError as err:
print(f"Error:  {err.response.text if err.response else err}")
except  Exception as  e:
print(f"An unexpected error occurred:  {str(e)}")

| Parameter    | Type   | Required | Description                                                                    |
| ------------ | ------ | -------- | ------------------------------------------------------------------------------ |
| leverage     | number | Yes      | The leverage level to set for the contract (e.g., 10). Must be an integer.     |
| contractName | string | Yes      | The trading pair or contract name to which the leverage applies (e.g., BTCINR) |

# RESPONSE

The response parameters are described below:

{
"updatedLeverage":  10,
"contractName": "ETHINR"
}

https://lightningnodes.github.io/slate/?python#change-log
---
# Change Log – Pi42 API Reference Documentation

| Parameter       | Description                                                                                     |
| --------------- | ----------------------------------------------------------------------------------------------- |
| updatedLeverage | The updated leverage for the contract (10).                                                     |
| contractName    | The name of the contract (ETHINR), indicating Ethereum (ETH) traded against Indian Rupee (INR). |

# Deleting an Order

# DELETE /v1/order/delete-order

Deletes a specific order based on its client order ID. It requires the client order ID (clientOrderID) to identify the order to be deleted and a timestamp for request validation.

def delete_order():
client_order_id = input("Enter the clientOrderId to delete: ")
delete_order_url  = "https://fapi.pi42.com/v1/order/delete-order"
timestamp =  str(int(time.time() *  1000))
params = {
'clientOrderId': client_order_id,
'timestamp':  timestamp
}
data_to_sign  = json.dumps(params,  separators=(',', ':'))
signature =  generate_signature(api_secret, data_to_sign)
headers = {
'api-key': api_key,
'Content-Type': 'application/json',
'signature':  signature,
}
try:
response  = requests.delete(delete_order_url, json=params, headers=headers)
response.raise_for_status()
print(f"Order with clientOrderId {client_order_id} deleted successfully.")
except requests.exceptions.HTTPError as err:
print(f"Failed {response.status_code}: {response.text}")

| Parameter     | Type   | Required | Description                                                                             |
| ------------- | ------ | -------- | --------------------------------------------------------------------------------------- |
| clientOrderId | string | Yes      | The unique identifier for the order to be deleted (e.g., a9c5ba9893c99828e4b5-6238-ext) |
| timestamp     | string | Yes      | The current timestamp (in milliseconds) for request validation                          |

Requires clientOrderId that can be retrieved from Get Open Orders API.

# RESPONSE

{
"clientOrderId": "93513fe2a8af44157234-6238-ext",
"orderId": 24717,
"status": "CANCELED",
"success": true
}

https://lightningnodes.github.io/slate/?python#change-log
---
# Change Log – Pi42 API Reference Documentation

| Parameter     | Description                                                             |
| ------------- | ----------------------------------------------------------------------- |
| clientOrderId | Unique identifier for the client order (93513fe2a8af44157234-6238-ext). |
| orderId       | Unique identifier for the order (24717).                                |
| status        | The status of the order (CANCELED).                                     |
| success       | Indicates whether the operation was successful (true).                  |

# Cancel all the orders

# DELETE /v1/order/cancel-all-orders

Deletes all the open orders.

import time
import json
import requests

def cancel_all_orders():
endpoint  = "/v1/order/cancel-all-orders"
# Generate the current timestamp
timestamp =  str(int(time.time() *  1000))
# Prepare the request payload
params =  {
'timestamp':  timestamp
}
# Convert the request body to a JSON string for signing
data_to_sign = json.dumps(params,   separators=(',', ':'))
# Generate the signature (ensure `generate_signature` is properly defined)
signature =  generate_signature(api_secret, data_to_sign)
# Headers for the DELETE request
headers = {
'api-key': api_key,
'Content-Type': 'application/json',
'signature':  signature
}
# Construct the full URL
cancel_orders_url  =  f"{base_url}{endpoint}"
try:
# Send the DELETE request to cancel all orders
response  = requests.delete(cancel_orders_url, json=params, headers=headers)
response.raise_for_status()  # Raises an error for 4xx/5xx responses
response_data  = response.json()
print('All orders canceled successfully:',  json.dumps(response_data, indent=4))
except requests.exceptions.HTTPError as  err:
print(f"Failed {response.status_code}: {response.text}")
except Exception  as  e:
print(f"An unexpected error occurred: {str(e)}")

| Parameter | Type   | Required | Description                                                    |
| --------- | ------ | -------- | -------------------------------------------------------------- |
| timestamp | string | Yes      | The current timestamp (in milliseconds) for request validation |

https://lightningnodes.github.io/slate/?python#change-log
---
# Change Log – Pi42 API Reference Documentation

# RESPONSE

{
"success": true,
"data": [
{
"clientOrderId": "02f8c7b42c904b5475b6-6238-ext",
"status": "CANCELED",
"message": "Order is cancelled"
},
]
}

| Parameter     | Description                                                               |
| ------------- | ------------------------------------------------------------------------- |
| clientOrderId | Unique identifier for the client order ( 93513fe2a8af44157234-6238-ext ). |
| status        | The status of the order ( CANCELED ).                                     |
| message       | Order is cancelled.                                                       |

# Close all the positions

DELETE /v1/positions/close-all-positions
Closes all the Positions.

import time
import json
import requests

def close_all_positions():
endpoint  = "/v1/positions/close-all-positions"
# Generate the current timestamp
timestamp =  str(int(time.time() *  1000))
# Prepare the request payload
params =  {
'timestamp':  timestamp
}
# Convert the request body to a JSON string for signing
data_to_sign = json.dumps(params,   separators=(',', ':'))
# Generate the signature (ensure `generate_signature` is properly defined)
signature =  generate_signature(api_secret, data_to_sign)
# Headers for the DELETE request
headers = {
'api-key': api_key,
'Content-Type': 'application/json',
'signature':  signature
}
# Construct the full URL
cancel_orders_url  = f"{base_url}{endpoint}"
try:
# Send the DELETE request to cancel all orders
response = requests.delete(cancel_orders_url, json=params, headers=headers)
response.raise_for_status()  # Raises an error for 4xx/5xx responses
response_data  = response.json()

https://lightningnodes.github.io/slate/?python#change-log
---
# Change Log – Pi42 API Reference Documentation

print('All orders canceled successfully:',  json.dumps(response_data, indent=4))

except requests.exceptions.HTTPError as  err:
print(f"Failed {response.status_code}: {response.text}")
except Exception as e:
print(f"An unexpected error occurred: {str(e)}")

| Parameter | Type   | Required | Description                                                    |
| --------- | ------ | -------- | -------------------------------------------------------------- |
| timestamp | string | Yes      | The current timestamp (in milliseconds) for request validation |

# RESPONSE

{
"success": true,
"data": [
{
"positionId": "2d29687c-2aab-4378-ada3-f18ecb73b332",
"status": "CLOSED",
"message": "Position is closed."
}
]
}

| Parameter  | Description                                                                |
| ---------- | -------------------------------------------------------------------------- |
| positionId | Unique identifier for the position (2d29687c-2aab-4378-ada3-f18ecb73b332). |
| status     | The status of the order (CLOSED).                                          |
| message    | Position is closed.                                                        |

# Get futures wallet details

GET /v1/wallet/futures-wallet/details
Get all details of Futures wallet.

import requests
import hmac
import hashlib
import time
import json
def generate_signature(api_secret, data_to_sign):
return  hmac.new(api_secret.encode('utf-8'), data_to_sign.encode('utf-8'), hashlib.sha256).hexdigest()
def get_futures_wallet_details():
endpoint   = "/v1/wallet/futures-wallet/details"
# Generate the current timestamp
timestamp  = str(int(time.time() * 1000))
# Optional parameters with timestamp
params  =  {
'marginAsset': 'INR',
'timestamp': timestamp
}
query_string = f"marginAsset={params['marginAsset']}&timestamp={params['timestamp']}"
# Generate the signature (ensure `generate_signature` is properly defined)

https://lightningnodes.github.io/slate/?python#change-log
---
# Change Log – Pi42 API Reference Documentation

signature  = generate_signature(api_secret, query_string)
# Headers for the GET request
headers =  {
'api-key': api_key,
'signature': signature
}
# Construct the full URL
wallet_details_url  = f"{base_url}{endpoint}?{query_string}"
try:
# Send the GET request to fetch the futures wallet details
response  = requests.get(wallet_details_url, headers=headers)
response.raise_for_status()   # Raises an error for 4xx/5xx responses
response_data =   response.json()
print('Futures wallet details:',   json.dumps(response_data, indent=4))
except  requests.exceptions.HTTPError  as err:
print(f"Failed  {response.status_code}: {response.text}")
except  Exception as  e:
print(f"An unexpected error occurred:  {str(e)}")

| Parameter   | Type   | Required | Description                                                    |
| ----------- | ------ | -------- | -------------------------------------------------------------- |
| timestamp   | string | Yes      | The current timestamp (in milliseconds) for request validation |
| marginAsset | string | No       | MarginAsset of Futures wallet (INR).                           |

# RESPONSE

//  Response
{
"inrBalance": "1941.50",
"walletBalance": "1941.50",
"withdrawableBalance": "1468.50",
"maintenanceMargin": "0.00",
"unrealisedPnlCross": "0.00",
"unrealisedPnlIsolated":  "0.00",
"maxWithdrawableBalance":  "1468.50",
"lockedBalance": "473.00",
"marginBalance": "1468.52",
"pnlPercentCross":  "0.00",
"pnlPercentIsolated": "0.00",
"lockedBalanceCross": "0.00",
"lockedBalanceIsolated":  "473.00",
"marginAsset": "INR"
}

| Parameter              | Description                                                                         |
| ---------------------- | ----------------------------------------------------------------------------------- |
| inrBalance             | INR balance of Futures wallet (INR).                                                |
| walletBalance          | Total wallet balance in INR.                                                        |
| withdrawableBalance    | Amount of INR that can be withdrawn from the wallet.                                |
| maintenanceMargin      | Amount of INR locked as maintenance margin.                                         |
| unrealisedPnlCross     | Unrealized profit and loss (PnL) in cross margin mode in INR.                       |
| unrealisedPnlIsolated  | Unrealized profit and loss (PnL) in isolated margin mode in INR.                    |
| maxWithdrawableBalance | Maximum amount of INR that can be withdrawn, factoring in margins and locked funds. |
| lockedBalance          | Total locked balance in INR, which cannot be withdrawn or used.                     |

https://lightningnodes.github.io/slate/?python#change-log
---
# Change Log – Pi42 API Reference Documentation

| Parameter             | Description                                                |
| --------------------- | ---------------------------------------------------------- |
| marginBalance         | Total margin balance in INR, including any unrealized PnL. |
| pnlPercentCross       | Percentage of unrealized PnL in cross margin mode.         |
| pnlPercentIsolated    | Percentage of unrealized PnL in isolated margin mode.      |
| lockedBalanceCross    | Amount of INR locked in cross margin mode.                 |
| lockedBalanceIsolated | Amount of INR locked in isolated margin mode.              |
| marginAsset           | Asset type used for margin, in this case, INR.             |

# Get funding wallet details

# GET /v1/wallet/funding-wallet/details

Get details of funding wallet.

import requests
import hmac
import hashlib
import time
import json

def generate_signature(api_secret, data_to_sign):
return hmac.new(api_secret.encode('utf-8'), data_to_sign.encode('utf-8'), hashlib.sha256).hexdigest()

def get_futures_wallet_details():
endpoint = "/v1/wallet/funding-wallet/details"
# Generate the current timestamp
timestamp = str(int(time.time() * 1000))
# Optional parameters with timestamp
params = {
'marginAsset': 'INR',
'timestamp': timestamp
}
query_string = f"marginAsset={params['marginAsset']}&timestamp={params['timestamp']}"
# Generate the signature (ensure `generate_signature` is properly defined)
signature = generate_signature(api_secret, query_string)
# Headers for the GET request
headers = {
'api-key': api_key,
'signature': signature
}
# Construct the full URL
wallet_details_url = f"{base_url}{endpoint}?{query_string}"
try:
# Send the GET request to fetch the futures wallet details
response = requests.get(wallet_details_url, headers=headers)
response.raise_for_status()  # Raises an error for 4xx/5xx responses
response_data = response.json()
print('Funding wallet details:', json.dumps(response_data, indent=4))
except requests.exceptions.HTTPError as err:
print(f"Failed {response.status_code}: {response.text}")

https://lightningnodes.github.io/slate/?python#change-log
---
# Change Log – Pi42 API Reference Documentation

except Exception as e:
print(f"An unexpected error occurred: {str(e)}")

| Parameter   | Type   | Required | Description                                                    |
| ----------- | ------ | -------- | -------------------------------------------------------------- |
| timestamp   | string | Yes      | The current timestamp (in milliseconds) for request validation |
| marginAsset | string | No       | MarginAsset of Futures wallet ( INR ).                         |

# RESPONSE

// Response
{
"inrBalance": "601.00",
"walletBalance": "601.00",
"withdrawableBalance": "601.00",
"lockedBalance": "0.00",
"marginAsset": "INR"
}

| Parameter           | Description                                                     |
| ------------------- | --------------------------------------------------------------- |
| inrBalance          | INR balance of Futures wallet ( INR ).                          |
| walletBalance       | Total wallet balance in INR.                                    |
| withdrawableBalance | Amount of INR that can be withdrawn from the wallet.            |
| lockedBalance       | Total locked balance in INR, which cannot be withdrawn or used. |
| marginAsset         | Asset type used for margin, in this case, INR.                  |

# Public Endpoints

Public endpoints in Pi42 are designed to facilitate easy access to various functionalities of the Pi42 platform, particularly for integration with external systems and applications. Below is an overview of the public endpoints available in Pi42, their typical uses, and example API calls.

# Ticker Update (24Hr)

GET /v1/market/ticker24Hr

Fetches the 24-hour market ticker data for a specific trading pair. It provides details such as the last traded price, volume, and other market metrics over the past 24 hours.

import requests
import json
def get_24hr_ticker_update():
# Get the contract pair input from the user
contract_pair = input("Enter the contract pair (e.g., btc, eth): ").lower()
# Validate the input
---
# Change Log – Pi42 API Reference Documentation

if not contract_pair:
print("Invalid contract pair. Please enter a valid contract pair (e.g., btc, eth).")
return
# Construct the full URL for the API request using the provided contract pair
full_url = f"https://api.pi42.com/v1/market/ticker24Hr/{contract_pair}"
try:
# Send the GET request to the API
response = requests.get(full_url)
response.raise_for_status()  # Raise an error for HTTP 4xx/5xx responses
# Parse the JSON response data
response_data = response.json()
# Print the 24-hour ticker update in a formatted manner
print('24-hour ticker update fetched successfully:', json.dumps(response_data,  indent=4))
except requests.exceptions.HTTPError as  err:
# Handle HTTP errors specifically
print(f"Error: {err.response.text if  err.response else err}")
except Exception as e:
# Handle any other unexpected errors
print(f"An unexpected error occurred: {str(e)}")

# Parameter

| contractPair | string | Yes | The trading pair for which to fetch the ticker data (e.g., BTCINR) |
| ------------ | ------ | --- | ------------------------------------------------------------------ |

# RESPONSE

# The response parameters are as follows:

//  Response
{
"data": {
"e":  "24hrTicker",
"E":  1726313209122,
"s":  "BTCINR",
"p":  "139470.66",
"P":  "2.718",
"w":  "5230573.12",
"c":  "5271387.66",
"Q":  "0.081",
"o":  "5131917",
"h":  "5344655.41",
"l":  "5079790.8",
"v":  "274282.584",
"q":  "16265932028.08",
"O":  1726226760000,
"C":  1726313209120,
"F":  5380307688,
"L":  5383597456,
"n":  3289757
}
}

# Parameter

| e | The event type ( 24hrTicker ), indicating a 24-hour ticker event.                               |
| - | ----------------------------------------------------------------------------------------------- |
| E | The event time in milliseconds since epoch ( 1726313209122 ).                                   |
| s | The trading pair symbol ( BTCINR ), indicating Bitcoin (BTC) traded against Indian Rupee (INR). |
| p | The price change in the last 24 hours ( 139470.66 INR ).                                        |

41/57
---
# Change Log – Pi42 API Reference Documentation

| Parameter | Description                                                                       |
| --------- | --------------------------------------------------------------------------------- |
| P         | The percentage price change in the last 24 hours (2.718%).                        |
| w         | The weighted average price in the last 24 hours (5230573.12 INR).                 |
| c         | The last price (5271387.66 INR).                                                  |
| Q         | The last quantity traded (0.081 BTC).                                             |
| o         | The open price of the 24-hour period (5131917 INR).                               |
| h         | The highest price in the last 24 hours (5344655.41 INR).                          |
| l         | The lowest price in the last 24 hours (5079790.8 INR).                            |
| v         | The total traded volume in the last 24 hours (274282.584 BTC).                    |
| q         | The total traded quote asset volume in the last 24 hours (16265932028.08 INR).    |
| O         | The start time of the 24-hour period in milliseconds since epoch (1726226760000). |
| C         | The end time of the 24-hour period in milliseconds since epoch (1726313209120).   |
| F         | The first trade ID in the 24-hour period (5380307688).                            |
| L         | The last trade ID in the 24-hour period (5383597456).                             |
| n         | The number of trades in the 24-hour period (3289757).                             |

# Aggregate Trade Update

# GET /v1/market/aggTrade

Retrieves aggregated trade data for a specific trading pair. Aggregated trades provide summarized information about trade activities, such as total volume and price changes, for the given trading pair.

import requests
import json

def get_trade_updates():
# Prompt the user to enter a contract pair
contract_pair = input("Enter the contract pair (e.g., btc, eth): ").lower()
# Validate the user input
if not contract_pair:
print("Invalid contract pair. Please enter a valid contract pair (e.g., btc, eth).")
return
# Construct the URL for the API request using the provided contract pair
full_url = f"https://api.pi42.com/v1/market/aggTrade/{contract_pair}"
try:
# Send the GET request to fetch trade updates
response = requests.get(full_url)
response.raise_for_status() # Raise an exception for HTTP error responses

https://lightningnodes.github.io/slate/?python#change-log
---
# Change Log – Pi42 API Reference Documentation

# Parse the JSON response data
response_data = response.json()
# Print the trade updates in a formatted manner
print('Trade updates fetched successfully:', json.dumps(response_data, indent=4))

except requests.exceptions.HTTPError as err:
# Handle HTTP errors specifically
print(f"Error: {err.response.text if  err.response else err}")
except Exception as e:
# Handle any other unexpected errors
print(f"An unexpected error occurred: {str(e)}")

| Parameter    | Type   | Required | Description                                                              |
| ------------ | ------ | -------- | ------------------------------------------------------------------------ |
| contractPair | string | Yes      | The trading pair for which to fetch aggregated trade data (e.g., BTCINR) |

# RESPONSE

The response body parameters are described as follows:

// Response
{
"data": [
{
"e": "aggTrade",
"E": 1726313202969,
"a": 2329235556,
"s": "BTCINR",
"p": "5271343.57",
"q": "0.002",
"f": 5383597285,
"l": 5383597285,
"T": 1726313202966,
"m": true
}
]
}

| Parameter | Description                                                                                   |
| --------- | --------------------------------------------------------------------------------------------- |
| e         | The event type (aggTrade), indicating an aggregated trade event.                              |
| E         | The event time in milliseconds since epoch (1726313202969).                                   |
| a         | The aggregate trade ID (2329235556).                                                          |
| s         | The trading pair symbol (BTCINR), indicating Bitcoin (BTC) traded against Indian Rupee (INR). |
| p         | The price of the trade (5271343.57 INR).                                                      |
| q         | The quantity of the trade (0.002 BTC).                                                        |
| f         | The first trade ID in the aggregate trade (5383597285).                                       |
| l         | The last trade ID in the aggregate trade (5383597285).                                        |
| T         | The trade time in milliseconds since epoch (1726313202966).                                   |
| m         | Whether the buyer is the market maker (true).                                                 |

https://lightningnodes.github.io/slate/?python#change-log
---
# Change Log – Pi42 API Reference Documentation

# Depth Update

# GET /v1/market/depth/

Fetches the order book depth data for a specific trading pair. It provides information about the current market depth, including bid and ask prices and their respective volumes, which is essential for understanding market liquidity.

def get_depth_update():
# Prompt the user to enter a contract pair
contract_pair = input("Enter the contract pair (e.g., btc, eth): ").lower()
# Validate the user input
if not contract_pair:
print("Invalid contract pair. Please enter a valid contract pair (e.g., btc, eth).")
return
# Construct the URL for the API request using the provided contract pair
full_url =  f"https://api.pi42.com/v1/market/depth/{contract_pair}"
try:
# Send the GET request to fetch depth updates
response = requests.get(full_url)
response.raise_for_status()   # Raises an error for 4xx/5xx responses
# Parse the JSON response data
response_data  = response.json()
# Print the depth update in a formatted manner
print('Depth update fetched successfully:',  json.dumps(response_data, indent=4))
except requests.exceptions.HTTPError  as err:
# Handle HTTP errors specifically
print(f"Error: {err.response.text  if  err.response else err}")
except Exception  as e:
# Handle any other unexpected errors
print(f"An unexpected error occurred: {str(e)}")

| Parameter    | Type   | Required | Description                                                                  |
| ------------ | ------ | -------- | ---------------------------------------------------------------------------- |
| contractPair | string | Yes      | The trading pair for which to fetch the order book depth data (e.g., BTCINR) |

# RESPONSE

The parameters contained in the response body are as follows:

{
"data":  {
"e":  "depthUpdate",
"E":  1726313210012,
"T":  1726313210009,
"s":  "BTCINR",
"U":  5339856484581,
"u":  5339856497601,
"pu":  5339856483867,
"b":  [
[
"5271043.69",
"0.554"
]
],
"a":  [
[
"5271396.49",
""
]
]
}
---
# Change Log – Pi42 API Reference Documentation

| Parameter | Description                                                                                                                                                                  |
| --------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| e         | The event type (depthUpdate), indicating a market depth update.                                                                                                              |
| E         | The event time in milliseconds since epoch (1726313210012).                                                                                                                  |
| T         | The transaction time in milliseconds since epoch (1726313210009).                                                                                                            |
| s         | The trading pair symbol (BTCINR), indicating Bitcoin (BTC) traded against Indian Rupee (INR).                                                                                |
| U         | The first update ID in the update (5339856484581).                                                                                                                           |
| u         | The last update ID in the update (5339856497601).                                                                                                                            |
| pu        | The previous update ID (5339856483867).                                                                                                                                      |
| b         | Current bid prices and quantities. Each entry is an array where the first element is the price and the second element is the quantity. Example: \[\["5271043.69", "0.554"]]. |
| a         | Current ask prices and quantities. Each entry is an array where the first element is the price and the second element is the quantity. Example: \[\["5271396.49", "0.866"]]. |

# Get Klines

# POST /v1/market/klines

Retrieves candlestick (kline) data for a specified trading pair and time interval. It provides historical price data that can be used for charting and analysis, including start and end times, and limits on the number of records returned.

def get_kline_data():
try:
# User inputs
pair = input("Enter the trading pair (e.g., BTCINR): ").upper()
interval  = input("Enter the interval (e.g., 1m, 5m, 1h): ").lower()
# Prepare the request body (JSON)
params =  {
'pair': pair,
'interval': interval,
'limit': 1000
}
# Headers for the POST request (no API key or signature required)
headers =  {
'Content-Type': 'application/json'
}
# Construct the full URL for the Kline endpoint
kline_url  = "https://api.pi42.com/v1/market/klines"
# Send the POST request to get Kline data
response  = requests.post(kline_url, json=params, headers=headers)
response.raise_for_status() # Raises an error for 4xx/5xx responses

https://lightningnodes.github.io/slate/?python#change-log
---
# Change Log – Pi42 API Reference Documentation

response_data = response.json()
print('Kline data fetched successfully:', json.dumps(response_data, indent=4))

except  ValueError:

print("Please enter valid inputs for pair, interval.")

except  requests.exceptions.HTTPError as err:

print(f"Error: {err.response.text if err.response else err}")

except  Exception as e:

print(f"An unexpected error occurred: {str(e)}")

| Parameter | Type   | Required | Description                                                               |
| --------- | ------ | -------- | ------------------------------------------------------------------------- |
| pair      | string | Yes      | The trading pair for which to fetch kline data (e.g., BTCINR)             |
| interval  | string | Yes      | The interval for each kline (e.g., "1m" for 1 minute, "5m" for 5 minutes) |
| startTime | number | No       | The start time (in milliseconds) for the kline data (timestamp)           |
| endTime   | number | No       | The end time (in milliseconds) for the kline data (timestamp)             |
| limit     | number | No       | The maximum number of kline records to return                             |

# RESPONSE

The response parameters are described below:

[
{
"startTime": "1726312200000",
"open": "5270382.19",
"high": "5270408.64",
"low": "5270382.19",
"close": "5270382.19",
"endTime": "1726312259999",
"volume": "59.102"
},
]

| Parameter | Description                                                                 |
| --------- | --------------------------------------------------------------------------- |
| startTime | The start time of the interval in milliseconds since epoch (1726312200000). |
| open      | The opening price of the interval (5270382.19 INR).                         |
| high      | The highest price during the interval (5270408.64 INR).                     |
| low       | The lowest price during the interval (5270382.19 INR).                      |
| close     | The closing price of the interval (5270382.19 INR).                         |
| endTime   | The end time of the interval in milliseconds since epoch (1726312259999).   |
| volume    | The trading volume during the interval (59.102 BTC).                        |

# Exchange

GET /v1/exchange/exchangeInfo

Retrieve exchange information

https://lightningnodes.github.io/slate/?python#change-log
---
# Change Log – Pi42 API Reference Documentation

def get_exchange_info():
# Construct the URL
full_url = f"{base_url}/v1/exchange/exchangeInfo"
try:
# Send the GET request to fetch exchange information
response = requests.get(full_url)
response.raise_for_status()  # Raises an error for 4xx/5xx responses
response_data = response.json()
print('Exchange information fetched successfully:', json.dumps(response_data, indent=4))
except requests.exceptions.HTTPError as err:
print(f"Error: {err.response.text if err.response else err}")
except Exception as e:
print(f"An unexpected error occurred: {str(e)}")

# Parameter

| market | string | No | Will return exchangeInfo for market (e.g., INR/USDT) |
| ------ | ------ | -- | ---------------------------------------------------- |

# RESPONSE

The response parameters are described below:

| Parameter    | Description                                                                                              |
| ------------ | -------------------------------------------------------------------------------------------------------- |
| market       | A list of markets included in the response.                                                              |
| contracts    | An array of contract objects that contain detailed information about specific trading contracts.         |
| name         | The name of the trading pair (e.g., "BTCINR" for Bitcoin to INR)                                         |
| contractName | The full name of the contract (e.g., "Bitcoin").                                                         |
| filters      | A list of filters that apply to the contract, detailing quantity and order constraints                   |
| maxQty       | The maximum quantity allowed                                                                             |
| minQty       | The minimum quantity allowed                                                                             |
| filterType   | The type of filter (e.g., "MARKET\_QTY\_SIZE", "LIMIT\_QTY\_SIZE", "MAX\_NUM\_ORDERS", "MIN\_NOTIONAL"). |
| limit        | The maximum number of orders allowed.                                                                    |
| notional     | The minimum notional value.                                                                              |
| makerFee     | The fee percentage for makers.                                                                           |
| takerFee     | The fee percentage for takers.                                                                           |
| baseAsset    | The base asset for the contract (e.g., "BTC").                                                           |
| orderTypes   | The types of orders supported (e.g., "LIMIT", "MARKET").                                                 |
| quoteAsset   | The quote asset for the contract (e.g., "INR").                                                          |
| maxLeverage  | The maximum leverage allowed (e.g., "20").                                                               |
| contractType | The type of contract (e.g., "PERPETUAL").                                                                |

https://lightningnodes.github.io/slate/?python#change-log
---
# Change Log – Pi42 API Reference Documentation

| Parameter                       | Description                                                                                |
| ------------------------------- | ------------------------------------------------------------------------------------------ |
| marginBuffer                    | The margin buffer value.                                                                   |
| depthGrouping                   | The grouping for order book depth (e.g., \["0.1"]).                                        |
| liquidationFee                  | The fee percentage for liquidation (e.g., "0.020000").                                     |
| pricePrecision                  | The number of decimal places for prices.                                                   |
| isDefaultContract               | A boolean indicating if this is the default contract (e.g., true).                         |
| quantityPrecision               | The number of decimal places for quantities.                                               |
| limitPriceVarAllowed            | The allowed price variation for limit orders (e.g., "0.2").                                |
| marginBufferPercentage          | The percentage for margin buffer (e.g., "1").                                              |
| maintenanceMarginPercentage     | The percentage for maintenance margin (e.g., "1").                                         |
| iconUrl                         | The URL for the contract's icon (e.g., "string").                                          |
| reduceMarginAllowedRatioPercent | The allowed ratio percentage for reducing margin (e.g., 0.2).                              |
| market                          | The market identifier                                                                      |
| marginAssetsSupported           | A list of supported margin assets (e.g., \["INR"]).                                        |
| fundingFeeInterval              | The interval for funding fees (e.g., 8).                                                   |
| tags                            | A list of tags associated with the market or contracts (e.g., \["MEME", "DECENTRALIZED"]). |
| assetPrecisions                 | An object that specifies the precision for assets.                                         |
| INR                             | The precision for INR (e.g., 2 decimal places).                                            |
| USDT                            | The precision for USDT (e.g., 4 decimal places).                                           |
| conversionRates                 | An object that specifies conversion rates for margin and settlement.                       |
| INR\_MARGIN\_USDT               | The conversion rate for INR margin to USDT (e.g., 88).                                     |
| INR\_MARGIN\_INR                | The conversion rate for INR margin to INR (e.g., 1)                                        |
| INR\_SETTLEMENT\_USDT           | The conversion rate for INR settlement to USDT (e.g., 88).                                 |
| INR\_SETTLEMENT\_INR            | The conversion rate for INR settlement to INR (e.g., 1)                                    |
| USDT\_SETTLEMENT\_USDT          | The conversion rate for USDT settlement to USDT (e.g., 1).                                 |
| USDT\_MARGIN\_USDT              | The conversion rate for USDT margin to USDT (e.g., 1)                                      |

# Web Sockets

WebSockets are used to provide real-time updates and maintain a continuous connection between clients (traders) and servers (exchanges).

https://lightningnodes.github.io/slate/?python#change-log
---
# Change Log – Pi42 API Reference Documentation

Here's how different web sockets work:

# Authenticated Web Sockets

Authenticated WebSockets require user validation to ensure that only authorized users can access the data or functionality provided such as receiving real-time updates about a trader's account. For example, balance changes, order executions, or margin updates.

# Notes:

- Authenticated Web Socket stream base URL: https://fawss-uds.pi42.com/auth-stream
- Requires listenkey that can be obtained from the Create Listen Key API

The WebSocket client connects to a server using a listen key and listens for various events related to trading activities and session management. Each event handler logs specific information when the event is received. Event listeners are described below:

| Event                | Description                                                      |
| -------------------- | ---------------------------------------------------------------- |
| connect              | Triggered when the connection to the WebSocket server is open.   |
| newPosition          | Triggered when a new position is received from the server.       |
| orderFilled          | Triggered when an order is completely filled.                    |
| orderPartiallyFilled | Triggered when an order is partially filled.                     |
| orderCancelled       | Triggered when an order is cancelled.                            |
| orderFailed          | Triggered when an order fails.                                   |
| newOrder             | Triggered when a stop order is executed.                         |
| updateOrder          | Triggered when a stop limit order is executed.                   |
| updatePosition       | Triggered when a position is updated.                            |
| closePosition        | Triggered when a position is closed.                             |
| balanceUpdate        | Triggered when the balance is updated.                           |
| newTrade             | Triggered when a new trade occurs.                               |
| sessionExpired       | Triggered when the session expires.                              |
| disconnect           | Triggered when the connection to the WebSocket server is closed. |

# Required installations:

# python-socketio asyncio aiohttp
import socketio
import asyncio

WebSocket server URL (without namespace): https://lightningnodes.github.io/slate/?python#change-log
---
# Change Log – Pi42 API Reference Documentation

server_url  = 'Pi42-Authenticated-websocket-url'
# Namespace path for authorized streaming
namespace_path  = '/auth-stream/your-listen-key'
# Create a new asynchronous Socket.IO client
sio  = socketio.AsyncClient()
# Event listener for a successful connection to the server
@sio.event
async def connect():
print('Successfully connected to the WebSocket server')
# Event listener for when the connection to the server is closed
@sio.event
async def disconnect():
print('Disconnected from the WebSocket server')
# Event handler for receiving a new position update from the server
@sio.on('newPosition', namespace=namespace_path)
async def on_new_position(data):
print("New position received:", data)
# Event handler for receiving an order filled notification
@sio.on('orderFilled', namespace=namespace_path)
async def on_order_filled(data):   # Accept data parameter
print("Order filled:", data)
# Event handler for receiving a partially filled order update
@sio.on('orderPartiallyFilled',  namespace=namespace_path)
async def on_order_partially_filled(data):
print("Order partially filled:", data)
# Event handler for receiving a cancelled order notification
@sio.on('orderCancelled', namespace=namespace_path)
async def on_order_cancelled(data):
print("Order cancelled:", data)
# Event handler for receiving a failed order notification
@sio.on('orderFailed', namespace=namespace_path)
async def on_order_failed(data):
print("Order failed:", data)
# Event handler for receiving a new order(TP/SL) notification
@sio.on('newOrder', namespace=namespace_path)
async def on_new_order(data):
print("New order:", data)
# Event handler for receiving a position update
@sio.on('updatePosition', namespace=namespace_path)
async def on_update_position(data):
print("Position updated:", data)
# Event handler for receiving a position close notification
@sio.on('closePosition', namespace=namespace_path)
async def on_close_position(data):
print("Position closed:", data)
# Event handler for balance update notifications
@sio.on('balanceUpdate', namespace=namespace_path)
async def on_balance_update(data):
print("Balance updated:", data)
# Event handler for receiving a new trade notification
@sio.on('newTrade', namespace=namespace_path)
async def on_new_trade(data):
print("New trade:", data)
# Event handler for session expiration notifications
@sio.on('sessionExpired', namespace=namespace_path)
async def on_session_expired(data):
print("Session expired:", data)

https://lightningnodes.github.io/slate/?python#change-log
---
# Change Log – Pi42 API Reference Documentation

# Event listener for connection errors

@sio.event
async def connect_error(data):
print('Failed to connect to the WebSocket server:', data)

# Main function to initiate and maintain the WebSocket connection

async def main():
try:
# Attempt to connect to the server with specified transports
await sio.connect(server_url, transports=["websocket"])
await sio.wait()  # Keeps the connection open to listen for events
except Exception as e:
print("Connection error:", e)

# Entry point for the asyncio program

# Uses asyncio.run() to execute the main coroutine
if __name__ == '__main__':
asyncio.run(main())

# Public Web Sockets

Public WebSockets are open to all clients and do not require authentication to establish a connection. They are useful for scenarios where the data being transmitted is not sensitive or where the application does not require user-specific interactions. For example, to receive real-time updates on market data such as price changes, order book depth, and trade history without requiring authentication.

Public Web Socket URL: https://fawss.pi42.com/

Once connected, users can subscribe to different topics mentioned below:

| Parameter                          | Example              | Listening Topic    |
| ---------------------------------- | -------------------- | ------------------ |
| contract\_pair\@depth\_minGrouping | btcinr\@depth \_ 0.1 | depthUpdate        |
| contract \_pair\@kline \_ interval | btcinr\@kline \_ 1m  | kline              |
| contract \_pair\@markPrice         | btcinr\@markPrice    | markPriceUpdate    |
| contract \_pair\@aggTrade          | btcinr\@aggTrade     | aggTrade           |
| contract \_pair\@ticker            | btcinr\@ticker       | 24hrTicker         |
| contract \_pair\@marketInfo        | btcinr\@marketInfo   | marketInfo         |
| markPriceArr                       | N/A                  | markPriceArr       |
| tickerArr                          | N/A                  | tickerArr          |
| All contracts details              | N/A                  | allContractDetails |

Intervals: The intervals for kline (candlestick) data can be 1m, 3m, 5m, 15m, 30m, 1h, 2h, 4h, 6h, 8h, 12h, 1d, 3d, 1w, 1M.

MinGroupings: Depth groupings vary by contract. For example, 0.1 is used for BTC.

Get depthGrouping value of each contract from Exchange Info API

# Required installations:

# pip install python-socketio

https://lightningnodes.github.io/slate/?python#change-log
---
# Change Log – Pi42 API Reference Documentation

import socketio
# WebSocket server URL
server_url = 'https://fawss.pi42.com/'
# Create a new Socket.IO client
sio  = socketio.Client()
# Event listener for when the connection is open
@sio.event
def connect():
print('Connected to WebSocket server')
subscribe_to_topics()
# Event listener for when the connection is closed
@sio.event
def disconnect():
print('Disconnected from WebSocket server')
# Event listener for errors
@sio.event
def connect_error(data):
print('Socket.IO connection error:', data)
# Event listener for general errors
@sio.on('error')
def handle_error(data):
print('Socket.IO error:', data)
# Function to subscribe to various WebSocket topics
def subscribe_to_topics():
topics = ['btcinr@depth_0.1', 'btcinr@markPrice']  # List of topics to subscribe to
# Subscribe to each topic
sio.emit('subscribe',  {
'params': topics    # Sends the topics array to the WebSocket server
})
# Event listeners for updates on various data topics
@sio.on('depthUpdate')
def on_depth_update(data):
print('depthUpdate:', data)
@sio.on('kline')
def on_kline(data):
print('kline:', data)
@sio.on('markPriceUpdate')
def on_mark_price_update(data):
print('markPriceUpdate:',  data)
@sio.on('aggTrade')
def on_agg_trade(data):
print('aggTrade:',  data)
@sio.on('24hrTicker')
def on_24hr_ticker(data):
print('24hrTicker:', data)
@sio.on('marketInfo')
def on_market_info(data):
print('marketInfo:', data)
@sio.on('markPriceArr')
def on_mark_price_arr(data):
print('markPriceArr:', data)
@sio.on('tickerArr')
def on_ticker_arr(data):
print('tickerArr:',  data)
---
# Change Log – Pi42 API Reference Documentation

@sio.on('marginRate')
def on_margin_rate(data):
print('marginRate:', data)

# Connect to the WebSocket server

sio.connect(server_url)
# Keep the connection open
sio.wait()

# Create Listen Key

POST /v1/retail/listen-key

Creates a new listen key for WebSocket connections. A listen key is used to maintain a persistent connection to the WebSocket server, allowing you to receive real-time updates on user account data.

| Parameter | Type   | Required | Description                                                                                   |
| --------- | ------ | -------- | --------------------------------------------------------------------------------------------- |
| timestamp | string | Yes      | The current timestamp in milliseconds to ensure request uniqueness and prevent replay attacks |

The createListenKey function also requires an apiKey and apiSecret for authentication, and these are included in the headers of the request:

apiKey : The API key for authenticating the request.
apiSecret : The API secret used to generate the signature for request validation.

The function generates a signature using HMAC SHA-256 encryption of the request parameters and sends a POST request to the API endpoint to create a new listen key. If successful, it logs and returns the listen key; otherwise, it logs and throws the error for further handling.

# RESPONSE

The response parameters are described below:

// Response
{
"listenKey": "c44ec0b16e1e79d82473283a9736d2d037f105c39190ad48539fd6479a5b8ecc"
}

| Parameter | Description                                                                                                                                                                               |
| --------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| listenKey | The unique identifier for the Listen Key, used to maintain a persistent connection for real-time data streams. Example: c44ec0b16e1e79d82473283a9736d2d037f105c39190ad48539fd6479a5b8ecc. |

# Get Listen Key

POST /v1/retail/listen-key

Retrieves a new listen key for WebSocket connections. A listen key is used to maintain a persistent WebSocket connection, allowing you to receive real-time updates.

https://lightningnodes.github.io/slate/?python#change-log
---
# Change Log – Pi42 API Reference Documentation

def create_or_update_listen_key():
timestamp  = str(int(time.time() * 1000))
params = {
'timestamp': timestamp
}
# Convert the parameters to a query string (if signing a query string)
data_to_sign  = json.dumps(params, separators=(',', ':'))
signature  = generate_signature(api_secret, data_to_sign)
# Headers for the request
headers =  {
'api-key': api_key,
'Content-Type':  'application/json',
'signature': signature,
}
try:
# Send the POST request to create or update a listen key
response = requests.post(f'{listen_key_url}', json=params, headers=headers)
response.raise_for_status()
response_data =  response.json()
print('Listen key created or updated successfully:', json.dumps(response_data, indent=4))
except requests.exceptions.HTTPError  as err:
print(f"Failed {response.status_code}:  {response.text}")

| Parameter | Type | Required | Description                                                                                                    |
| --------- | ---- | -------- | -------------------------------------------------------------------------------------------------------------- |
| None      | N/A  | No       | A listen key is used to maintain a persistent WebSocket connection, allowing you to receive real-time updates. |

# Update Listen Key

PUT /v1/retail/listen-key
Updates the listen key for WebSocket connections.
Updating the listen key is necessary to maintain an active WebSocket connection and prevent disconnections due to inactivity.

| Parameter | Type | Required | Description                                       |
| --------- | ---- | -------- | ------------------------------------------------- |
| None      | N/A  | No       | Updates the listen key for WebSocket connections. |

def update_listen_key_expiry():
timestamp  = str(int(time.time() * 1000))
params = {
'timestamp': timestamp
}
data_to_sign  = json.dumps(params, separators=(',', ':'))
# Generate the signature using the provided helper function
signature  = generate_signature(api_secret, data_to_sign)
# Headers for the PUT request
headers =  {
'api-key': api_key,
'signature': signature,
}

https://lightningnodes.github.io/slate/?python#change-log
---
# Change Log – Pi42 API Reference Documentation

try:
# Send the PUT request to update the listen key expiry
response  = requests.put(listen_key_url, json=params, headers=headers)
print('Listen key expiry updated successfully:', response)
except Exception as  e:
print(f"Failed  {response.status_code}: {response.text}")

# RESPONSE

The response contains a message as shown:

//  Response
Listen Key expiry  time updated successfully.

# Delete Listen Key

DELETE /v1/retail/listen-key
Deletes the listen key for WebSocket connections.
This action terminates the connection and stops the receipt of real-time updates.

def delete_listen_key():
# Generate the current timestamp
timestamp  = str(int(time.time() * 1000))
# Prepare the data for the request (listenKey is passed in the URL path)
params = {
'timestamp': timestamp
}
# Generate the signature based on the params
data_to_sign  = json.dumps(params, separators=(',', ':'))
signature  = generate_signature(api_secret, data_to_sign)
# Headers for the DELETE request
headers =  {
'api-key': api_key,
'signature': signature,
'accept': '*/*'
}
# Construct the full URL, inserting the listenKey into the path
delete_listen_key_url = f"{base_url}/v1/retail/listen-key/"
try:
# Send the DELETE request to delete the listen key
response  = requests.delete(delete_listen_key_url,  json=params, headers=headers)
response.raise_for_status()  # Raises an error for 4xx/5xx responses
print('Listen key deleted successfully.')
except  requests.exceptions.HTTPError as err:
print(f"Error:  {err.response.text if err.response  else err}")
except  Exception as e:
print(f"An unexpected error occurred:  {str(e)}")

| Parameter | Type | Required | Description                                      |
| --------- | ---- | -------- | ------------------------------------------------ |
| None      | N/A  | No       | Deletes the listen key for WebSocket connections |

https://lightningnodes.github.io/slate/?python#change-log
---
# Change Log – Pi42 API Reference Documentation

The response body contains the message as shown in the snippet:

Listen key deleted successfully.

# Error Codes

Pi42 APIs utilize a set of custom error codes, each associated with an HTTP status code and a specific error message. These codes help users pinpoint the exact issue that caused the request to fail.

| Error Code | HTTP Status Code | Error Message                                               | API Endpoints                                                         |
| ---------- | ---------------- | ----------------------------------------------------------- | --------------------------------------------------------------------- |
| 2303       | 400              | Contract pair not found                                     | v1/exchange/update/leverage                                           |
| 2304       | 400              | Leverage value out of range                                 | v1/exchange/update/leverage                                           |
| 2305       | 400              | Leverage cannot be updated with open position               | v1/exchange/update/leverage                                           |
| 2306       | 400              | Leverage cannot be updated with open orders                 | v1/exchange/update/leverage                                           |
| 2307       | 500              | Unable to update user leverage preference                   | v1/exchange/update/leverage                                           |
| 2400       | 400              | Interval value is invalid                                   | v1/market/klines                                                      |
| 2401       | 500              | Unable to fetch kline data                                  | v1/market/klines v1/market/depth/{contractPair}                       |
| 2402       | 400              | Invalid contract pair                                       | v1/market/aggTrade/{contractPair} v1/market/ticker24Hr/{contractPair} |
| 2403       | 500              | Unable to fetch depth update for given contract pair        | v1/market/depth/{contractPair}                                        |
| 2404       | 500              | Unable to fetch trade update for given contract pair        | v1/market/aggTrade/{contractPair}                                     |
| 2405       | 500              | Unable to fetch 24 hr ticker update for given contract pair | v1/market/ticker24Hr/{contractPair}                                   |
| 2406       | 400              | Invalid market is provided                                  | v1/market/marketInfo                                                  |
| 2407       | 500              | Unable to fetch market information                          | v1/market/marketInfo                                                  |
| 2500       | 400              | Account id not found                                        | v1/positions/{positionStatus}                                         |
| 2501       | 500              | Unable to fetch positions                                   | v1/positions/{positionStatus}                                         |
| 2502       | 400              | No position exists with provided position id                | v1/positions                                                          |

https://lightningnodes.github.io/slate/?python#change-log
---
# Change Log – Pi42 API Reference Documentation

| Error Code | HTTP Status Code | Error Message                                                                              | API Endpoints         |
| ---------- | ---------------- | ------------------------------------------------------------------------------------------ | --------------------- |
| 2503       | 400              | Invalid contract pair                                                                      | v1/positions          |
| 2504       | 500              | Unable to fetch position for provided position id                                          | v1/positions          |
| 3000       | 400              | Incorrect device type in header values                                                     | v1/order/place-order  |
| 3001       | 400              | Symbol is missing                                                                          | v1/order/place-order  |
| 3003       | 400              | Invalid leverage                                                                           | v1/order/place-order  |
| 3004       | 400              | Invalid order side                                                                         | v1/order/place-order  |
| 3005       | 400              | Order price not present                                                                    | v1/order/place-order  |
| 3006       | 400              | Quantity precision should be less than {value}                                             | v1/order/place-order  |
| 3007       | 400              | Price precision should be less than {value}                                                | v1/order/place-order  |
| 3008       | 400              | Limit price is required                                                                    | v1/order/place-order  |
| 3009       | 400              | Limit price is out of allowed values                                                       | v1/order/place-order  |
| 3010       | 400              | Order quantity is out of range                                                             | v1/order/place-order  |
| 3011       | 400              | Order declined, TP/SL will be activated instantly                                          | v1/order/place-order  |
| 3012       | 400              | Margin asset {asset} is not supported for this contract                                    | v1/order/place-order  |
| 3013       | 400              | Order placement for this contract pair is not allowed as there is already an open order    | v1/order/place-order  |
| 3014       | 400              | Order placement for this contract pair is not allowed as there is already an open position | v1/order/place-order  |
| 3015       | 400              | Take profit/Stop loss orders cannot be placed while reducing position                      | v1/order/place-order  |
| 3018       | 400              | Insufficient margin                                                                        | v1/order/place-order  |
| 3019       | 400              | Ref id already exists                                                                      | v1/order/place-order  |
| 3020       | 400              | API request limit exceeded                                                                 | v1/order/place-order  |
| 3021       | 400              | Order type is not supported                                                                | v1/order/place-order  |
| 3022       | 500              | Order execution error                                                                      | v1/order/place-order  |
| 3023       | 500              | Order cancellation error                                                                   | v1/order/cancel-order |

https://lightningnodes.github.io/slate/?python#change-log