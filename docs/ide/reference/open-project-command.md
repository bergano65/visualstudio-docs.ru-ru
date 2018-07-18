---
title: Команда Open Project
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- file.openproject
helpviewer_keywords:
- op command
- File.OpenProject command
- Open Project command
ms.assetid: baa85f86-041b-49f4-9ced-0c397dc180e1
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6663ef73f87ea0fa80eb16a3deef6765265882db
ms.sourcegitcommit: fe5a72bc4c291500f0bf4d6e0778107eb8c905f5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/07/2018
ms.locfileid: "33704136"
---
# <a name="open-project-command"></a>Команда Open Project
Открывает существующий проект.

## <a name="syntax"></a>Синтаксис

```cmd
File.OpenProject filename
```

## <a name="arguments"></a>Аргументы
 `filename`

 Обязательно. Полный путь и имя файла для открываемого проекта.

 В соответствии с требованиями синтаксиса для аргумента `filename` путь, содержащий пробелы, должен заключаться в кавычки.

## <a name="remarks"></a>Примечания
 Функция автозавершения пытается определить правильный путь и правильное имя файла во время их ввода.

 Эта команда недоступна при отладке.

## <a name="example"></a>Пример
 Этот пример открывает проект [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] — Test1.

```cmd
>File.OpenProject "C:\My Projects\Test1\Test1.vbproj"
```

## <a name="see-also"></a>См. также

- [Команды Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Командное окно](../../ide/reference/command-window.md)
- [Поле "Поиск/команда"](../../ide/find-command-box.md)
- [Псевдонимы команд Visual Studio](../../ide/reference/visual-studio-command-aliases.md)