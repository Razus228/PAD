# Online Dating App Platform

The app enables users with opposite or same gender to chat the main purpose being dating. There are features like user registration that makes easier access for those who use the app frequently, matching system, that makes finding the right person easier, a chat that is started if both parties liked each other. The Websockets are integrated to make easier access to chat and allow both services (User Registration and Matching) to work separately.

# Assess Application Suitability

1. Easy Availability
    - If a service fails, the other one won't be affected by it. In my application, if the `User Registration` service fails, the `Matching` service will be available for use.
2. Easy Communication
    - There can be more chats open at the same time.
3. Scalability
    - Real-time communication is easier by using microservices, and components such as User Registration and Matching System can scale by themselves, depending on the demand.

# Service Boundaries

1. User Registration Service - Manages the basic user registration to the app. There is also a login feature implemented once the user has created an account and wants to enter the app.
2. Matching Service - Manages the like and dislike feature that exists in Tinder. Also, if both users gave a positive answer, then a chat is opened for further discussion.

Check the diagram below for easier clarification.

![The diagram](/Diagram.png)

# Technology Stack and Communication Patterns

