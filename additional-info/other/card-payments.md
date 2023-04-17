# 💳 Card Payments

### Terms

#### General

**POS** - Point-of-Sale Terminal aka Merchant Terminal

Acquiring Bank (**Acquirer**) - bank that processes card payments on behalf of a merchant

**Issuing Bank** ("Emitent" - RU) - bank that offers payment cards directly to consumers

#### Cards

**MII** - major industry identifier (2 - MIR, 3 - American Express, 4 - Visa, 5 -  MasterCard, 6 UnionPay)

**BIN** - Bank Identification Number - the first four to six numbers that appear on payment cards, or Issuer Identification Number (**IIN**)

**PAN** - Primary Account Number - Card Number

#### Online Card Payments

**CNP** - Card Not Present

CNP Types:

* **CIT** - Customer Initiated Transaction
* **MIT** - Merchant Initiated Transaction
* **COF** - Card On File&#x20;

### Card Data

<figure><img src="../../.gitbook/assets/изображение (5).png" alt=""><figcaption></figcaption></figure>

* First digit is the major industry identifier (MII)
* A six or eight-digit Issuer Identification Number (IIN/BIN)
* A variable length (up to 12 digits) individual account identifier/number
* Last one number - a checksum, which is a key that shows whether a credit card is valid or not

### Payment: Payment stages

* 🕙 Authorization (Merchant => Bank Acquirer => Payment System => Issuing bank)
* 📄 Sending for clearing (capture, presentment, clear) (Merchant => Bank Acquirer => Payment System => Issuing bank)
* ❌ Cancellations (Merchant => Bank Acquirer => Payment System => Issuing bank)
* 🤑 Refunds (User request => Merchant => Bank Acquirer => Payment System => Issuing bank)
* 🕵️‍♂️ Chargeback (User request => Issuing bank => Payment System => Bank Acquirer)

### Online Payments

Main types:&#x20;

* CIT - triggered by Customer
* MIT - triggered by Merchant
* Recurrent Payment - triggered by Merchant, based on previous payments
* COF - could be triggered by Merchant or Customer, using already saved to service card data (without CVV)

