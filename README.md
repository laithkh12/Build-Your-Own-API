# Joke API

A simple RESTful API built with Express.js that allows users to retrieve, filter, add, update, and delete jokes. It includes endpoints for various joke-related operations and uses environment variables for secure operations.

## Features
- Retrieve a random joke
- Retrieve a specific joke by ID
- Filter jokes by type
- Add a new joke
- Update a joke (PUT and PATCH methods)
- Delete a specific joke by ID
- Delete all jokes (protected by a master key)

## Technologies Used
- Node.js
- Express.js
- Body-parser
- dotenv (for managing environment variables)

## Setup and Installation

### Prerequisites
- [Node.js](https://nodejs.org/) installed on your local machine
- [NPM](https://www.npmjs.com/), which comes with Node.js
- [dotenv](https://www.npmjs.com/package/dotenv) for environment configuration

### Installation
1. Clone the repository:
   ```bash
   git clone https://github.com/yourusername/joke-api.git
   ```
2. Change to the project directory:
   ```bash
   cd joke-api
   ```
3. Install dependencies:
   ```bash
   npm install
   ```
4. Create a `.env` file and define your `MASTER_KEY`:
   ```bash
   MASTER_KEY=your_secret_key
   ```
5. Start the server:
   ```bash
   npm start
   ```

The server will run on `http://localhost:3000`.

## Usage

### Endpoints

#### 1. Retrieve a Random Joke
- **URL:** `/random`
- **Method:** `GET`
- **Response:** Returns a random joke from the jokes array.
- **Example Request:**
   ```http
   GET http://localhost:3000/random
   ```
- **Example Response:**
   ```json
   {
     "id": 2,
     "jokeText": "Why did the scarecrow win an award? Because he was outstanding in his field.",
     "jokeType": "Puns"
   }
   ```

#### 2. Retrieve a Specific Joke by ID
- **URL:** `/jokes/:id`
- **Method:** `GET`
- **Params:**
   - `id` - The ID of the joke to retrieve
- **Example Request:**
   ```http
   GET http://localhost:3000/jokes/1
   ```
- **Example Response:**
   ```json
   {
     "id": 1,
     "jokeText": "Why don't scientists trust atoms? Because they make up everything.",
     "jokeType": "Science"
   }
   ```

#### 3. Filter Jokes by Type
- **URL:** `/filter`
- **Method:** `GET`
- **Query Parameters:**
   - `type` - The type of jokes to filter by (e.g., "Puns", "Science")
- **Example Request:**
   ```http
   GET http://localhost:3000/filter?type=Puns
   ```
- **Example Response:**
   ```json
   [
     {
       "id": 2,
       "jokeText": "Why did the scarecrow win an award? Because he was outstanding in his field.",
       "jokeType": "Puns"
     }
   ]
   ```

#### 4. Add a New Joke
- **URL:** `/jokes`
- **Method:** `POST`
- **Body Parameters:**
   - `text` - The joke text
   - `type` - The joke type (e.g., "Science", "Wordplay")
- **Example Request:**
   ```json
   POST http://localhost:3000/jokes
   Content-Type: application/json
   {
     "text": "How does a penguin build its house? Igloos it together!",
     "type": "Animals"
   }
   ```
- **Example Response:**
   ```json
   {
     "id": 51,
     "jokeText": "How does a penguin build its house? Igloos it together!",
     "jokeType": "Animals"
   }
   ```

#### 5. Update a Joke (Replace Entirely)
- **URL:** `/jokes/:id`
- **Method:** `PUT`
- **Params:**
   - `id` - The ID of the joke to update
- **Body Parameters:**
   - `text` - New joke text
   - `type` - New joke type
- **Example Request:**
   ```json
   PUT http://localhost:3000/jokes/1
   Content-Type: application/json
   {
     "text": "Why did the student eat his homework? Because his teacher said it was a piece of cake!",
     "type": "School"
   }
   ```
- **Example Response:**
   ```json
   {
     "id": 1,
     "jokeText": "Why did the student eat his homework? Because his teacher said it was a piece of cake!",
     "jokeType": "School"
   }
   ```

#### 6. Update a Joke (Partial Update)
- **URL:** `/jokes/:id`
- **Method:** `PATCH`
- **Params:**
   - `id` - The ID of the joke to partially update
- **Body Parameters:**
   - `text` - (Optional) New joke text
   - `type` - (Optional) New joke type
- **Example Request:**
   ```json
   PATCH http://localhost:3000/jokes/1
   Content-Type: application/json
   {
     "text": "Why did the chicken cross the road? To get to the other side!"
   }
   ```
- **Example Response:**
   ```json
   {
     "id": 1,
     "jokeText": "Why did the chicken cross the road? To get to the other side!",
     "jokeType": "Classic"
   }
   ```

#### 7. Delete a Specific Joke by ID
- **URL:** `/jokes/:id`
- **Method:** `DELETE`
- **Params:**
   - `id` - The ID of the joke to delete
- **Example Request:**
   ```http
   DELETE http://localhost:3000/jokes/1
   ```
- **Example Response:**
   ```json
   {
     "message": "Joke deleted successfully."
   }
   ```

#### 8. Delete All Jokes
- **URL:** `/jokes`
- **Method:** `DELETE`
- **Query Parameters:**
   - `master_key` - The master key to authenticate the request
- **Example Request:**
   ```http
   DELETE http://localhost:3000/jokes?master_key=your_secret_key
   ```
- **Example Response:**
   ```json
   {
     "message": "All jokes deleted successfully."
   }
   ```

## Contributing

Contributions are welcome! If you have suggestions or improvements, feel free to open an issue or submit a pull request.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Author

Laith Khater
