# The challenge
Your challenge is to build a new **API's** to manage payments transactions of our merchants. 

## Functional requirements
We need an endpoint that calculates the merchant's total Payables by period, the response should contain:
- Total amount of receivables
- Amount receivable for the future
- Total fee charged

## Considerations
1. Endpoints to process payments transactions and return the list of all transactions created for a given merchant. 
2. A payment transaction must contains at least:
    * The gross amount of the transaction, in a decimal formatted string.
    * Description of the transaction, for example: “T-Shirt Black/M”
    * The payment method: **debit_card** or **credit_card**
    * The card number, cardholder name, card expiration date and card verification code (CVV).
3. As the card number is sensitive information, we must store and return only the last 4 digits of the card.
4. Create merchant **receivables (payables)**, following the business requirements:
    * **Debit card**:
      * The payable must be created with **status = paid,** indicating that the merchant has already received this amount.
      * The payable must be created with the payment date equal to the date of creation of the transaction (D + 0).
    * **Credit card**:
      * The payable must be created with **status = waiting_funds**, indicating that the merchant will receive this amount in the future.
      * The payable must be created with the payment date equal to the date of creation of the transaction + 30 days (D + 30).
5. When the payables are created, the processing fee must be discounted. Consider 2% of fee for **debit card** transactions and 4% for **credit card** transactions. Example: when a merchant processes $ 100,00 from a credit card transaction, he will receive $ 96,00. 

## Technical requirements
  * RESTFul API with NodeJS
  * Best practices
    * Use OOP instead of multiple if / else or switch / case statements.
    * SOLID, DRY code.
  * Error handling
    * HTTP status code
    * Handle exceptions to show expected error messages to the client
  * Unit testing
  * Observability
    * Logging (Plus)
  * Technically explain requirements that weren’t completed on time.
  * Use the Json Server to persist transaction information

# Installation
Requirement is to have docker on your machine to run our mock API:

```
docker-compose up
```

## Mock API
With the service running you can use the following API's:

---

## Transactions
List of registered `transactions` `GET http://0.0.0.0:8080/transactions`

Loading a `transaction` specific `GET http://0.0.0.0:8080/transactions/:id`

Creation of `transactions` `POST http://0.0.0.0:8080/transactions`

`Transaction` removal by ID `DELETE http://0.0.0.0:8080/transactions/:id`

---

## Payables
List of registered `payables` `GET http://0.0.0.0:8080/payables`

Loading a specific `payable` `GET http://0.0.0.0:8080/payables/:id`

Creating `payables` POST `http://0.0.0.0:8080/payables`

`Payable` removal by ID `DELETE http://0.0.0.0:8080/payables/:id`
