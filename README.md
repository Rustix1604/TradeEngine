# Trading Low-Latency Engine

This repository contains a simple low-latency trading engine implemented in TypeScript. The engine supports basic functionalities such as handling limit orders, market orders, providing order book depth, and calculating final account balances after all orders are executed.

## Features

1. **Place Limit Orders**: Create limit orders to buy or sell at a specified price.
2. **Execute Market Orders**: Retrieve the best available price from the order book to fulfill a buy or sell order.
3. **View Order Book Depth**: Check the current state of the order book, including bid and ask prices and quantities.
4. **Check Final Balances**: Get the final account balance after executing all orders.

---

## API Endpoints

### 1. `POST /order`
**Purpose**: Submit a limit order (buy/sell).

**Request Body**:
```json
{
  "type": "limit",       
  "side": "buy",       
  "price": 100.5,     
  "quantity": 10         
}
```

**Response**:
```json
{
  "status": "success",
  "orderId": "12345",   
  "message": "Order placed successfully."
}
```

### 2. `GET /quote`
**Purpose**: Execute a market order and get the best available price.

**Query Parameters**:
- `side`: The side of the order (`buy` or `sell`).
- `quantity`: The quantity of the asset.

**Example**:
`GET /quote?side=buy&quantity=5`

**Response**:
```json
{
  "status": "success",
  "executedPrice": 101.0,  
  "quantity": 5,         
  "message": "Market order executed."
}
```

### 3. `GET /depth`
**Purpose**: Retrieve the current order book.

**Response**:
```json
{
  "bids": [
    { "price": 100.0, "quantity": 20 },
    { "price": 99.5, "quantity": 15 }
  ],
  "asks": [
    { "price": 101.0, "quantity": 25 },
    { "price": 102.5, "quantity": 10 }
  ]
}
```

### 4. `GET /balance`
**Purpose**: Retrieve the final account balance after executing all orders.

**Response**:
```json
{
  "status": "success",
  "balance": {
    "USD": 5000,   
    "ASSET": 100    
  }
}
```

---

## Setup Instructions

1. **Clone the Repository**:
   ```bash
   git clone https://github.com/your-username/trading-engine.git
   cd trading-engine
   ```

2. **Install Dependencies**:
   ```bash
   npm install
   ```

3. **Run the Application**:
   ```bash
   npm start
   ```

4. **Test the Endpoints**:
   Use tools like Postman, curl, or any HTTP client to test the API endpoints.

---

## Example Workflow

1. Place a limit order:
   ```
   POST /order
   {
     "type": "limit",
     "side": "buy",
     "price": 100,
     "quantity": 10
   }
   ```

2. Place a market order:
   ```
   GET /quote?side=buy&quantity=5
   ```

3. View the order book:
   ```
   GET /depth
   ```

4. Check final balance:
   ```
   GET /balance
   ```

---

## Technologies Used
- **TypeScript**: Ensures type safety and modern JavaScript features.
- **Express.js**: Lightweight and fast Node.js framework for building APIs.

---

## Future Enhancements
- Add support for stop-loss and take-profit orders.
- Improve matching engine to handle larger order volumes efficiently.
- Implement WebSocket support for real-time updates on trades and order book changes.

---



