# Руководство по установке и использованию библиотеки

1. Через Менеджер библиотек в Arduino IDE нужно найти и установить библиотеку MCUFRIEND_kbv (не находит в последнее время, поэтому устанавливать придётся вручную.)

2. Установите библиотеку Adafruit_GFX, если она еще не установлена.

3. Вставьте в Arduino UNO mcufriend шилд с дисплеем. Поддерживаются только 28-выводные экраны.

4. Соберите любой из примеров из меню Файл->Примеры->Mcufriend_kbv. Например, graphictest_kbv.ino

5. Большинство из примеров будут выводить текст в монитор последовательного порта (9600 бод). Для примеров с BMP необходимо скопировать изображения из каталога bitmaps/ в корень microSD карты.

6. Эта библиотека предназначена только для Arduino UNO и конкретных mcufriend шилдов. Так же она будет работать на MEGA2560, но не очень быстро.

7. Конструктор не принимает аргументов (потому что он работает только с определенными шилдами)

8. Приведенные примеры являются стандартными для Adafruit. Вы можете просмотреть мои изменения, выполнив поиск по "kbv".

9. Any Adafruit sketch should work with the MCUFRIEND_kbv constructor() but should allow extra ID values.  Конструктор Adafruit(cs, rs, wr, rd, rst) ИГНОРИРУЕТ любые аргументы. т.е. использует только выводы управления шилдом.

MCUFRIEND_kbv наследует все методы из классов:

- `Adafruit_GFX`: https://learn.adafruit.com/adafruit-gfx-graphics-library/overview
- `Print`: https://www.arduino.cc/en/Serial/Print

Единственные "новые" методы связаны с оборудованием:
`vertScroll()`, `readGRAM()`, `readPixel()`, `setAddrWindow()`, `pushColors()`, `readID()`, `begin()`
`readReg()`, `pushCommand()`, `WriteCmdData()` получают доступ к регистрам контроллера

10. В данный момент поддерживаются UNO шилды на платах от "mcufriend.com" со следующими контроллерами:

| Контроллер | Разрешение | Идентификатор | Примечание |
| ------ | ------- | --------- | --- |
| GC9302   | 240x320  | ID=0x9302 |     |
| HX8347-A | 240x320  | ID=0x8347 | #define SUPPORT_8347A *** Не тестирован *** |
| HX8347-D | 240x320  | ID=0x4747 | #define SUPPORT_8347D |
| HX8347-G | 240x320  | ID=0x7575 | #define SUPPORT_8347D |
| HX8347-I | 240x320  | ID=0x9595 | #define SUPPORT_8347D |
| HX8352-A | 240x400  | ID=0x5252 | #define SUPPORT_8352A |
| HX8352-B | 240x400  | ID=0x0065 | #define SUPPORT_8352B |
| HX8357-B | 320x480  | ID=0x8357 | (shares init with 8357-D) |
| HX8357-C | 320x480  | ID=0x9090 | (Идентификатор изменился с 0x8357) |
| HX8357-D | 320x480  | ID=0x0099 | #define SUPPORT_8357D_GAMMA |
| HX8367-A | 240x320  | ID=0x6767 | #define SUPPORT_8347D |
| ILI9163  | 128x160  | ID=0x9163 | #define SUPPORT_9163 |
| ILI9225  | 176x220  | ID=0x9225 | #define SUPPORT_9225 |
| ILI9226  | 176x220  | ID=0x9226 | #define SUPPORT_9225 |
| ILI9320  | 240x320  | ID=0x9320 |  |
| ILI9325  | 240x320  | ID=0x9325 |  |
| ILI9326  | 240x400  | ID=0x9326 | #define SUPPORT_9326_5420 |
| ILI9327  | 240x400  | ID=0x9327 |  |
| ILI9328  | 240x320  | ID=0x9328 |  |
| ILI9329  | 240x320  | ID=0x9329 |  |
| ILI9331  | 240x320  | ID=0x9331 |  |
| ILI9335  | 240x320  | ID=0x9335 |  |
| ILI9338  | 240x320  | ID=0x9338 |  |
| ILI9340  | 240x320  | ID=0x9340 |  |
| ILI9341  | 240x320  | ID=0x9341 |  |
| ILI9342  | 320x240  | ID=0x9342 | #define SUPPORT_9342 |
| ILI9481  | 320x480  | ID=0x9481 |  |
| ILI9486  | 320x480  | ID=0x9486 |  |
| ILI9487  | 320x480  | ID=0x9487 |  |
| ILI9488  | 320x480  | ID=0x9488 | (weird 555 display :#define SUPPORT_9488_555) |
| LGDP4532 | 240x320  | ID=0x4532 | #define SUPPORT_4532 |
| LGDP4535 | 240x320  | ID=0x4535 | #define SUPPORT_4535 |
| NT35310  | 320x480  | ID=0x5310 | (hardware must be set for 8-bit parallel) |
| NT35702  | 240x320  | ID=0x1602 | no readGRAM() or readPixel() |
| R61505   | 240x320  | ID=0x1505 | works like an ILI9320 |
| R61505V  | 240x320  | ID=0xB505 |  |
| R61505W  | 240x320  | ID=0xC505 |  |
| R61509V  | 240x400  | ID=0xB509 | #define SUPPORT_B509_7793 |
| R61520   | 240x320  | ID=0x1520 | (no Vertical Scroll) |
| R61526A  | 240x320  | ID=0x1526 | (no Vertical Scroll) configure NVM with sketch |
| R61580   | 240x320  | ID=0x1580 | #define SUPPORT_1580 *** Не тестирован *** |
| R61581   | 320x480  | ID=0x1581 |  |
| RM68090  | 240x320  | ID=0x6809 |  |
| RM68130  | 176x220  | ID=0x6813 | #define SUPPORT_9225 |
| RM68140  | 320x480  | ID=0x6814 | #define SUPPORT_68140 |
| S6D0139  | 240x320  | ID=0x0139 | #define SUPPORT_0139 (no Band Scroll) |
| S6D0154  | 240x320  | ID=0x0154 | #define SUPPORT_0154 |
| SPFD5408 | 240x320  | ID=0x5408 |  |
| SPFD5420 | 240x400  | ID=0x5420 | #define SUPPORT_9326_5420 |
| SSD1963  | 800x480  | ID=0x1963 |  |
| SSD1289  | 240x320  | ID=0x1289 | #define SUPPORT_1289 |
| SSD1297  | 240x320  | ID=0x9797 | #define SUPPORT_1289 (unstable readGRAM()) |
| ST7735   | 128x160  | ID=0x7735 | #define SUPPORT_7735 (Не тестирован) |
| ST7781   | 240x320  | ID=0x7783 | #define SUPPORT_7781 (no Vertical Scroll) |
| ST7789V  | 240x320  | ID=0x7789 |  |
| ST7793   | 240x400  | ID=0x7793 | #define SUPPORT_B509_7793 |
| ST7796   | 320x480  | ID=0x7796 |  |
| UC8230   | 240x320  | ID=0x8230 | #define SUPPORT_8230 |
| UNKNOWN  | 320x480  | ID=0x1511 | (scroll directions not correct) |
| UNKNOWN  | 240x320  | ID=0xAC11 |  |
| UNKNOWN  | 240x320  | ID=0x2053 | weird controller from BangGood (was ID=0x0000) |
| UNKNOWN  | 240x320  | ID=0x8031 | (no Vertical Scroll) |
| UNKNOWN  | 240x320  | ID=0x0001 | (0x9320 style) |
| UNKNOWN  | 240x320  | ID=0x3229 | readGRAM() does not work properly. NEED DATASHEET. |
| UNKNOWN  | 240x320  | ID=0xE300 | weird controller from BangGood. NEED DATASHEET |

Большинство из этих контроллеров по умолчанию имеют определения (`#define SUPPORT_xxxx`).
Вы можете сэкономить флэш-память на Uno, закомментировав ненужные макрос(ы) в MCUFRIEND_kbv.cpp

11. Библиотека должна работать на ***UNO***, ***MEGA2560***, ***LEONARDO***, ***DUE***, ***ZERO***, ***M0-PRO***. Она также работает на ***NUCLEO-F103*** и ***TEENSY3.2*** с адаптером **Sparkfun**

12. Как правило, все эти шильды Mcufriend имеют резистивный сенсорный экран на выводах `A1`, `7`, `A2`, `6`, но они не всегда имеют одинаковое направление движение.<br>
Скетч [TouchScreen_Calibr_native.ino](../examples/TouchScreen_Calibr_native/TouchScreen_Calibr_native.ino) проведет диагностику контактов сенсорного экрана, выполнит калибровку и выведет отчет на монитор последовательного порта.<br>
Калибровка должна работать с библиотекой TouchScreen.h от Adafruit.<br>
Вы всегда можете скопировать локальную библиотеку TouchScreen_kbv.h из скетча в глобальный каталог пользовательских библиотек.

13. Скетч [graphictest_kbv.ino](../examples/graphictest_kbv/graphictest_kbv.ino) запускает стандартные тесты Adafruit и сообщает время их выполнения.<br>
Тесты прокрутки показывают каждый поворот экрана, цвета, направления прокрутки, инверсию цвета.<br>
Вертикальная прокрутка осуществляется вверх/вниз в портретном режиме. Влево/вправо в альбомном.<br>
Прокрутка полосы должна просто перемещать цветную полосу.<br>
ILI9320 всегда будет перемещать весь экран.<br>
Текст "*SOFTWARE SCROLL*" должен перемещаться по экрану горизонтально или сообщать об ОШИБКЕ readPixel().

14. Скетч [scroll_kbv.ino](../examples/scroll_kbv/scroll_kbv.ino) должен прокручивать окно или подокно для большинства чипов. Но не все чипы могут это делать.

15. The [readpixel_kbv.ino](../examples/readpixel_kbv/readpixel_kbv.ino) sketch should display memory in each aspect.

16. The [GLUE_Demo_320x240.ino](../examples/GLUE_Demo_320x240/GLUE_Demo_320x240.ino) sketch uses a "GLUE" class to display a UTFT sketch on supported mcufriend shields.<br>
It is NOT perfect.   Please report any problems. It is designed as a CONVENIENCE for legacy UTFT code.<br>
Please use MCUFRIEND_kbv method()s in new code.

17. Если у вас не стандартный шилд для Uno, вы можете добавить SPECIAL определение в mcufriend_special.h
    - Отредактируйте mcufriend_shield.h:  #define USE_SPECIAL
    - Отредактируйте mcufriend_special.h: например #define USE_MEGA_16BIT_SHIELD<br>
    Если ваш "специальный" доступен только для записи, библиотека не сможет прочитать идентификатор и всегда возвращает `0xD3D3`

18. Запустите файл [LCD_ID_readreg.ino](../examples/LCD_ID_readreg/LCD_ID_readreg.ino) для проверки нестандартного подключения.  Вставьте определение в сообщение на форуме.

19. Шилды OPEN-SMART имеют другую разводку, чем обычные шилды для Uno:<br>
    - Отредактируйте utility/mcufriend_shield.h: `#define USE_SPECIAL`
    - Отредактируйте utility/mcufriend_special.h: #define USE_OPENSMART_SHIELD_PINOUT_xxx например `USE_OPENSMART_SHIELD_PINOUT_MEGA`
    - Отредактируйте MCUFRIEND_kbv.cpp: `#define SUPPORT_8352B`

20. OPEN-SMART Shields can not read LM75A on a Mega because there are no SDA/SCL pins next on AREF header.<br>
    - Uno:  LM75A on pcb works.  Difficult to add external I2C devices when Shield is plugged in.
    - Uno:  All use of SPI bus should use SPI.beginTransaction(), SPI.endTransaction()
    - Leo:  I do not support USE_OPENSMART_SHIELD_PINOUT_LEO
    - Mega: Old boards do not have SDA/SCL on AREF header.   - Only external I2C devices on COMMS header
    - Due:  MAX809 Reset chip interferes with 3.3V RST on SPI header.  Manual reset for Upload / Run.

21. BLUEPILL Adapter standard wiring is:
    //LCD pins  |D7 |D6 |D5 |D4 |D3 |D2 |D1 |D0 | |RD |WR |RS |CS |RST| |SD_SS|SD_DI|SD_DO|SD_SCK|<br>
    //STM32 pin |PA7|PA6|PA5|PA4|PA3|PA2|PA1|PA0| |PB0|PB6|PB7|PB8|PB9| |PA15 |PB5  |PB4  |PB3   | **ALT-SPI1**<br>

    Maple core:  to use SPI2 for SPI. edit SPI.cpp for SPIClass SPI(2);<br>
    STM Core:    to use SPI2 for SPI. edit variant.h to use PA15, PB3, PB4, PB5 for SPI_SS etc

    Touchscreen needs XM, YP to be on Analog capable pins.  Measure resistance with DMM to determine X, Y
    300R pair is XP, XM.  500R pair is YP, YM.  choose XM, YP from PA7, PA6.  XP, YM from PB6, PB7
    Run the Calibration sketch to get accurate TS_LEFT, TS_RT, TS_TOP, TS_BOT values.
    Ignore the XP, XM, ... values.   They mean nothing on a BluePill

    Adafruit_Touchscreen might need: typedef volatile uint32_t RwReg;

    Maple core:  use Touchscreen_kbv library
    STM Core:    regular Touchscreen libraries should be ok.

    ИСТОРИЯ ИЗМЕНЕНИЙ теперь находится в файле "mcufriend_history.txt"
