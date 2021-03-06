# Dissociate tokens from an account

Disassociates the provided account from the provided tokens. This transaction must be signed by the provided Account's Key. Once the association is removed, no token related operation can be performed to that account. AccountBalanceQuery and AccountInfoQuery will not return anything related to the token that was disassociated.

*  If the provided account is not found, the transaction will resolve to INVALID\_ACCOUNT\_ID.
*  If the provided account has been deleted, the transaction will resolve to ACCOUNT\_DELETED.
*  If any of the provided tokens is not found, the transaction will resolve to INVALID\_TOKEN\_REF.
* If any of the provided tokens has been deleted, the transaction will resolve to TOKEN\_WAS\_DELETED.
* If an association between the provided account and any of the tokens does not exist, the transaction will resolve to TOKEN\_NOT\_ASSOCIATED\_TO\_ACCOUNT.
* If the provided account has a nonzero balance with any of the provided tokens, the transaction will resolve to TRANSACTION\_REQUIRES\_ZERO\_TOKEN\_BALANCES.
* On success, associations between the provided account and tokens are removed.

{% hint style="info" %}
The account is required to have a zero balance of the token you wish disassociates. If a token balance is present, you will receieve a TRANSACTION\_REQUIRES\_ZERO\_TOKEN\_BALANCES error.
{% endhint %}

| Constructor | Description |
| :--- | :--- |
| `new TokenDissociateTransaction()` | Initializes the TokenDissociateTransaction object |

```java
new TokenDissociateTransaction()
```

### Methods

| Method | Type | Description | Requirement |
| :--- | :--- | :--- | :--- |
| `setTokenId(<tokenId>)` | [TokenId](token-id.md) | The tokens to be dissociated with the provided account | Required |
| `setAccountId(<accountId>)` | [AccountId](../specialized-types.md#accountid) | The account to be dissociated with the provided tokens | Required |

{% tabs %}
{% tab title="Java" %}
```java
//Disassociate a token from an account
TokenDissociateTransaction transaction = new TokenDissociateTransaction()
    .setAccountId(accountId)
    .addTokenId(tokenId);
        
//Build the unsigned transaction, sign with the private key of the account that is being dissociated from a token, submit the transaction to a Hedera network
TransacionId transactionId = transaction.build(client).sign(accountKey).execute(client);
    
//Request the receipt of the transaction
TransactionReceipt getReceipt = transactionId.getReceipt(client);
    
//Obtain the transaction consensus status
Status transactionStatus = getReceipt.status;

System.out.println("The transaction consensus status is: " +transactionStatus);
//Version: 1.2.2
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
//Disassociate a token from an account
const transaction = await new TokenDissociateTransaction()
    .setAccountId(accountId)
    .addTokenId(tokenId);
        
//Build the unsigned transaction, sign with the private key of the account that is being dissociated from a token, submit the transaction to a Hedera network
const transactionId = await transaction.build(client).sign(accountKey).execute(client);
    
//Request the receipt of the transaction
const getReceipt = await transactionId.getReceipt(client);
    
//Obtain the transaction consensus status
const transactionStatus = await getReceipt.status;

console.log("The transaction consensus status is: " +transactionStatus);
//Version 1.4.2
```
{% endtab %}
{% endtabs %}





