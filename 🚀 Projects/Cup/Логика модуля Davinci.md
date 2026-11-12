**Переменные**
``` bash
DAVINCI_20_URL="ссыль на скачивание"
DAVINCI_20_VERSIONS="20.3.3"

DAVINCI_20_MIN_SIZE=8992784008
SIZE=stat -c "%s" "фаил"
```

**1. Подготовка**

- Создать временную папку (`mktemp -d`), сохранить путь в `local temp_dir`.
- Создать .cache
- Вывести сообщение: `==> Installing DaVinci Resolve Studio`.

**2. Скачивание**

- `download_file "$DAVINCI_URL" "$temp_dir/davinci.zip"`.

**3. Проверка размера**
- Проверить наличие файла if [ -f "путь к файлу" ]
- Если истина, то получить размер скачанного файла через `stat`.
- Иначе выводим ошибку что архива не существует и вернуть первый код ошибки
- Сравнивать `MIN_SIZE` с размером файла `SIZE` 
	- Если условие ложно вывести: `==> Error: Downloaded file is too small. Link may be outdated.` и `return 1`.
	- Если истинно то переходим к распаковке

**4. Распаковка**
- Распаковываем архив через`unzip, не переходя в временную папку, eсли ошибка — `выводим сообщение и return 1
- => Error: Extraction failed.

**5. Поиск установщика**
- Ищем файл `.run` в распакованной папке.
- Делаем его исполняемым и запускаем, если ошибка - `exit 1`
- Если файла`.run` нет — ошибка «installer not found» и `exit 1`.

**6. Установка**
**7. Запись в БД**

- `write_package "DaVinci Resolve Studio" "davinci" "$DAVINCI_VERSION" "" ""`.

**9 Уборка**

- Удаляем (`rm -rf`) `$temp_dir`  .
- `return 0`

**8. Фикс библиотек **

- Переходим в `/opt/resolve/libs`.
- Создай папку `disabled_libs` (если её нет).
- Перемещаем туда конфликтующие библиотеки: `libglib*`, `libgio*`, `libgmodule*`, `libgobject*`.






cd /opt/resolve

sudo perl -pi -e 's/\xBE\x05\x00\x00\x00\xE8\x0B\x8A\x01\x00\x84\xC0\x0F\x84\xCA\x00\x00\x00/\xBE\x05\x00\x00\x00\xE8\x0B\x8A\x01\x00\x84\xC0\x90\x90\x90\x90\x90\x90/' bin/resolve

sudo perl -pi -e 's/\xB3\x01\xE8\x64\x92\x98\x03\x84\xC0\x0F\x85\xC9\x00\x00\x00/\xB3\x01\xE8\x64\x92\x98\x03\x84\xC0\x90\xE9\xC9\x00\x00\x00/' bin/resolve

sudo perl -0777 -pi -e 's/\x74(.\xBF\x16\x00\x00\x00\xBE.\x01\x00\x00(?:\x89\xC2\x89\xC3)?\xE8)/\x75$1/g' bin/resolve