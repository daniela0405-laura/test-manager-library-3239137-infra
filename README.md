# test-manager-library-3239137-infra

Contenedores, red, volumen y motor de base de datos de Manager Library.

## Qué levanta

- `db`: PostgreSQL 16 (motor de referencia del data-model), en UTC.
- Red `library-net` y volumen `db_data`.
- La base arranca vacía: las tablas las crean las migraciones de la API.

## Cómo levantarlo (un solo comando, RNF-5)

    docker compose up -d

La base queda en `localhost:5434` (base `library`, usuario `library`).

## Luego, en la API

    php artisan migrate
    php artisan app:ensure-admin
    php artisan serve