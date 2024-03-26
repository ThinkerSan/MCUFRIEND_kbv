# MCUFRIEND_kbv

Библиотека для mcufriend шилдов с дисплеями 2.4, 2.8, 3.5, 3.6, 3.95 дюймов под Arduino UNO

1. Через Менеджер библиотек в Arduino IDE нужно найти и установить библиотеку MCUFRIEND_kbv (не находит в последнее время, поэтому устанавливать придётся вручную.)

2. Установите библиотеку Adafruit_GFX, если она еще не установлена.

3. Вставьте в Arduino UNO mcufriend шильд с дисплеем. Поддерживаются только 28-выводные экраны.

4. Соберите любой из примеров из меню Файл->Примеры->Mcufriend_kbv. Например:

    - graphictest_kbv.ino: показывает все методы.
    - LCD_ID_readreg.ino:  диагностическая проверка для выявления неподдерживаемых контроллеров.

MCUFRIEND_kbv наследует все методы из классов:

- `Adafruit_GFX`: <https://learn.adafruit.com/adafruit-gfx-graphics-library/overview>
- `Print`: <https://www.arduino.cc/en/Serial/Print>

Единственные "новые" методы связаны с оборудованием:
`vertScroll()`, `readGRAM()`, `readPixel()`, `setAddrWindow()`, `pushColors()`, `readID()`, `begin()`

`readReg()`, `pushCommand()`, `WriteCmdData()` получают доступ к регистрам контроллера

Расположение файла изменилось с версией 2.9.3. При замене библиотеки, существовавшей до версии 2.9.3 необходимо:

- Выйти из Arduino IDE.
- Удалить существующую папку MCUFRIEND_kbv.
- Запустить IDE. Установить билиотеку заново из менеджера библиотек.

КАК УСТАНОВИТЬ И ИСПОЛЬЗОВАТЬ теперь находится в файле [mcufriend_how_to.txt](extras/mcufriend_how_to.md)

ИСТОРИЯ ИЗМЕНЕНИЙ теперь находится в файле [mcufriend_history.txt](extras/mcufriend_history.txt)
