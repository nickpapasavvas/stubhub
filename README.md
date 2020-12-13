# Ticketing app

### Features

1. Users can list a ticket for an event (content, sports) for sale or buy a ticket
2. When a user attempts to purchase a ticket, the ticket is 'locked' for 15 minutes. 
The user has 15 minutes to enter their payment info
3. While locked no other user can purchase the ticket. After 15 minutes, the ticket 'unlocks'
4. Ticket prices can be edited if they are not locked.
5. Production grade authentication (explain in detail)
6. Integration with Stripe for payments

### Data model

The data model is being depicted in the following image: 

### Services:

1. auth
2. tickets: Handles ticket creation / editing: Knows whether a ticket can be updated
3. orders:  Order creation/editing
4. expiration: Watches for orders to be created and cancels them after 15 minutes
5. payments: Handles credit card payments. Cancels orders if a payment fails, completes if payment succeeds

An alternative feature-based design would be better.

### Events

User Created , User Updated
Order Created, Order Cancelled, Order Expired
Ticket Created, Ticket Updated
ChargeCreated

### Architecture:

The general architecture is depicted in the following image:


### Technology overview

Typescript, React, Next.js, Node, Mongo, NATS Streaming Service

#### Routes

##### Auth Service

| Route                  | Method       | Body                             |
| :-------------         | :----------: | -------------------------------: |
| api/users/signup       | POST         | {email:string, password: string} |
| api/users/signin       | POST         | {email:string, password: string} |
| api/users/signout      | POST         |                0                 |
| api/users/currentuser  | GET          |                -                 |