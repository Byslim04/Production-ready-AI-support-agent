# 🚀 Production-Ready AI Customer Support Agent

Автономный агент службы поддержки интернет-магазина корпоративного уровня с поддержкой RAG, интеграцией CRM-API и системой безопасной обработки ошибок.

## 📋 Оглавление
1. [Бизнес-проблема](#1-бизнес-проблема)
2. [Архитектура](#2-архитектура)
3. [Используемые API и сервисы](#3-используемые-api-и-сервисы)
4. [Устройство RAG](#4-устройство-rag)
5. [Инструменты агента (Tools)](#5-инструменты-агента-tools)
6. [Обработка ошибок](#6-обработка-ошибок)
7. [Безопасность и среды (Environments)](#7-безопасность-и-среды-environments)
8. [Мониторинг и метрики](#8-мониторинг-и-метрики)
9. [План запуска (Pre-Production Checklist)](#9-план-запуска-pre-production-checklist)

---

### 1. Бизнес-проблема
Компания теряет много времени на ответы на рутинные вопросы клиентов («Где мой заказ?», «Как вернуть товар?», «Сколько идет доставка?»). Агент автоматизирует до 80% типовых запросов 24/7.

### 2. Архитектура
Система разделена на слои: Chat Trigger ➔ AI Agent Router ➔ Tools (RAG / CRM API) ➔ Guardrails & Verification ➔ Final Response.

### 3. Используемые API и сервисы
* OpenAI / Groq LLM API (для обработки естественного языка).
* Интернет-магазин CRM API (для проверки статусов заказов по order_id).

### 4. Устройство RAG
Использует векторный поиск по локальной базе знаний в папке knowledge_base/ (политики доставки, возврата, оплаты, гарантий). Фактические данные извлекаются из документов без галлюцинаций модели.

### 5. Какие инструменты доступны агенту
* Search Knowledge Base — поиск регламентов компании.
* Get Order Status — получение статуса заказа по ID из CRM.

### 6. Как обрабатываются ошибки
* Автоматический перехват падений внешних API (OpenAI / CRM).
* Выдача вежливых альтернативных ответов при отсутствии данных или сбоях связи.

### 7. Как организовано тестирование
Проект разделен на среды: Development (локально с мок-данными), Staging (тестовый контур с песочницей API) и Production (боевой сервер). Секреты хранятся в защищенных переменных окружения.

### 8. Какие меры безопасности реализованы
* Principle of Least Privilege: Токен CRM имеет права только на чтение (Read-Only).
* Запрет на передачу чужих персональных данных и строгая фильтрация секретов.

### 9. Как контролируются расходы
Мониторинг токенов на запрос, ограничение максимальной длины контекста и кэширование частых ответов базы знаний.





----------






# 🚀 Production-Ready AI Customer Support Agent

An enterprise-grade autonomous customer support agent for online stores featuring RAG support, CRM-API integration, and a secure error-handling system.

## 📋 Table of Contents
1. [Business Problem](#1-business-problem)
2. [Architecture](#2-architecture)
3. [APIs and Services Used](#3-apis-and-services-used)
4. [RAG Implementation](#4-rag-implementation)
5. [Agent Tools](#5-agent-tools)
6. [Error Handling](#6-error-handling)
7. [Security and Environments](#7-security-and-environments)
8. [Monitoring and Metrics](#8-monitoring-and-metrics)
9. [Pre-Production Checklist](#9-pre-production-checklist)

---

### 1. Business Problem
The company spends a significant amount of time answering routine customer questions ("Where is my order?", "How do I return an item?", "How long does delivery take?"). The agent automates up to 80% of standard inquiries 24/7.

### 2. Architecture
The system is divided into layers: Chat Trigger ➔ AI Agent Router ➔ Tools (RAG / CRM API) ➔ Guardrails & Verification ➔ Final Response.

### 3. APIs and Services Used
* OpenAI / Groq LLM API (for natural language processing).
* Online store CRM API (for checking order statuses via order_id).

### 4. RAG Implementation
Uses vector search over a local knowledge base located in the knowledge_base/ folder (delivery, return, payment, and warranty policies). Factual data is extracted directly from documents to prevent model hallucinations.

### 5. Agent Tools
* Search Knowledge Base — searches company regulations and policies.
* Get Order Status — retrieves order status by ID from the CRM.

### 6. Error Handling
* Automatic exception catching for external API failures (OpenAI / CRM).
* Graceful fallback responses when data is missing or connection issues occur.

### 7. Security and Environments
The project is split into environments: Development (locally with mock data), Staging (test environment with API sandbox), and Production (live server). Secrets are stored in secure environment variables.

### 8. Security Measures Implemented
* Principle of Least Privilege: The CRM token has Read-Only access permissions.
* Prevention of unauthorized exposure of personal data and strict secret filtering.

### 9. Cost Control
Per-request token monitoring, context window length limitation, and caching of frequent knowledge base responses.
