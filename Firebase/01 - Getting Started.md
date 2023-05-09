## Set up a Firebase project

Go to the Firebase Console, sign in, and create a new project. Once your project is created, click on the "Add app" button to add a new web app. Follow the instructions to register your app and obtain your Firebase configuration credentials, including your API key, authDomain, and projectId.

## Set up Firebase SDK

Add the Firebase SDK to your web app by adding the following code to your HTML file, just before the closing </body> tag:

```html
<!-- The core Firebase JS SDK is always required and must be listed first -->
<script src="https://www.gstatic.com/firebasejs/8.4.2/firebase-app.js"></script>

<!-- Add Firebase products that you want to use -->
<script src="https://www.gstatic.com/firebasejs/8.4.2/firebase-firestore.js"></script>

<!-- Initialize Firebase -->
<script>
  // Your web app's Firebase configuration
  var firebaseConfig = {
    apiKey: "YOUR_API_KEY",
    authDomain: "YOUR_AUTH_DOMAIN",
    projectId: "YOUR_PROJECT_ID",
    storageBucket: "YOUR_STORAGE_BUCKET",
    messagingSenderId: "YOUR_MESSAGING_SENDER_ID",
    appId: "YOUR_APP_ID"
  };
  
  // Initialize Firebase
  firebase.initializeApp(firebaseConfig);
</script>
```

## Create a Firestore database

In the Firebase Console, go to the "Firestore Database" section and click on the "Create Database" button. Follow the instructions to create a new Firestore database, and select the appropriate region and mode for your app.

## Set up Firestore security rules

Firestore security rules control access to your data, so it's important to set them up correctly. In the Firebase Console, go to the "Firestore Database" section and click on the "Rules" tab. Replace the default rules with the following to allow authenticated users to read and write data:

```javascript
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /{document=**} {
      allow read, write: if request.auth != null;
    }
  }
}
```

## Read and write data

With the Firebase SDK and Firestore set up, you can now read and write data to your Firestore database. To write data, use the set() method on a DocumentReference object, like this:

```javascript
var db = firebase.firestore();
var docRef = db.collection("users").doc("alice");

docRef.set({
  name: "Alice",
  age: 30,
  email: "alice@example.com"
})
.then(function() {
  console.log("Document successfully written!");
})
.catch(function(error) {
  console.error("Error writing document: ", error);
});

```

This is just a basic overview to help you get started with Firebase and Firestore using JavaScript. There are many more features and capabilities to explore, including real-time data updates, cloud functions, and more.