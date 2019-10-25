---
title: Команда Open File
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- file.openfile
helpviewer_keywords:
- Open File command
- File.OpenFile command
- of command
ms.assetid: a51a83fc-e3c6-4fa2-8882-8b7b6c0a6406
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 811667e89f01728c5a7516f5e7f7a12d448c6311
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72666433"
---
# <a name="open-file-command"></a>Команда Open File

Открывает существующий файл и позволяет указать редактор.

## <a name="syntax"></a>Синтаксис

```cmd
File.OpenFile filename [/e:editorname]
```

## <a name="arguments"></a>Аргументы

`filename`

Обязательный. Полный или частичный путь и имя для открываемого файла. Пути, содержащие пробелы, следует заключить в кавычки.

## <a name="switches"></a>Переключатели

/e:`editorname`

Необязательный параметр. Имя редактора, в котором будет открыт файл. Если аргумент указан, но имя редактора не предоставляется, отображается диалоговое окно **Открыть с помощью**.

В синтаксической структуре аргумента /e:`editorname` имена редакторов используются в том виде, в каком они отображаются в диалоговом окне "Открыть с помощью", с заключением в кавычки.

Например, чтобы открыть файл в редакторе исходного кода, нужно ввести для аргумента /e:`editorname` следующую строку:

```cmd
/e:"Source Code (text) Editor"
```

## <a name="remarks"></a>Примечания

Когда вы вводите путь, функция автозавершения пытается определить правильный путь и правильное имя файла.

## <a name="example"></a>Пример

Этот пример открывает файл стилей "Test1.CSS" в редакторе исходного кода.

```cmd
>File.OpenFile "C:\My Projects\project1\Test1.css" /e:"Source Code (text) Editor"
```

## <a name="see-also"></a>См. также

- [Команды Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Командное окно](../../ide/reference/command-window.md)
- [Окно интерпретации](../../ide/reference/immediate-window.md)
- [Поле "Поиск/команда"](../../ide/find-command-box.md)
- [Псевдонимы команд Visual Studio](../../ide/reference/visual-studio-command-aliases.md)