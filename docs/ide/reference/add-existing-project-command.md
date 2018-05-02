---
title: Команда Add Existing Project
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- file.addexistingproject
helpviewer_keywords:
- Add Existing Project command
- File.AddExistingProject
ms.assetid: 71cf3e31-c76b-405b-ad6a-1b1bc654bd40
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 72ce42ae8a13decd48e4e41a02b18f5baeb875d6
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
---
# <a name="add-existing-project-command"></a>Команда Add Existing Project
Добавляет существующий проект в текущее решение.

## <a name="syntax"></a>Синтаксис

```
File.AddExistingProject filename
```

## <a name="arguments"></a>Аргументы
 `filename` Необязательный. Полный путь и имя проекта с расширением для проекта, который необходимо добавить в решение.

 Если аргумент `filename` содержит пробелы, его необходимо заключить в кавычки.

 Если имя файла не указано, при выполнении команды откроется диалоговое окно файла, в котором пользователь может выбрать проект.

## <a name="remarks"></a>Примечания
 Функция автозавершения пытается определить правильный путь и правильное имя файла во время их ввода.

## <a name="example"></a>Пример
 В этом примере в текущее решение добавляется проект [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] с именем TestProject1.

```
>File.AddExistingProject "c:\visual studio projects\TestProject1.vbproj"
```

## <a name="see-also"></a>См. также

- [Команды Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Командное окно](../../ide/reference/command-window.md)
- [Поле "Поиск/команда"](../../ide/find-command-box.md)
- [Псевдонимы команд Visual Studio](../../ide/reference/visual-studio-command-aliases.md)