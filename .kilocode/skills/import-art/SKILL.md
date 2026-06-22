---
name: import-art
description: Импортирует изображения в папку Art с правильной структурой и настройками для URP
---

# Импорт арта

## Инструкция
1. Попроси пользователя указать путь к файлам на диске (например, `C:/Temp/Art/`).
2. Для каждого файла определи тип (Environment, Characters, UI) по имени или по запросу пользователя.
3. Используя MCP-инструмент `import_asset`, импортируй файл в соответствующую подпапку `Art/{тип}/`.
4. После импорта **настрой текстуры** для URP:
   - Для **Environment** (фоны, ландшафты):
     - Texture Type: `Default`
     - sRGB (Color Texture): ✅ включена
     - Compression: `High Quality` (или `Normal Quality` для больших текстур)
     - Format: `ASTC 6x6` (или `DXT5` для Windows)
   - Для **Characters** (спрайты персонажей):
     - Texture Type: `Sprite (2D and UI)`
     - Sprite Mode: `Single` (или `Multiple`, если есть атлас)
     - Pixels Per Unit: `100` (или стандартное)
     - Compression: `High Quality`
     - Format: `ASTC 6x6` (или `DXT5` для Windows)
   - Для **UI** (кнопки, иконки):
     - Texture Type: `Sprite (2D and UI)`
     - Sprite Mode: `Single`
     - Pixels Per Unit: `100`
     - Compression: `High Quality`
     - Format: `ASTC 6x6` (или `DXT5` для Windows)
5. Если MCP не поддерживает изменение настроек импорта, сообщи пользователю, какие настройки нужно применить вручную (через Inspector → Texture Import Settings).
6. После завершения импорта и настройки проверь, что файлы появились в окне Project, и сообщи пользователю результат.