# url-shortener

Простой сервис сокращения ссылок на Go

## Структура проекта

- `cmd/url-shortener/` — точка входа (main.go)
- `internal/config/` — работа с конфигом
- `config/local.yaml` — пример конфига
- `go.mod`, `go.sum` — зависимости

## Быстрый старт

1. **Установите зависимости:**
   ```bash
   go mod tidy
   ```
2. **Запуск локально:**
   Из корня проекта:
   ```bash
   go run ./cmd/url-shortener/
   ```
   По умолчанию будет использоваться конфиг `config/local.yaml`.

3. **Передача конфига:**
   Можно указать путь к конфигу через флаг:
   ```bash
   go run ./cmd/url-shortener/ -config=config/local.yaml
   ```

## Переменные окружения

- Можно использовать переменную окружения `CONFIG_PATH` для указания пути к конфигу (если не задан флаг `-config`).

## Docker/Kubernetes

- Для Docker/K8s удобно пробрасывать переменные окружения или монтировать конфиг как volume.
- Пример Dockerfile и манифесты можно добавить по запросу.

## Пример config/local.yaml
```yaml
env: "local"
storage_path: "./storage/storage.db"
http_server:
  address: "localhost:8082"
  timeout: 4s
  idle_timeout: 60s
```

## TODO
- Логгер
- Хранилище (sqlite)
- HTTP router (chi)
- Запуск сервера 