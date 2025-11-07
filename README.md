# Movie API (Express.js)

A simple Express.js API for browsing and searching movie and person data.

## How to Run

This project is containerized and includes a `Dockerfile` and `docker-compose.yml`.

1.  **Clone the repository.**
2.  **Run with Docker Compose:**

    ```
    # This will build the image and start the container
    docker-compose up -d

    ```

The API will be running on the port specified in your `docker-compose.yml` file (e.g., `http://localhost:3000`).

## API Key

**All requests** to the API require a valid API key sent as a query parameter.

Key: api_key

Value: 123456789

Example:

http://localhost:3000/movie/top_rated?api_key=123456789

Requests without this key will receive a `401 Invalid API Key` response.

## API Endpoints

### Root (`/`)

- `GET /`: Welcome route.
- `GET /most_popular`: Get a paginated list of the most popular movies.
  - Query: `page` (optional, default: 1)

### Movie (`/movie`)

- `GET /top_rated`: Get a paginated list of top-rated movies.
  - Query: `page` (optional, default: 1)

- `GET /:movieId`: Get details for a specific movie by its ID.
- `POST /:movieId/rating`: Submit a rating for a movie. (Requires JSON body)
- `DELETE /:movieId/rating`: Delete a rating for a movie.

### Search (`/search`)

_Note: All search routes require a `query` parameter._

- `GET /movie`: Search movies by title or overview.
  - Query: `query` (required)

- `GET /person`: Search people by name.
  - Query: `query` (required)
