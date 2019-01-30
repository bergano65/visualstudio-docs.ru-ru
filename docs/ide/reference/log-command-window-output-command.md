---
title: Команда Log Command Window Output
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- tools.logcommandwindowoutput
helpviewer_keywords:
- log Command window output command
- View.LogCommandWindowOutput command
ms.assetid: d4ecec35-5af4-4954-8d60-2cd24583fbb4
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f582b4a2017985f6fcd1961c6da3899b3faa0180
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54958814"
---
# <a name="log-command-window-output-command"></a>Команда Log Command Window Output
Копирует все входные и выходные данные из окна **Команда** в файл.

## <a name="syntax"></a>Синтаксис

```cmd
Tools.LogCommandWindowOutput [filename] [/on|/off] [/overwrite]
```

## <a name="arguments"></a>Аргументы
 `filename`

 Необязательный параметр. Имя файла журнала. По умолчанию этот файл создается в папке профиля пользователя. Если такое имя файла уже существует, журнал добавляется в конец имеющегося файла. Если файл не указан, используется последний указанный файл. Если предыдущий файл отсутствует, создается файл журнала по умолчанию с именем cmdline.log.

> [!TIP]
> Чтобы изменить расположение для сохранения файла журнала, введите полный путь. Если этот путь содержит пробелы, заключите его в кавычки.


## <a name="switches"></a>Переключатели
 /on

 Необязательный параметр. Запускает ведение журнала для окна **Команда** в указанном файле, добавляя в него новые данные.

 /off

 Необязательный параметр. Останавливает ведение журнала для окна **Команда**.

 /overwrite

 Необязательный параметр. Если указанный в аргументе `filename` файл совпадает с существующим файлом, он перезаписывается.

## <a name="remarks"></a>Примечания
 Если файл не указан, создается файл по умолчанию cmdline.log. По умолчанию эта команда имеет псевдоним Log.

## <a name="examples"></a>Примеры
 Этот пример создает файл журнала cmdlog и запускает ведение журнала команд.

```cmd
>Tools.LogCommandWindowOutput cmdlog
```

 Этот пример останавливает ведение журнала команд.

```cmd
>Tools.LogCommandWindowOutput /off
```

 Этот пример возобновляет ведение журнала команд в ранее использовавшемся файле.

```cmd
>Tools.LogCommandWindowOutput /on
```

## <a name="see-also"></a>См. также раздел

- [Команды Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Командное окно](../../ide/reference/command-window.md)
- [Поле "Поиск/команда"](../../ide/find-command-box.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)