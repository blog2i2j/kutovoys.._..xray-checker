---
title: Возможности
description: Возможности Xray Checker
tableOfContents: false
---

### 🚀 Основные возможности

- 🔍 Мониторинг работоспособности Xray-прокси серверов с поддержкой различных протоколов (VLESS, VMess, Trojan, Shadowsocks)

- 🔄 Автоматическое обновление конфигурации прокси из подписки (subscription) с [настраиваемым интервалом](/ru/configuration/envs#subscription_update_interval)

- 📊 [Экспорт метрик](/ru/integrations/metrics) в формате Prometheus с информацией о статусе и задержках прокси-серверов

- 🌓 Веб-интерфейс с темной/светлой темой для мониторинга состояния всех прокси-endpoint'ов

### 📝 Форматы и конфигурация

- 📋 [Поддержка различных форматов конфигурации](/ru/configuration/subscription):

  - 🔗 URL-подписки
  - 🔐 Base64-encoded строки
  - 📄 JSON-файлы

### 🔌 Интеграции

- 📥 [Автоматическая генерация endpoint'ов](/ru/integrations/uptime-kuma) для интеграции с системами мониторинга (например, Uptime-Kuma)

- ⏱️ [Симуляция задержек](/ru/configuration/advanced-conf) для endpoint'ов для для правильного отображения в системах мониторинга

- 📡 [Интеграция с Prometheus Pushgateway](/ru/integrations/prometheus#интеграция-с-pushgateway) для отправки метрик во внешние системы мониторинга

### ⚡ Методы проверки

- 🔧 [Поддержка трех методов проверки прокси](/ru/configuration/check-methods):
  - 🌐 Через сравнение IP-адресов
  - ✅ Через проверку HTTP-статусов
  - 📥 Через тестирование скачивания файлов

### 🔒 Безопасность

- 🛡️ [Защита метрик и веб-интерфейса](/ru/configuration/advanced-conf#настройка-безопасности) с помощью Basic Authentication

### 🤖 Развертывание

- 🐳 Возможность запуска как в [Docker-контейнере](/ru/usage/docker) (включая Docker Compose), так и в режиме [standalone CLI-приложения](/ru/usage/cli)

:::tip[💡 Быстрый старт]
Чтобы начать использовать Xray Checker прямо сейчас, перейдите в раздел [Быстрый старт](/ru/intro/quick-start)
:::
