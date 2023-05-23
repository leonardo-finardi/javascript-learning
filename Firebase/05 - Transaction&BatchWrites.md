## Firestore Transactions

Firestore transactions allow you to perform a series of read and write operations atomically. If any concurrent changes occur while the transaction is running, Firestore automatically retries the transaction to ensure data consistency.

To perform a transaction, you need to create a transaction object using the transaction() method of the Firestore instance. The transaction function takes a callback function that receives the transaction object as an argument.
Inside the transaction callback, you can perform read and write operations using the transaction object.

Here's an example of a Firestore transaction in JavaScript:

```javascript
const transaction = db.runTransaction(async (transaction) => {
  const docRef = db.collection('users').doc('user1');
  const docSnapshot = await transaction.get(docRef);
  const userData = docSnapshot.data();

  if (docSnapshot.exists) {
    const newBalance = userData.balance + 100; // Increase balance by 100
    transaction.update(docRef, { balance: newBalance });
  }
});

```

## Batch Writes

Batch writes in Firestore allow you to perform multiple write operations as a single atomic unit. This is useful when you need to update multiple documents together or create multiple documents atomically.

To perform a batch write, you need to create a batch object using the batch() method of the Firestore instance. You can then use the batch object to queue multiple write operations.

Once you have added all the operations to the batch object, you can commit the batch to execute all the operations atomically.

Here's an example of a Firestore batch write in JavaScript:

```javascript
const batch = db.batch();

const docRef1 = db.collection('users').doc('user1');
batch.update(docRef1, { name: 'John Doe' });

const docRef2 = db.collection('users').doc('user2');
batch.delete(docRef2);

const docRef3 = db.collection('users').doc();
batch.set(docRef3, { name: 'Jane Smith', age: 25 });

await batch.commit();

```

## Error Handling

Both transactions and batch writes can encounter errors. It's important to handle these errors appropriately.

In transactions, if an error occurs, the transaction function should throw an error to roll back the transaction.

In batch writes, you can use commit().catch() to handle errors that occur during the commit operation.
