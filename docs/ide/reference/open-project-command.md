---
title: Открыть проект - команда
description: Узнайте о команде Open Project и о том, как она позволяет открыть существующий проект или решение.
ms.custom: SEO-VS-2020
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
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 4298c840094f7f1f75e58be1b25213cdf66a6674
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99881974"
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

## <a name="remarks"></a>Комментарии

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
