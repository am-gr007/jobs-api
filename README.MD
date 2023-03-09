#### Setup

```bash
npm install && npm start
```

#### Database Connection

1. Import connect.js
2. Invoke in start()
3. Setup .env in the root
4. Add MONGO_URI with correct value

#### Routers

- auth.js
- jobs.js

#### User Model

Email Validation Regex

```regex
/^(([^<>()[\]\\.,;:\s@"]+(\.[^<>()[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/
```

#### Register User

- Validate - name, email, password - with Mongoose (using validators in Mongoose Schema)
- Hash Password (with bcryptjs) - can be optimized by hashing the passwords before saving the mongoose document using mongoose pre middleware.
- Save User 
- Generate Token - use jsonwebtoken package and can be optimised using mongoose's document instance methods to create JWT tokens
- Send Response with Token

#### Login User

- Validate - email, password - in controller
- If email or password is missing, throw BadRequestError
- Find User
- Compare Passwords
- If no user or password does not match, throw UnauthenticatedError
- If correct, generate Token
- Send Response with Token

#### Regarding Jobs Model

- create a Job Model to instantiate and create related mongoose documents
- In JobSchema an entity should connect current Job model to the created User model
- add the authentication token from login and register request to our postman model dynamically
- 

#### Mongoose Errors

- Validation Errors - look in errorHandlerMiddleware
- Duplicate (Email) - look in errorHandlerMiddleware
- Cast Error - look into errorHandlerMiddleware

#### Security

- helmet
- cors
- xss-clean
- express-rate-limit

Swagger UI

```yaml
/jobs/{id}:
  parameters:
    - in: path
      name: id
      schema:
        type: string
      required: true
      description: the job id
```
