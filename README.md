## Getting Started

To get started with this project, follow these steps:

1. Clone the repository:
    ```bash
    git clone https://github.com/your-username/pedidos_farmacia.git
    ```
2. Navigate to the project directory:
    ```bash
    cd pedidos_farmacia
    ```
3. Copy the `.env.example` file to `.env`:
    ```bash
    cp .env.example .env
    ```
4. Build and start the Docker containers:
    ```bash
    docker-compose up --build -d
    ```
5. Create the database schema:
    ```bash
    docker-compose exec pgsql psql -U postgres -d postgres -c "CREATE SCHEMA pedidos_farmacia;"
    ```
6. Generate an application key:
    ```bash
    docker-compose exec pedidos_farmacia php artisan key:generate
    ```
7. Run the database migrations:
    ```bash
    docker-compose exec pedidos_farmacia php artisan migrate --seed
    ```
8. Run the database migrations:
    ```bash
    docker compose exec pedidos-farmacia bash -c "npm run dev -- --host 0.0.0.0"

    ```

You should now be able to access the application at `http://localhost`.