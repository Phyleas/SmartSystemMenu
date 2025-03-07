![SmartSystemMenu](https://user-images.githubusercontent.com/8102586/68280906-8e86b800-0087-11ea-9762-f9eb028bb8fe.png) SmartSystemMenu
=============

- [English](/README.md)
- Русский
- [中文版](/README_CN.md)

---

SmartSystemMenu добавляет дополнительные пункты системного меню, такие как:

* **Information.** Отображает диалог с детальной информацией об окне и процессе, которому принадлежит окно.
* **Roll Up.** Позволяет свернуть вверх до заголовка окно и обратно.
* **Aero Glass.** Включает для текущего окна режим "Aero Glass". (Поддерживается в Windows Vista and выше. Удобно по большей части для консольных окон.)
* **Always On Top.** Отображает окно поверх остальных окон системы.
* **Send To Bottom.** Отображает окно за всеми окнами системы.
* **Save Screenshot.** Позволяет сохранить скриншот окна в файл.
* **Open File In Explorer.** Открывает File Explorer с выделенным файлом процесса, которому принадлежит окно.
* **Drag By Mouse.** Позволяет перетащить окно мышкой за любую его область.
* **Resize.** Позволяет изменить размер окна.
* **Move To.** Позволяет перенести окно на другой монитор.
* **Alignment.** Позволяет выравнить окно в одной из 9 позиций.
* **Transparency.** Позволяет изменить прозрачность окна.
* **Priority.** Позволяет изменить приоритет процесса, которому принадлежит окно.
* **Clipboard.** Позволяет скопировать текст окна в буфер обмена или очистить буфер обмена.
* **System Tray.** Сворачивает окно в системный трей.
* **Other Windows.** Позволяет закрыть или минимизировать все окна системы кроме текущего.
* **Start Program.** Запускает любой процесс заданный через настройки программы.

Скриншоты
------------------

![alt tag](https://user-images.githubusercontent.com/8102586/104854360-42840400-5917-11eb-8844-1528b72ee62c.jpg)
![alt tag](https://user-images.githubusercontent.com/8102586/104854362-457ef480-5917-11eb-9ccf-21c6a8d50b53.jpg)
![alt tag](https://user-images.githubusercontent.com/8102586/104854366-4879e500-5917-11eb-91d1-e2a7c555ce39.jpg)
![alt tag](https://user-images.githubusercontent.com/8102586/104854373-4d3e9900-5917-11eb-9ab6-ec7e29b8f704.png)

Интерфейс командной строки
--------------------

```bash
   --help             The help
   --title            Title
   --titleBegins      Title begins 
   --titleEnds        Title ends
   --titleContains    Title contains
   --handle           Handle (1234567890) (0xFFFFFF)
   --processId        PID (1234567890)
-d --delay            Delay in milliseconds
-l --left             Left
-t --top              Top
-w --width            Width
-h --height           Height
-i --information      Information dialog
-s --savescreenshot   Save Screenshot
-m --monitor          [0, 1, 2, 3, ...]
-a --alignment        [topleft,
                       topcenter,
                       topright,
                       middleleft,
                       middlecenter,
                       middleright,
                       bottomleft,
                       bottomcenter,
                       bottomright]
-p --priority         [realtime,
                       high,
                       abovenormal,
                       normal,
                       belownormal,
                       idle]
   --transparency     [0 ... 100]
   --alwaysontop      [on, off]
-g --aeroglass        [on, off]
   --sendtobottom     No params
-o --openinexplorer   No params
-c --copytoclipboard  No params
   --clearclipboard   No params
   --nohighdpi        Disable High DPI Support
-n --nogui            No GUI

Example:
SmartSystemMenu.exe --title "Untitled - Notepad" -a topleft -p high --alwaysontop on --nogui
```

Установка
--------------------

* Скачайте последнюю версию [SmartSystemMenu](https://github.com/AlexanderPro/SmartSystemMenu/releases) в zip файле
* [Chocolatey](https://chocolatey.org/): `choco install smartsystemmenu`

Требования к системе
--------------------

* ОС Windows XP SP3 и выше. Поддержка x86 and x64 систем.
* .NET Framework 4.0

Файлы
--------------------

* SmartSystemMenu.exe
* SmartSystemMenu64.exe (находится в ресурсах SmartSystemMenu.exe)
* SmartSystemMenuHook.dll
* SmartSystemMenuHook64.dll
* SmartSystemMenu.xml
* Language.xml

Программа состоит из SmartSystemMenu.exe and SmartSystemMenuHook.dll модулей для x86 систем, SmartSystemMenu64.exe и SmartSystemMenuHook64.dll модулей для x64 систем. Когда запускается процесс SmartSystemMenu.exe, он так же стартует SmartSystemMenu64.exe процесс. Эти два процесса загружают хуки (SmartSystemMenuHook.dll и SmartSystemMenuHook64.dll) во все процессы системы. Когда выбирается один из добавленных пунктов меню, хук пересылает информацию об этом в основной процесс SmartSystemMenu.exe (SmartSystemMenu64.exe) и уже сам процесс выполняет действие.

Ограничения
--------------------

Утилита не может добавлять пункты в системные меню окон, которые не имеют его или которые создают своё собственное системное меню, такие как IE 9 и выше, Chrome 29 и выше, окна Delphi процессов и т.д.

Примечание
--------------------

При запуске SmartSystemMenu.exe отображается окно UAC, т.к. программе требуются привилегии для доступа к информации о процессах и окнах системы.