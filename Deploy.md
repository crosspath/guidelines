# Подготовка к выкладке кода на сервер

Пример для Kamal, GitHub и Sentry:

1. Запустить автотесты.
2. Создать резервную копию БД.
3. Проверить возможность отката версии кода на `production`-сервере:
  - см. `tag` в столбце `IMAGE` после двоеточия: `kamal app containers -q -d production`
    например, `ghcr.io/username/repo:030816942405cb833edbdc433f3c031b8e4ed469`
  - `kamal rollback -d production %{tag}`
4. `kamal deploy -d production` (или через GitHub Actions).
5. Проверить статус серверного приложения при работе с админкой и мобильными приложениями.
6. `kamal shell -d production` + `bin/rails db:migrate`
7. Проверить список ошибок в Sentry.
8. Проверить нагрузку сервера через `htop`.
9. Проверить логи веб-сервера и приложения: `kamal logs -d production -f`
