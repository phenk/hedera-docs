# FileAppend

## FileAppendTransactionBody

‌Append the given contents to the end of the specified file. If a file is too big to create with a single FileCreateTransaction, then it can be created with the first part of its contents, and then appended as many times as necessary to create the entire file.

| Field | Type | Description |
| :--- | :--- | :--- |
| fileID | ​[FileID](/@docs-hedera/s/hedera-api/basic-types-1/untitled-2)​ | The file to which the bytes will be appended |
| contents | ​Content | The bytes that will be appended to the end of the specified file |

