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

1. User Registration Service
    - Language: Python
    - Framework: Flask
    - Communication: REST API for easy communication with the Matching Service
2. Matching Service
    - Language: JavaScript
    - Framework: Express.JS
    - Communication: Websockets for opening chat and communication with cache.

# Design Data Management

## User Registration Service

1. Register a new user (POST /user/register)

- Input

```
    {
        "username": "igor",
        "password": "tudorloh",
        "age": "21",
        "gender": "male",
        "preferencies": "female"
    }
```

- Output

```
    {
        "message": "Account created, you may navigate through accounts"
    }
```

2. Login (POST /user/login)

- Input

```
    {
        "username": "igor",
        "password": "tudorloh"
    }
```

- Output

```
    {
        "message": "Welcome back!"
    }
```

## Matching service

1. Liked (/like/userId)

- Input

```
    {
        "like": true
    }
```

- Output

```
    {
        "message": "Both users liked, opening a chat",
        "chat_name": "username1"
    }
```


# Set up Deployment and Scaling

Both microservices will have their own docker file.

```
    # User Resgistration Service Dockerfile
    FROM node:18-alpine
    WORKDIR /app
    COPY . .
    RUN npm install 
    CMD ["node", "start"]
```

Example of Docker Compose

```
    version: '3.8'
    services: 
        user-registration-service:
            build: ./user-registration-service
            ports:
                - "3001:3001"
        matching-service:
            build: ./matching-service
            ports:
                - "3002:3002"
        redis:
            image: "redis:alpine"
```

# Implementation

Task timeouts will be implemented for both services and it will be like 10 seconds. I will implement it using the timeout parameter. Implement the Max Concurrent field to limit the number of running concurrent tasks and give it a value of 5. Gateway will be implemented in java.

# Conclusion

Overall this laboratory work seems both very interesting and challenging at the same time. There are a lot of thigs to learn from it starting from the definition of microservices finishing with deployment of a so called "dating app" in my case.