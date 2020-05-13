---
title: Команда Add Existing Project
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- file.addexistingproject
helpviewer_keywords:
- Add Existing Project command
- File.AddExistingProject
ms.assetid: 71cf3e31-c76b-405b-ad6a-1b1bc654bd40
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 008802546d87bd44137c6d13ee2aef802877e308
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/18/2020
ms.locfileid: "75595882"
---
# <a name="add-existing-project-command"></a>Команда Add Existing Project
Добавляет существующий проект в текущее решение.

## <a name="syntax"></a>Синтаксис

```cmd
File.AddExistingProject filename
```

## <a name="arguments"></a>Аргументы
`filename`\
Необязательный параметр. Полный путь и имя проекта с расширением для проекта, который необходимо добавить в решение.

Если аргумент `filename` содержит пробелы, его необходимо заключить в кавычки.

Если имя файла не указано, при выполнении команды откроется диалоговое окно файла, в котором пользователь может выбрать проект.

## <a name="remarks"></a>Remarks
Функция автозавершения пытается определить правильный путь и правильное имя файла во время их ввода.

## <a name="example"></a>Пример
В этом примере в текущее решение добавляется проект [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] с именем TestProject1.

```cmd
>File.AddExistingProject "c:\visual studio projects\TestProject1.vbproj"
```

## <a name="see-also"></a>См. также раздел

- [Команды Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Окно команд](../../ide/reference/command-window.md)
- [Поле "Поиск/команда"](../../ide/find-command-box.md)
- [Псевдонимы команд Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
