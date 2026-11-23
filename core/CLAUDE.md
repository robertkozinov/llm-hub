# core — ядро-шлюз и CLI на Go

Модуль `github.com/robertkozinov/llm-hub/core`. Все команды Go запускаются из папки `core/`.

## Правила кода
- Зависимости — только из ADR 7 (`docs/adr/0007-stack-and-testing.md`). SDK провайдеров и langchaingo не подключаем.
- HTTP — стандартный `net/http`; шлюз слушает только `127.0.0.1`, CORS не открываем.
- Ошибки API — в формате OpenAI (ADR 3), тексты ошибок API на английском. Сообщения CLI — на русском.
- Неизвестные поля запросов и ответов не теряем (ADR 2).

## Команды
- Все тесты: `go test -race ./...`
- Перезаписать golden-файлы: `go test ./... -update`, затем прочитать изменения глазами.
- Живые тесты с настоящими ключами: `go test -tags live ./...` (нужен `LLMHUB_LIVE_CONFIG`).
- Сборка: `go build -o llmhub ./cmd/llmhub`
