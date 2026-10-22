# Deploy to Vercel with Supabase

This project runs Laravel in a Vercel container. Import the `warjay590` GitHub repository with project name `warjay590`, root directory `./`, and framework preset `Other`.

## Vercel environment variables

Add these to Production (and Preview if needed). Do not commit secret values.

| Variable | Value |
| --- | --- |
| `APP_ENV` | `production` |
| `APP_DEBUG` | `false` |
| `APP_KEY` | Generate with `php artisan key:generate --show` and add the output in Vercel |
| `APP_URL` | The production URL assigned by Vercel |
| `LOG_CHANNEL` | `stderr` |
| `DB_CONNECTION` | `pgsql` |
| `DB_HOST` | Supabase Session Pooler host from the project's **Connect** panel |
| `DB_PORT` | `5432` |
| `DB_DATABASE` | `postgres` (or the database name shown by Supabase) |
| `DB_USERNAME` | The Session Pooler username shown by Supabase |
| `DB_PASSWORD` | The Supabase database password |
| `DB_SSLMODE` | `require` |
| `SESSION_DRIVER` | `database` |
| `CACHE_STORE` | `database` |
| `QUEUE_CONNECTION` | `sync` |

Copy the exact Session Pooler host and username from the Supabase project's Connect panel. Supabase recommends Session Pooler for Laravel and SSL with `sslmode=require`.

## Database migrations

Run `php artisan migrate --force` as a separate release step after setting the database variables. Do not run migrations when the container starts. Use a fresh Supabase database or back it up before migrating an existing one.

The Vercel container filesystem is not durable. Keep uploaded files in external storage if the app starts storing them.
