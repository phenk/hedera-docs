# TransactionRecord

## TransactionRecord

Response when the client sends the node TransactionGetRecordResponse



| Field | Type | Label | Description |
| :--- | :--- | :--- | :--- |
| receipt | [TransactionReceipt](transactionreceipt.md) |  | The status \(reach consensus, or failed, or is unknown\) and the ID of any new account/file/instance created.  |
| transactionHash | bytes |  | The hash of the Transaction that executed \(not the hash of any Transaction that failed for having a duplicate TransactionID\)  |
| consensusTimestamp | [Timestamp](timestamp.md) |  | The consensus timestamp \(or null if didn't reach consensus yet\)  |
| transactionID | [TransactionID](../basic-types/transactionid.md) |  | The ID of the transaction this record represents  |
| memo | string |  | The memo that was submitted as part of the transaction \(max 100 bytes\)  |
| transactionFee | uint64 |  | The actual transaction fee charged, not the original transactionFee value from TransactionBody  |
| contractCallResult | ContractFunctionResult |  | Record of the value returned by the smart contract function \(if it completed and didn't fail\) from ContractCallTransaction  |
| contractCreateResult | ContractFunctionResult |  | Record of the value returned by the smart contract constructor \(if it completed and didn't fail\) from ContractCreateTransaction  |
| transferList | TransferList |  | All hbar transfers as a result of this transaction, such as fees, or transfers performed by the transaction, or by a smart contract it calls, or by the creation of threshold records that it triggers.  |
| tokenTransferLists | [TokenTransferList](../basic-types/tokentransferlist.md) | repeated | All Token transfers as a result of this transaction  |

