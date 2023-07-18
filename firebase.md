# Firebase v9 Setup

The process of creating a new Firebase project and database is the same as always.

Go to the Firebase Console and click Add project.
Enter a project name, enable/disable Google Analytics and click create project.
Once your project is created Add a “Web App” to your project, name it, then you will be presented with a Firebase config that includes your apiKey, project ID, etc. Copy this to your clipboard and choose “Continue to console.”
Your config looks something like this


```javascript
// Import the functions you need from the SDKs you need
import { initializeApp } from "firebase/app";
// TODO: Add SDKs for Firebase products that you want to use
// https://firebase.google.com/docs/web/setup#available-libraries

// Your web app's Firebase configuration
const firebaseConfig = {
  apiKey: "AIzaTyD2Jp9aB7ycUbW1z8QyPLmD111rHezHcOw",
  authDomain: "delete-project-c7021.firebaseapp.com",
  projectId: "delete-project-c7021",
  storageBucket: "delete-project-c7021.appspot.com",
  messagingSenderId: "688102987186",
  appId: "1:688102987186:web:e27537ggg7abc2b86b982b"
};

// Initialize Firebase
const app = initializeApp(firebaseConfig);
```


This configuration deviates from the previous Firebase configs.

Firebase v9 is modular and allows you to import individual features as you need them (which is one of the perks of v9, a much smaller size).

We’ll now be calling functions like getAuth(), getFirebase(), getStorage(), etc., and imports now look like the following:

```js
import { initializeApp } from 'firebase/app';
import { getFirestore } from 'firebase/firestore';
import { getAuth, signInWithPopup, GoogleAuthProvider } from 'firebase/auth';
Pretty neat, yet different.

So create a config file in your project called firestore.js and add the following (using your values of course):

import { initializeApp } from 'firebase/app';
import { getFirestore } from 'firebase/firestore';
import { getAuth, GoogleAuthProvider } from 'firebase/auth';

const firebaseConfig = {
  apiKey: "AIzaTyD2Jp9aB7ycUbW1z8QyPLmD111rHezHcOw",
  authDomain: "delete-project-c7021.firebaseapp.com",
  projectId: "delete-project-c7021",
  storageBucket: "delete-project-c7021.appspot.com",
  messagingSenderId: "688102987186",
  appId: "1:688102987186:web:e27537ggg7abc2b86b982b"
};

const app = initializeApp(firebaseConfig);

export const db = getFirestore(app);
export const auth = getAuth();
export const provider = new GoogleAuthProvider();
provider.setCustomParameters({ prompt: 'select_account' });

```


1. We’ll import db anytime we need to access the database.
2. We’ll import auth anytime we need to authenticate with Firebase.
3. We’ll import provider anytime we need to authenticate with Google.


## Firebase v9 Authentication

Following our modular approach, to sign in with Google, we’ll use our Google provider and the signInWithPopup() method (be sure to change the auth and provider import path to match your project).

```js
import { signInWithPopup, GoogleAuthProvider } from 'firebase/auth';
import { auth, provider } from '../utils/firestore'; // update path to your firestore config

const googleHandler = async () => {
        provider.setCustomParameters({ prompt: 'select_account' });
        signInWithPopup(auth, provider)
            .then((result) => {
                // This gives you a Google Access Token. You can use it to access the Google API.
                const credential = GoogleAuthProvider.credentialFromResult(result);
                const token = credential.accessToken;
                // The signed-in user info.
                const user = result.user;
                // redux action? --> dispatch({ type: SET_USER, user });
            })
            .catch((error) => {
                // Handle Errors here.
                const errorCode = error.code;
                const errorMessage = error.message;
                // The email of the user's account used.
                const email = error.email;
                // The AuthCredential type that was used.
                const credential = GoogleAuthProvider.credentialFromError(error);
                // ...
            });
    };
```


To signOut, import the signOut module:

```js

import { signOut } from 'firebase/auth';
import { auth } from '../utils/firestore'; // update path to your firestore config

signOut(auth)
    .then(() => {
        console.log('logged out');
        navigate('/');
    })
    .catch((error) => {
        console.log(error);
    });

```

That code came directly from the Firebase docs.

For regular username/password, Facebook, Twitter, email link authentication, etc. refer to that page. Each example can be found in the navigation to the left. For example, click Password Authentication to see how to use the username/password authentication.

# Firebase v9 CRUD Examples

For CRUD functions, again we’ll import the modules we need like getDocs and setDoc, etc.

Here are some examples using Notes as an example:

*Note how you are importing/using doc and collection depending on whether you want a document or a collection

## setDoc

setDoc is used to create a document when you have a meaningful ID that you want to use. You must specify an ID.

```js


import { db } from '../utils/firestore'; // update with your path to firestore config
import { doc, setDoc } from "firebase/firestore"; 

export const createNote = async (note) => {
    await setDoc(doc(db, 'notes', note.id), note);
};
createNote(note);
```

## addDoc

Sometimes you do not have a meaningful ID that you want to use and thus want Firestore to create a unique one for you. For this, you use addDoc.

```js
import { db } from '../utils/firestore'; // update with your path to firestore config
import { doc, addDoc } from "firebase/firestore"; 

export const createNote = async (note) => {
    await addDoc(collection(db, 'notes'), coin);
};
createNote(note);

```

## getDoc

```js
import { db } from '../utils/firestore'; // update with your path to firestore config
import { doc, getDoc } from "firebase/firestore";

export const getNote = async (id) => {
    const noteSnapshot = await getDoc(doc(db, 'notes', id));
    if (noteSnapshot.exists()) {
        return noteSnapshot.data();
    } else {
        console.log("Note doesn't exist");
    }
};
getNote(id);

```

## getDocs

```js
import { db } from '../utils/firestore'; // update with your path to firestore config
import { collection, getDocs } from "firebase/firestore";

export const getNotes = async () => {
    const notesSnapshot = await getDocs(collection(db, "notes"));
    const notesList = notesSnapshot.docs.map((doc) => doc.data());
    return notesList;
};
getNotes();
```


## updateDoc

To update some of the fields without overwriting the entire document, use updateDoc().

```js
import { db } from '../utils/firestore'; // update with your path to firestore config
import { doc, updateDoc } from "firebase/firestore";

export const updateNote = async (note) => {
    const noteRef = doc(db, "notes", note.id);
    await updateDoc(noteRef, {
        description: "New description"
    });
};
updateNote(note);
```

## deleteDoc

```js

import { db } from '../utils/firestore'; // update with your path to firestore config
import { doc, deleteDoc } from "firebase/firestore";

export const deleteNote = async (note) => {
    const noteRef = doc(db, "notes", note.id);
    await deleteDoc(noteRef);
};
deleteNote(note);

```

# Firebase v9 Subcollections

What about subcollections and their documents? How do we go that deep?

Well, let’s say we have different sets of notes.

So there is a collection of sets and within that are ‘sets’ documents (like set 1, set 2, etc).

Then within each document is a collection of notes. It looks something like this:

|collection|documents (sets)|subcollections|documents (notes)|
|-|-|-|-|
|sets|set 1|notes|note 1, note 2, etc|
||set 2|notes|note 1, note 2, etc|
||set 3|notes|note 1, note 2, etc|


How do you access those documents in the subcollection (note 1, note 2, etc)?

You use getDocs, but add another parameter of the subcollection added.

So to get the notes within set 1, you could do something like:

```js

import { db } from '../utils/firestore'; // update with your path to firestore config
import { collection, getDocs } from 'firebase/firestore';
export const getSubcollections = (setId) => {
    const subcollections = await getDocs(collection(db, 'sets', setId, 'notes'));
    subcollection.forEach((doc) => {
        console.log(doc.data());
    });
}
getSubCollections('set 1')

```
Documentation Links
CRUD Documentation - Firebase CRUD Docs. (Be sure to choose version 9 in the code examples tabs and other data management functions like adding, reading, batching, compound queries, etc. can be found in the navigation to the left.)

Auth documentation - Firebase Auth Docs. (Same applies, different auth examples in the nav to the left.)