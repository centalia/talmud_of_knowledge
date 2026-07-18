1) Для начала ставим 
~~~
	sudo pacman -S bluez bluez-utils
~~~

bluez - стек протоколов Bluetooth 
bluez-utils - пакет, предоставляющий bluetoothctl

После установки проверяем `lsmod` модуль ядра btusb. Это не обязательно, но иногда стоит. Еслт его нет то загружаем

---
### Ссылки
- [ArchWiki](https://wiki.archlinux.org/title/Bluetooth_(%D0%A0%D1%83%D1%81%D1%81%D0%BA%D0%B8%D0%B9)) 