# unity-mcp-test

## Цель

Тестовый проект для автоматизации Unity через MCP (Model Context Protocol).

## Стек

| Компонент | Версия / Решение |
|---|---|
| Unity | 2022.3.62f1 LTS (URP) |
| ИИ-агент | Kilo Code |
| MCP-сервер | CoplayDev/unity-mcp |

## Rules and Skills

Rules взяты из репозитория **[Common-ka/ai-agent-unity-rules](https://github.com/Common-ka/ai-agent-unity-rules)** и адаптированы под наш проект.

**Адаптированные правила (Rules):**
- `index.mdc` — версия Unity 2022.3, стек технологий, принципы.
- `code-organization.mdc` — структура `Art/Environment`, `Art/Characters`, `Art/UI`, соглашения для AssetBundle и MCP.

**Навыки (Skills):**
- `/import-art` — импорт изображений в папку Art.
- `/create-bundle` — назначение AssetBundle и сборка.

## Результаты

- Созданы папки `Art/Environment`, `Art/Characters`, `Art/UI`.
- В них импортированы тестовые изображения.
- Назначены AssetBundle: `environment_bundle`, `ui_bundle`, а также `characters_bundle`.
- Бандлы собраны в папку `BuiltBundles/` с размерами: `environment_bundle` — 464 KB, `ui_bundle` — 308 KB, `characters_bundle` — 435 KB.