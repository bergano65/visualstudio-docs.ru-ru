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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d0946efb15758c76c078ff234717af6fd1fac15c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62792576"
---
# <a name="add-existing-project-command"></a>Команда Add Existing Project
Добавляет существующий проект в текущее решение.

## <a name="syntax"></a>Синтаксис

```cmd
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

```cmd
>File.AddExistingProject "c:\visual studio projects\TestProject1.vbproj"
```

## <a name="see-also"></a>См. также раздел

- [Команды Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Командное окно](../../ide/reference/command-window.md)
- [Поле "Поиск/команда"](../../ide/find-command-box.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)