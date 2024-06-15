# GoTinyURL

GoTinyURL is a URL shortening service that allows users to create short URLs from long ones and manage their links efficiently.

## Table of Contents
- [Features](#features)
- [Backend](#backend)
- [Client](#client)
- [API Endpoints](#api-endpoints)
- [Setup](#setup)
- [Usage](#usage)
- [Contributing](#contributing)

## Features
- Generate short URLs from long URLs
- Store URL mappings in PostgreSQL
- Cache URL mappings in Redis
- SwiftUI client app with local storage using CoreData
- View past shortened links on the client

## Backend
1. **Redis**: Used for caching URL mappings.
2. **PostgreSQL**: Used for storing URL mappings persistently.

## Client
1. **SwiftUI**: Used for building the iOS app.
2. **CoreData**: Used for storing URL mappings locally on the client side.

## API Endpoints

### Create Short URL
- **Endpoint**: `/create-short-url`
- **Method**: `POST`
- **Description**: Validates and creates a short URL from the provided long URL and user ID.
- **Sample Request**:
    ```sh
    curl --location --request POST 'http://localhost:9098/create-short-url' \
    --header 'Content-Type: text/plain' \
    --data-raw '{
        "long_url": "https://amazon.com",
        "user_id" : "e0dba740-fc4b-497872c-d360239e"
    }'
    ```
- **Sample Response** (200 Status Code):
    ```json
    {
        "message": "Short URL created successfully",
        "short_url": "http://localhost:9098/re/SwwSgzBe"
    }
    ```

### Redirect to Long URL
- **Endpoint**: `/re/:shortUrl`
- **Method**: `GET`
- **Description**: Redirects to the original long URL based on the short URL mapping present in the database or cache.

## Setup
1. Clone the repository:
    ```sh
    git clone https://github.com/drk-knght/GoTinyURL.git
    cd GoTinyURL
    ```
2. Set up PostgreSQL and Redis servers.
3. Update the configuration files with your database credentials.
4. Run the backend server:
    ```sh
    go run main.go
    ```

## Usage
- Use the provided API endpoints to create and manage short URLs.
- Use the SwiftUI client app to interact with the service and view your shortened URLs.

## Contributing
We welcome contributions! Please fork the repository and submit pull requests.

