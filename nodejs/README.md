# The challenge
We need to create a new **API** to manage payments transactions of our merchants. That been said, we need:

1. Endpoints to process payments transactions and return the list of all transactions created for a given merchant. 

2. A payment transaction must contains at least:
    * The gross amount of the transaction, in a decimal formatted string.
    * Description of the transaction, for example: “T-Shirt Black/M”
    * The payment method: **debit_card** or **credit_card**  
    * The card number, cardholder name, card expiration date and card verification code (CVV).

3. As the card number is sensitive information, we must store and return only the last 4 digits of the card.

4. Create merchant receivables (payables), following the business requirements:

    * **Debit card** transaction:
      * The payable must be created with **status = paid**, indicating that the merchant has already received this amount.
      * The payable must be created with the payment date equal to the date of creation of the transaction (D + 0).
      
    * **Credit card** transaction:
      * The payable must be created with **status = waiting_funds**, indicating that the merchant will receive this amount in the future.
      * The payable must be created with the payment date equal to the date of creation of the transaction + 30 days (D + 30).

5. When the payables are created, the processing fee must be discounted. Consider **2%** of fee for **debit card** transactions and **4%** for **credit card** transactions. Example: when a merchant processes R$ 100,00 from a credit card transaction, he will receive R$ 96,00. 

6. We also need an endpoint that returns the total receivable (payables) from all merchants by a period, and an endpoint that returns the total fee by a period.

7. Write down unit tests, at least for the main logic.