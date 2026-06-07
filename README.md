# API Estudiantes GraphQL

> Proyecto personal de [itamar6531](https://github.com/itamar6531)

## Acerca del proyecto

Este repositorio es una **API backend** para administrar información de estudiantes usando **GraphQL** en lugar de endpoints REST tradicionales. Está construido con Laravel y permite consultar, crear, actualizar y eliminar registros de estudiantes a través de un único endpoint (`/graphql`), donde el cliente define exactamente qué datos necesita en cada petición.

El objetivo del proyecto es practicar el diseño de esquemas GraphQL, el uso de queries y mutations, y su integración con Eloquent y migraciones de Laravel. Es un proyecto de aprendizaje y portafolio, pensado para explorar cómo GraphQL simplifica la comunicación entre frontend y backend al evitar el sobre-fetching y el under-fetching de datos.

## Características

- API GraphQL con [rebing/graphql-laravel](https://github.com/rebing/graphql-laravel)
- Framework [Laravel 12](https://laravel.com) sobre PHP 8.2+
- Base de datos SQLite por defecto (configurable a MySQL/PostgreSQL)
- Migraciones y seeders de Laravel
- Tests con [Pest](https://pestphp.com)

## Stack tecnológico

| Tecnología | Versión |
|------------|---------|
| PHP | ^8.2 |
| Laravel | ^12.0 |
| GraphQL (rebing/graphql-laravel) | ^9.10 |
| Base de datos | SQLite (por defecto) |

## Requisitos previos

- PHP >= 8.2 con extensiones: `mbstring`, `openssl`, `pdo`, `tokenizer`, `xml`, `ctype`, `json`, `bcmath`
- [Composer](https://getcomposer.org/)
- Node.js y npm (opcional, para assets frontend)

## Instalación

1. Clona el repositorio:

```bash
git clone https://github.com/itamar6531/api-estudiantes-graphql.git
cd api-estudiantes-graphql
```

2. Instala las dependencias de PHP:

```bash
composer install
```

3. Copia el archivo de entorno y genera la clave de la aplicación:

```bash
cp .env.example .env
php artisan key:generate
```

4. Crea la base de datos SQLite y ejecuta las migraciones:

```bash
touch database/database.sqlite
php artisan migrate
```

5. (Opcional) Instala dependencias frontend y compila assets:

```bash
npm install
npm run build
```

## Configuración

Las variables principales se definen en `.env`:

```env
APP_NAME="API Estudiantes GraphQL"
APP_URL=http://localhost:8000

DB_CONNECTION=sqlite
# DB_DATABASE se resuelve automáticamente a database/database.sqlite
```

Para usar MySQL u otro motor, modifica `DB_CONNECTION`, `DB_HOST`, `DB_DATABASE`, `DB_USERNAME` y `DB_PASSWORD` en `.env`.

## Ejecución

Inicia el servidor de desarrollo:

```bash
php artisan serve
```

La aplicación estará disponible en `http://localhost:8000`.

### Endpoint GraphQL

| Método | URL |
|--------|-----|
| GET / POST | `http://localhost:8000/graphql` |

Ejemplo de consulta con `curl`:

```bash
curl -X POST http://localhost:8000/graphql \
  -H "Content-Type: application/json" \
  -d '{"query": "{ __schema { queryType { name } } }"}'
```

Puedes probar consultas de forma interactiva con herramientas como [GraphiQL](https://github.com/graphql/graphiql) o [Altair GraphQL Client](https://altairgraphql.dev/).

## Estructura del proyecto

```
app/
├── GraphQL/
│   ├── Queries/      # Consultas GraphQL
│   ├── Mutations/    # Mutaciones GraphQL
│   └── Types/        # Tipos del esquema
├── Models/           # Modelos Eloquent
database/
├── migrations/       # Migraciones de base de datos
└── seeders/          # Datos de prueba
config/
└── graphql.php       # Configuración del esquema GraphQL
```

## Tests

```bash
composer test
# o
php artisan test
```

## Roadmap

- [ ] Modelo y migración de `Estudiante`
- [ ] Tipo GraphQL `Estudiante`
- [ ] Queries: listar y obtener estudiante por ID
- [ ] Mutations: crear, actualizar y eliminar estudiante
- [ ] Seeders con datos de ejemplo
- [ ] Tests de integración GraphQL

## Licencia

Este proyecto es de código abierto bajo la licencia [MIT](https://opensource.org/licenses/MIT).
