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
- `/import-art` — импорт изображений в папку Art с настройками для URP.
- `/create-bundle` — создание AssetBundle: спрашивает папку, имя, тип (корневой/вложенный), обрабатывает вложенные папки и предлагает сборку.
- `/build-bundles` — отдельная сборка всех AssetBundle (если не была выполнена в `/create-bundle`).

## Результаты

- Созданы папки `Art/Environment`, `Art/Characters`, `Art/UI`.
- В них импортированы тестовые изображения.
- Назначены два AssetBundle:
    - `art_bundle` (корневой) — включает все файлы в `Art`, **кроме** папки `Art/UI` (файлы верхнего уровня + Environment + Characters).
    - `ui_bundle` (вложенный) — включает только файлы внутри `Art/UI`.
- Бандлы собраны в папку `BuiltBundles/` с физической структурой:
  BuiltBundles/ 
  - ├── art_bundle # лежит прямо в корне BuiltBundles 
  - └── UI/ui_bundle # лежит внутри подпапки UI

## Примеры промптов для агента

Эти запросы активируют соответствующие скилы и автоматически запрашивают недостающие параметры (имя бандла, путь для вложенности и т.д.):

1. `«Импортировать изображения»`
Агент вызовет `/import-art`, спросит путь, сам определит тип по имени папки и применит настройки текстур.

2. `«Импортируй изображения из папки C:/Users/User/Downloads/art/ в папку Art. Файлы: forest.jpg → Environment/, knight.png → Characters/, button.png → UI/.»`  
Агент вызовет `/import-art`, разместит файлы в указанные папки и применит настройки текстур.

3. `«Создать AssetBundle»`
Агент вызовет `/create-bundle`, уточнит недостающую информацию.

4. `«Создай AssetBundle для папки Art с именем art_bundle как корневой»`
Агент вызовет `/create-bundle`, назначит бандл на файлы верхнего уровня, затем спросит про вложенные папки.

5. `«Собери все AssetBundle»`  
Агент вызовет `/build-bundles`, проверит назначения и соберёт бандлы.