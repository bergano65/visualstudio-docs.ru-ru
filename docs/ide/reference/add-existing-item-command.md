---
title: Команда Add Existing Item
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- project.addexistingitem
helpviewer_keywords:
- File.AddExistingItem command
- Add Existing Item command
ms.assetid: 41f56131-d4c7-4f81-83b7-bdac713ea870
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6ec281b508842424fbfb74bbe0726bb2ec47abe2
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
---
# <a name="add-existing-item-command"></a>Команда Add Existing Item
Добавляет существующий файл в текущее решение и открывает его.

## <a name="syntax"></a>Синтаксис

```
File.AddExistingItem filename [/e:editorname]
```

## <a name="arguments"></a>Аргументы
 `filename` Обязательный. Полный путь и имя файла с расширением для элемента, который нужно добавить в текущее решение. Если имя или путь файла содержат пробелы, нужно заключить весь путь в кавычки.

## <a name="switches"></a>Переключатели
 /e: `editorname` Необязательный. Имя редактора, в котором будет открыт файл. Если аргумент указан, но имя редактора не предоставляется, отображается диалоговое окно **Открыть с помощью**.

 В синтаксической структуре аргумента /e:`editorname` имена редакторов используются в том виде, в каком они отображаются в диалоговом окне **Открыть с помощью**, с заключением в кавычки. Например, чтобы открыть таблицу стилей в редакторе исходного кода, необходимо ввести для аргумента /e:`editorname` следующую строку:

```
/e:"Source Code (text) Editor"
```

## <a name="remarks"></a>Примечания
 Когда вы вводите данные, функция автозавершения пытается определить правильный путь и правильное имя файла.

## <a name="example"></a>Пример
 Этот пример добавляет файл Form1.frm в текущее решение.

```
>File.AddExistingItem "C:\public\solution files\Form1.frm"
```

## <a name="see-also"></a>См. также

- [Команды Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Командное окно](../../ide/reference/command-window.md)
- [Поле "Поиск/команда"](../../ide/find-command-box.md)
- [Псевдонимы команд Visual Studio](../../ide/reference/visual-studio-command-aliases.md)