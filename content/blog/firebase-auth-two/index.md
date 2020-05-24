---
title: 'Authentication with Firebase - How!'
date: 2020-05-24 13:08:20 +0300
description: # Add post description (optional)
img: ./registration.jpg # Add image post (optional)
tags: [Firebase, Authentication, Security]
---

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;In my last post we talked about why you would want to use firebase to handle your app's authentication, and in this post we will dig into how. This is meant to give you quick overview on how to get started, not a full guide. We will be talking in the context of a Node.js / React project environment.

## The Firebase Console

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;First we will need to visit the Firebase console. If you do not already have a google account, you will need to create one and sign in. Once you have an account and have logged in, you should be able to navigate to the admin console at https://console.firebase.google.com

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Once you are in the conosle, we will want to create a project and run through the project creation wizard:

![Create your project](./create-project.jpg)

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Now that we have our Firebase project created, let's navigate to the authentication area, and look at the sign-in methods:

![Various sign-in providers](./providers.jpg)

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;As you can see, we have multiple sign-in providers to choose from! This is probably my favorite feature of Firebase thus far. The ability to EASILY integrate sign-in's with accounts a user already has. This greatly reduces the barrier of entry to our applications. We want to make it as easy as possible for users to able to use our application, and this is a great way to eliminate a tedious and lengthy registration form.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Let's enable the Google sign in provider, then navigate to our project's home dashboard and register our web app with firebase:

![Register our web app with Firebase](./reg1.jpg)

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;After registration, you'll be provided with a code snippet that we will need to use to configure our web application. All we need from this snippet is the object assigned to the variable 'firebaseConfig':

![Save the config object for later use](./reg2.png)

## Installing The SDK

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Now that we have Firebase configured on the console side, we are ready to install the SDK. Installing the SDK gives us new methods to use in our application that allow us make specific calls to our new Firebase project. Open up our terminal and navigate to the projects root directory, and run the command:

`npm i firebase`

![Install the Firebase SDK via node package manager](./term1.png)

We are assuming you have Node.js installed in your dev environment.

## The Code - Firebase Utility

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;In our React project, let's navigate to the src folder and create a new folder for firebase. In that folder, we will create a new JavaScript file called firebase.utils.js to house our firebase config settings.

![Firebase config folder structure](./utils.png)

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Now let's dive into connecting our app to Firebase. Import the following from the Firebase SDK into our newly created utility file:

`import firebase from 'firebase/app';`

`import 'firebase/auth';`

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;The above imports allow us to use specific methods provided by Firebase for configuring our application. Remember the config object we set aside for later? Now here is where it comes into play. We will create a new object called config with this data in it. It should look like the following:

![Config object](./config.png)

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Now let's initialize our app by passing in the config object and calling the following method:

`firebase.initializeApp(config);`

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Next let's export the following method as the variable auth so we call this method as we need it through out our application:

`export const auth = firebase.auth();`

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;We can now configure a couple of options specific to the google sign-in provider we have enabled. We will want to create a variable called provider and set it with the following:

`const provider = new firebase.auth.GoogleAuthProvider();`

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;With this new variable, we can now chain on some cutom parameters to the provider with the .setCustomParameters() method. We will enforce the google sign-in pop up for account selection everytime we call the user to sign-in with google:

`provider.setCustomParameters({ prompt: 'select_account' });`

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;To wrap up the utility file, we will now create and export a signInWithGoogle function passing in the provider we have just created, and then export firebase for later use throughout our application:

`export const signInWithGoogle = () => auth.signInWithPopup(provider);`

`export default firebase;`

![signInWithGoogle function](./utils2.png)

## The Code - Sign-in component

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Now we just need to bring in our newly created signInWithGoogle function to whatever component you are using to handle sign-ins. In your sign-in component, import signInWithGoogle from firebase. Which, depending on your projects folder structure; should look close to:

`import { signInWithGoogle } from '../../firebase/firebase.utils'`

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;The last step is to now add an onClick listener to your button component that you wish to use for triggering the sign in with Google pop-up.

![onClick function](./onClick.png)

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Congratulations! You have now set up authentication with Google's sign-in provider. Clicking your button will now trigger the pop-up and allow users to authenticate with your app by using their existing Google account:

![Success!](./popup.png)

## Quick Wrap Up

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;This guide was only meant to get you started with using third-party authentication. I wanted to show just how easy it is to integrate this feature into your future applications. In order to fully leverage this feature in your app, you will need to think about assigning the Google user auth object that gets returned on sign-in to your applications state. How you choose to handle this will vary wildly depending on your projects scope and needs. This is why I did not go further with this tutorial. I'll point you towards the official Firebase documentation if you wish to learn more and take this further.

https://firebase.google.com/docs

## What's next?

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;My next article will be on how to integrate Stripe's API into your applications so you can securely accept credit card payments. Who doesn't want to monetize their projects???

Stay tuned!
