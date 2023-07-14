# PHP LIBS Energomer СЕ102 R5.1
##### Библиотека для работы с протоколом обмена данных по TCP\IP c СЕ102 R5.1

## Features
- [PHP] >= 8.0

## Installation
-  You can install the library using composer by adding prosamael/energomer to your composer.json
```sh
composer require prosamael/energomer
```

## Usage
```php
require 'vendor/autoload.php';

try {
    $en = new Energomer('127.0.0.1', 5010, 123456);
    $en->ReadDaysEnergy()->get();
} catch (Exception $e) {
    echo $e->getMessage();
}
```

## Documentation
- Создание объекта
```php
# IP (string) - Адресс подключение
# Port (integer) - Порт подключения
# Serial (integer) - Последнии 5 цифр серийного номера устройства
$en = new Energomer('IP', PORT, SERIAL);
```

#### Отправка данных и получения ответа
```php
    $en = new Energomer('127.0.0.1', 5010, 123456);
    $en->Ping()->get(); //return Array
```

Где метод Ping() отправит запрос, а get() прочитать ответ
#### Available methods
- Ping()
- TimeSync()
- Version($index) Если предать индекс = 0 будет вызван метод VersionEx
- ReadConfig()
- ReadMonthEnergy(..$args*)
- ReadDaysEnergy(...$args*)

> $args* (array) :
- $args[0] (int) – маска - индекс глубины опроса (0 – текущие значения, 1 – за прошедшие сутки, 2 – двое суток назад, 36 – 36 суток назад), BIT[7] : 0 – НА, 1 -ЗА;
- $args[1] (int) – номер тарифа (0 – сумма по тарифам, 1…5 тариф 1…5).

#### TODO
    -  WriteConfig();
    -  ReadStatus();
    -  ReadRTCCorrection();
    -  WriteRTCCorrection();
    -  WritePsw();
    -  ReadSerialNumber();
    -  ReadDateTime();
    -  WriteDateTime();
    -  ReadMeterCode();
    -  RTCCorrectMode();
    -  ReadJournalEvent();
    -  ActivateTarProg();
    -  ReadSeason();
    -  WriteSeson();
    -  ReadSpecDays();
    -  WriteSpecDays();
    -  ReadDaySched();
    -  WriteDaySched();
    -  ReadHourZimaLeto();
    -  WriteHourZimaLeto();
    -  SCOP();
    -  ClearTarProg();

## Exception
        0 => "Команда отсутствует",
        1 => "Неверный формат принятого пакета",
        2 => "Недостаточный уровень доступа для выполнения команды",
        3 => "Неверное количество параметров для выполнения команды",
        4 => "Текущая конфигурация не позволяет выполнить эту команду",
        5 => "Не нажата кнопка «Доступ», для выполнения команды через оптопорт",
        16 => "Неверные параметры для выполнения команды",
        32 => "Несуществующая или неверная запись в памяти",
        64 => "Недопустимая тарифная программа",
        128 => "Ошибка чтения внешней памяти",
## License
LGPL v.3


