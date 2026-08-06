**Debtap** - утилита для конвертации deb-пакетов в zst-пакеты. 

# Установка

```
sudo pacman -S debtap
```

# Использование

Перед конвентарции deb-пакета, обязательно обновляем базу debtap

~~~
sudo debtap -u
~~~

После обновления базы производим перевод

~~~
sudo debtap deb-package.deb
~~~

Утилита спросит имя пакет, лицензию, maintainer. И создаст pkg.tar.zst-файл, который мы устанавливаем.

~~~
sudo pacman -U deb-package.pkg.tar.zst
~~~

# Опции

|      Параметр      |                             Значение                              |
| :----------------: | :---------------------------------------------------------------: |
|  `-u`, `--update`  |                  обновить внутренную базу debtap                  |
|  `-q`, `--quiet`   |      пропустить все вопросы, кроме редактирования метаданных      |
|  `-Q`, `--Quiet`   |             пропустить все вопросы (не рекомендуется)             |
| `-s` , `--pseudo`  |     создать "псевдо 64-битный" пакет из 32-битного deb-пакета     |
| `-w`,  `--wipeout` |      Wipeout versions from all dependencies, conflicts etc.       |
| `-p`, `--pkgbuild` |               Additionally generate a PKGBUILD file               |
| `-P`, `--Pkgbuild` |                   Generate a PKGBUILD file only                   |
|  `-o`, `--output`  | Output directory for generated package and/or PKGBUILD (optional) |
| `-v`, `--version ` |                           Print version                           |
