---
title: 'Stripe - Getting started with React'
date: 2020-05-26 17:33:20 +0300
description: # Add post description (optional)
img: ./credit.jpg # Add image post (optional)
tags: [Stripe, React, Payments]
---

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Stripe is a payment processor renowned for their developer experience. Using Stripe to take in credit card information is a HUGE time saver during development; it is also a great move regarding security and protecting your users. This guide will get you started on using Stripe to take payments on your React applications. I will be covering the backend setup at a later date, but for now; this is how you set up Stripe on the client side.

## Stripe Console

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;First things first, sign up for an account at https://stripe.com and verify your email address. This will give you access to your dashboard.Let's navigate to the developers section, and choose API keys to view our API keys. Save your publishiable key to your clip board, we will be using it shortly.

![Stripe API keys](./api-keys.png)

## React Configuration

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Now this is the cool stuff! Open up your terminal and install the react-stripe-checkout library with:

`npm i react-stripe-checkout`

![Install the Stripe library](./term1.png)

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;After installing the package, let's navigate to our components folder and create new component for the Stripe button that will trigger the payment modal:

![Suggested directory structure](./folder-structure.png)

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Now we need to handle our imports in the new StripeButton component. Import React and StripeCheckout with:

`import React from 'react';`

`import StripeCheckout from 'react-stripe-checkout';`

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Our StripeCheckoutButton component will be functional, and take in the price as an argument. One thing to note about Stripe, is that they look for the total amount to charge in cents. This means we will have to instantiate a new variable inside the function called priceForStripe and set it to price \* 100 if you are working with USD. We will also need to assign our publishable key we copied earlier to a variable inside this function as well. This functional component needs to return the

`<StripeCheckout />`

component we imported earlier. Your component should now look like this:

![StripeButton component 1](./stripe-button-1.png)

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;The StripeCheckout component takes in predefined props from the react-stripe-checkout. These props configure the options your Stripe modal displays. Here is a list of most of the props you can pass and what they achieve:

![Props to use on StripeCheckout](./checkout-props.png)

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;I've configured my StripeCheckout component with the following options:

`label='Pay Now'`

`name='Ecom Ltd.'`

`billingAddress`

`shippingAddress`

`image='https://svgshare.com/i/LWt.svg'`

`` description={`Your total is $${price}`} ``

`amount={priceForStripe}`

`panelLabel='Pay Now'`

`token={onToken}`

`stripeKey={publishableKey}`

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;For the token parameter, we need to make the onToken function. This onToken function will take in the token as an argument, and we will just console.log the token for now and alert that a payment was successful. The token gets returned from the Stripe API once a successful payment has gone through, you will need to pass this token to your backend to complete the processing. For now, we are just focused on getting Stripe up and running on the client side. I will have another article for the backend at a later date. Your finished StripeButton component should now look this:

![Finished StripeButton component](./stripe-button-fin.png)

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Next stop is to import this new StripeButton component into your checkout component and pass in the variable that houses your total cost that you are charging.

## What's next?

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Now that we know what Firebase authentication excels at and who is a good fit for it, my next post will be a quick overview on how we can add this to our projects. It is actually much easier to implement than you would imagine. Stay tuned!
