## Initialize Firebase in Your React App

Create a Firebase configuration file (e.g., firebase.js) in your project's source directory.

Import the necessary Firebase modules and initialize Firebase with your project configuration.

Export the initialized Firebase instance to use it throughout your app.

```javascript
import firebase from 'firebase/app';
import 'firebase/firestore';

// Your Firebase project configuration
const firebaseConfig = {
  // Add your configuration here
};

// Initialize Firebase
firebase.initializeApp(firebaseConfig);

// Export the Firestore instance
export const db = firebase.firestore();

```

## Fetching Data from Firestore

To fetch data from Firestore, you can use Firestore's query methods like get() and onSnapshot().

In a React component, you can use hooks like useState and useEffect to manage the data and perform the initial fetch and subsequent updates.

```javascript
import { useEffect, useState } from 'react';
import { db } from './firebase';

const MyComponent = () => {
  const [data, setData] = useState([]);

  useEffect(() => {
    const fetchData = async () => {
      try {
        const querySnapshot = await db.collection('myCollection').get();
        const newData = querySnapshot.docs.map((doc) => doc.data());
        setData(newData);
      } catch (error) {
        console.error('Error fetching data:', error);
      }
    };

    fetchData();
  }, []);

  return (
    <div>
      {data.map((item) => (
        <p key={item.id}>{item.name}</p>
      ))}
    </div>
  );
};

```

## Real-time Updates in React

To receive real-time updates from Firestore, you can use the onSnapshot() method within a useEffect hook to listen for changes and update your component state accordingly.

```javascript
import { useEffect, useState } from 'react';
import { db } from './firebase';

const MyComponent = () => {
  const [data, setData] = useState([]);

  useEffect(() => {
    const unsubscribe = db.collection('myCollection').onSnapshot((querySnapshot) => {
      const newData = querySnapshot.docs.map((doc) => doc.data());
      setData(newData);
    });

    return () => {
      // Unsubscribe from the listener when component unmounts
      unsubscribe();
    };
  }, []);

  return (
    <div>
      {data.map((item) => (
        <p key={item.id}>{item.name}</p>
      ))}
    </div>
  );
};

```

## Adding Data to Firestore

To add data to Firestore, you can use the set() method on a document reference.

```javascript
import { db } from './firebase';

const addData = async () => {
  try {
    const data = { name: 'John Doe', age: 25 };
    await db.collection('myCollection').doc().set(data);
    console.log('Data added successfully!');
  } catch (error) {
    console.error('Error adding data:', error);
  }
};

```

## Updating and Deleting Data

You can update data in Firestore using the update() method on a document reference.

```javascript
import { db } from './firebase';

const updateData = async () => {
  try {
    const docRef = db.collection('myCollection').doc('documentId');
    await docRef.update({ name: 'Updated Name' });
    console.log('Data updated successfully!');
  } catch (error) {
    console.error('Error updating data:', error);
  }
};

const deleteData = async () => {
  try {
    const docRef = db.collection('myCollection').doc('documentId');
    await docRef.delete();
    console.log('Data deleted successfully!');
  } catch (error) {
    console.error('Error deleting data:', error);
  }
};

```

By following these steps, you can integrate Firestore into your React application, fetch data, receive real-time updates, and perform create, read, update, and delete (CRUD) operations seamlessly.