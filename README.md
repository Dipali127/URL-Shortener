# URL Shortener API

A URL Shortener application is a Node.js-based system developed using the Express.js framework, with MongoDB as the chosen database.

A URL shortener application typically involves creating a service that takes long URLs and converts them into shorter, more manageable links. These shortened links redirect users to the original long URL when clicked. The primary purpose of a URL shortener is to make links more concise and easier to share, particularly on platforms like social media where character limits may be a concern. Additionally, the application tracks the number of hits on each shortened URL with a click counter.

## url Model
urlModel stores information about the URLs, including their long and shortened versions, associated unique identifiers (short codes), and tracking the number of clicks.

* **Fields:**

    `longURL`: `String` (Represents the long URL provided by the user).

   `shortCode`: `String` (Represents the unique identifier for the shortened URL. this field must be unique).

  `urlClickcount`: `Number` (Represents the total number of clicks on the shortened URL. default value is 0).

## Endpoints

### URL

- **Generate a short URL**

  - **Endpoint:** `POST /generateShorturl`
  - **Description:** Generates a short URL from the provided long URL and saves it in the database with the fields `longURL`, `shortCode`, and `urlClickcount`. Returns the shortened URL.

- **Redirect to the long URL associated with a short URL**

  - **Endpoint:** `GET /:shortCode`
  - **Description:** Redirects the user to the long URL associated with the provided short URL. Increments the click count for the short URL.

- **Track the total number of clicks on a short URL**

  - **Endpoint:** `GET /clickCount/:shortCode`
  - **Description:** Returns the total number of clicks for the provided short URL.

- **Track clicks based on the entered short URL**

  - **Endpoint:** `POST /trackClicks`
  - **Description:** Accepts a short URL in the request body and returns the total number of clicks associated with it.

- **Examples:**
````json
{
  "longURL": "https://en.wikipedia.org/wiki/Withdrawal_of_Joe_Biden_from_the_2024_United_States_presidential",
  "shortCode": "FK60DbIk",
  "urlClickcount": 1
}
````

## Postman Collection

You can explore and test all the API endpoints of this URL Shortener application using Postman.

[![Run in Postman](https://run.pstmn.io/button.svg)](https://bit.ly/4oGw6Qy)


## Running URL Shortener Application

To run the `urlShortener` application, follow these steps:

1. **Ensure that you have Node.js and npm installed on your system.**

2. **Clone the repository to your local machine:**

    ```bash
    git clone -b feature/url-shortening https://github.com/Dipali127/URL_shortener.git
    ```

3. **Navigate to the root directory of the project:**

    ```bash
    cd URL_shortener
    ```

4. **Install dependencies:**

    ```bash
    npm install
    ```

5. **Set up any necessary environment variables or configuration files.**

6. **Start the application:**

    ```bash
    npm start
    ```

### Backend Setup

Before starting the application, ensure that you have set up the following:

- **Environment Variables:**
    - Create a new file named `.env` in the root directory of the project.
    - Set the following required environment variables in the `.env` file:
        - `PORT`: Set this variable to the desired port number. By default, the application listens on port 3000.
        - `DATABASE_CLUSTER_STRING`: Set this variable to the connection string for your MongoDB database cluster.
        - `BASE_URL`: Set this variable to the base URL of your application. For creating short URLs, you can set it to `http://localhost:3000`.
        - `REDIS_HOST`: Set this variable to the hostname of your Redis server (e.g., `localhost`).
        - `REDIS_PORT`: Set this variable to the port number Redis is listening on (default is `6379`).

- **Database Setup:**
    - Install Redis for fast retrieval of data. You can download and install Redis from the [official Redis website](https://redis.io/download).
    - Install Mongoose, the MongoDB object modeling tool for Node.js, by running the following command in your terminal:

    ```bash
    npm install mongoose
    ```

By following these steps and ensuring that the necessary configurations are in place in your `.env` file, you should be able to run the `urlShortener` application successfully.

## Tech Stack

- **Server:** Node.js, Express.js
- **Package for Unique Short Codes:** [nanoid](https://www.npmjs.com/package/nanoid)
- **Development Server Monitor:** [nodemon](https://www.npmjs.com/package/nodemon)
- **Environment Variables Management:** [dotenv](https://www.npmjs.com/package/dotenv)

## Helpful Links

[Visit this link to create short unique code using “nanoid” package](https://github.com/ai/nanoid?tab=readme-ov-file#readme)

[Visit this link to know more about long URL](https://medium.com/@hemant.ramphul/the-stucture-of-an-url-c59a6ccf7184)

