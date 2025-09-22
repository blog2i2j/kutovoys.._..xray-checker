---
title: Переменные окружения
description: Переменные окружения для Xray Checker
---

## Subscription

### SUBSCRIPTION_URL

- CLI: `--subscription-url`
- Обязательно: Да
- По умолчанию: Нет

URL, строка Base64 или путь к файлу для конфигурации прокси. Поддерживает несколько форматов:

- HTTP/HTTPS URL с Base64-кодированным содержимым
- Прямая Base64-кодированная строка
- Локальный путь к файлу с префиксом `file://`
- Локальный путь к папке с префиксом `folder://`

### SUBSCRIPTION_UPDATE

- CLI: `--subscription-update`
- Обязательно: Нет
- По умолчанию: `true`

Включает автоматическое обновление конфигурации прокси из источника подписки. При включении Xray Checker будет периодически проверять изменения и обновлять конфигурации соответственно.

### SUBSCRIPTION_UPDATE_INTERVAL

- CLI: `--subscription-update-interval`
- Обязательно: Нет
- По умолчанию: `300`

Время в секундах между проверками обновлений подписки. Используется только когда включен `SUBSCRIPTION_UPDATE`.

## Proxy

### PROXY_CHECK_INTERVAL

- CLI: `--proxy-check-interval`
- Обязательно: Нет
- По умолчанию: `300`

Время в секундах между проверками доступности прокси. Каждая проверка верифицирует все настроенные прокси.

### PROXY_CHECK_METHOD

- CLI: `--proxy-check-method`
- Обязательно: Нет
- По умолчанию: `ip`
- Значения: `ip`, `status`, `download`

Метод, используемый для проверки функциональности прокси:

- `ip`: Сравнивает IP-адреса с прокси и без него
- `status`: Проверяет HTTP-код состояния тестового запроса
- `download`: Скачивает файл через прокси для проверки функциональности

### PROXY_IP_CHECK_URL

- CLI: `--proxy-ip-check-url`
- Обязательно: Нет
- По умолчанию: `https://api.ipify.org?format=text`

URL, используемый для проверки IP при `PROXY_CHECK_METHOD=ip`. Должен возвращать текущий IP-адрес в текстовом формате.

### PROXY_STATUS_CHECK_URL

- CLI: `--proxy-status-check-url`
- Обязательно: Нет
- По умолчанию: `http://cp.cloudflare.com/generate_204`

URL, используемый для проверки статуса при `PROXY_CHECK_METHOD=status`. Должен возвращать HTTP-код 204/200.

### PROXY_DOWNLOAD_URL

- CLI: `--proxy-download-url`
- Обязательно: Нет
- По умолчанию: `https://proof.ovh.net/files/1Mb.dat`

URL файла для скачивания при `PROXY_CHECK_METHOD=download`. Файл будет скачан через прокси для проверки функциональности.

### PROXY_DOWNLOAD_TIMEOUT

- CLI: `--proxy-download-timeout`
- Обязательно: Нет
- По умолчанию: `60`

Максимальное время в секундах ожидания завершения скачивания файла при использовании `PROXY_CHECK_METHOD=download`.

### PROXY_DOWNLOAD_MIN_SIZE

- CLI: `--proxy-download-min-size`
- Обязательно: Нет
- По умолчанию: `51200`

Минимальное количество байт для успешной проверки при использовании `PROXY_CHECK_METHOD=download`. По умолчанию 50KB.

### PROXY_TIMEOUT

- CLI: `--proxy-timeout`
- Обязательно: Нет
- По умолчанию: `30`

Максимальное время в секундах ожидания ответа прокси во время проверок.

### SIMULATE_LATENCY

- CLI: `--simulate-latency`
- Обязательно: Нет
- По умолчанию: `true`

Добавляет измеренную задержку в ответы эндпоинтов, полезно для систем мониторинга.

## Xray

### XRAY_START_PORT

- CLI: `--xray-start-port`
- Обязательно: Нет
- По умолчанию: `10000`

Начальный номер порта для SOCKS5 прокси. Каждый прокси будет использовать последовательные порты, начиная с этого номера.

### XRAY_LOG_LEVEL

- CLI: `--xray-log-level`
- Обязательно: Нет
- По умолчанию: `none`
- Значения: `debug`, `info`, `warning`, `error`, `none`

Управляет уровнем детализации логирования Xray Core.

## Metrics

### METRICS_HOST

- CLI: `--metrics-host`
- Обязательно: Нет
- По умолчанию: `0.0.0.0`

Адрес для эндпоинтов метрик и статуса.

### METRICS_PORT

- CLI: `--metrics-port`
- Обязательно: Нет
- По умолчанию: `2112`

Номер порта для HTTP-сервера, предоставляющего эндпоинты метрик и статуса.

### METRICS_PROTECTED

- CLI: `--metrics-protected`
- Обязательно: Нет
- По умолчанию: `false`

Включает базовую аутентификацию для эндпоинтов метрик и статуса.

### METRICS_USERNAME

- CLI: `--metrics-username`
- Обязательно: Нет
- По умолчанию: `metricsUser`

Имя пользователя для базовой аутентификации при `METRICS_PROTECTED=true`.

### METRICS_PASSWORD

- CLI: `--metrics-password`
- Обязательно: Нет
- По умолчанию: `MetricsVeryHardPassword`

Пароль для базовой аутентификации при `METRICS_PROTECTED=true`.

### METRICS_INSTANCE

- CLI: `--metrics-instance`
- Обязательно: Нет
- По умолчанию: Нет

Метка экземпляра, добавляемая ко всем метрикам. Полезно для различения нескольких экземпляров Xray Checker.

### METRICS_PUSH_URL

- CLI: `--metrics-push-url`
- Обязательно: Нет
- По умолчанию: Нет

URL Prometheus Pushgateway для отправки метрик. Формат: `https://user:pass@host:port`

### METRICS_BASE_PATH

- CLI: `--metrics-base-path`
- Обязательно: Нет
- По умолчанию: ""

URL-путь, по которому будут доступны метрики и страница для их мониторинга. Формат: `/vpn/metrics`. Мониторинг будет доступен по адресу `http://localhost:port/metrics-base-path`

## Other

### RUN_ONCE

- CLI: `--run-once`
- Обязательно: Нет
- По умолчанию: `false`

Выполняет один цикл проверки и завершает работу. Полезно для сред с запланированным выполнением.
