---
title: Открыть проект - команда
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- file.openproject
- file.opensolution
helpviewer_keywords:
- op command
- File.OpenProject command
- Open Project command
ms.assetid: baa85f86-041b-49f4-9ced-0c397dc180e1
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7e9249088b188fde1b346772ab1230d33160fe59
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62996817"
---
# <a name="open-project-command"></a>Команда Open project

Открывает существующий проект или решение.

## <a name="syntax"></a>Синтаксис

```cmd
File.OpenProject filename
```

## <a name="arguments"></a>Аргументы

`filename`

Обязательный. Полный путь и имя файла открываемого проекта или решения.

> [!NOTE]
> В соответствии с требованиями синтаксиса для аргумента `filename` путь, содержащий пробелы, должен заключаться в кавычки.

## <a name="remarks"></a>Примечания

Функция автозавершения пытается определить правильный путь и правильное имя файла во время их ввода.

Эта команда недоступна при отладке.

## <a name="example"></a>Пример

В следующем примере открывается проект Visual Basic **Test1**:

```cmd
>File.OpenProject "C:\My Projects\Test1\Test1.vbproj"
```

## <a name="see-also"></a>См. также

- [Команды Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Командное окно](../../ide/reference/command-window.md)
- [Поле "Поиск/команда"](../../ide/find-command-box.md)
- [Псевдонимы команд Visual Studio](../../ide/reference/visual-studio-command-aliases.md)