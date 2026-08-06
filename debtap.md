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

# Опц