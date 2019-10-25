---
title: Команда "Оболочка" | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- tools.shell
helpviewer_keywords:
- exe files
- Shell command
- Tools.Shell command
- executables, running from Visual Studio
- .exe files
- Shell, launching exe files
- Visual Studio, executables from
ms.assetid: 737fda23-b852-45c4-a9fe-41cbce6ba70f
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ad49aadf6be56fb330b883050e6a6ff893cf054a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663544"
---
# <a name="shell-command"></a>Команда Shell
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Запускает исполняемые программы из [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].

## <a name="syntax"></a>Синтаксис

```
Tools.Shell [/command] [/output] [/dir:folder] path [args]
```

## <a name="arguments"></a>Аргументы
 `path` Обязательный. Путь и имя исполняемого файла или открываемого документа. Полный путь требуется, если указанный файл не находится в одном из каталогов, заданных в переменной среды PATH.

 `args` Необязательный. Все аргументы, передаваемые в вызванную программу.

## <a name="switches"></a>Переключатели
 /коммандвиндов [или]/Command [или]/c [или]/КМД необязательный. Указывает, что выходные данные для исполняемого файла отображаются в окне **Команда**.

 /Dir: `folder` [или]/d: `folder` необязательный. Указывает рабочий каталог, задаваемый при запуске программы.

 /OutputWindow [или]/Output [или]/out [или]/o необязательный. Указывает, что выходные данные для исполняемого файла отображаются в окне **Вывод**.

## <a name="remarks"></a>Примечания
 Параметры /dir /o /c должны быть указаны сразу после `Tools.Shell`. Все, что указано после имени исполняемого файла, передается в виде аргументов командной строки.

 Вместо `Tools.Shell` можно использовать предопределенный псевдоним `Shell`.

> [!CAUTION]
> Если аргумент `path` указывает путь к каталогу, а также имя файла, следует заключить все имя пути в кавычки ("""), как показано ниже:

```
Tools.Shell """C:\Program Files\SomeFile.exe"""
```

 Каждый набор из трех двойных кавычек (""") интерпретируется процессором `Shell` как один символ двойной кавычки. Таким образом, предыдущий пример фактически передает в команду `Shell` следующую строку пути:

```
"C:\Program Files\SomeFile.exe"
```

> [!CAUTION]
> Если не заключить строку пути в кавычки ("""), Windows будет использовать только часть строки, расположенную до первого пробела. Например, если бы приведенная выше строка пути не была заключена в кавычки должным образом, Windows искала бы файл с именем "Program", расположенный в корневом каталоге C:\. Если бы исполняемый файл C:\Program.exe был реально доступен, даже будучи установленным в результате незаконного изменения, Windows попыталась бы выполнить эту программу вместо требуемой "c:\Program Files\SomeFile.exe".

## <a name="example"></a>Пример
 Следующая команда использует xcopy.exe, чтобы скопировать файл `MyText.txt` в папку `Text`. Выходные данные xcopy.exe отображаются как в окне **Команда**, так и в окне **Вывод**.

```
>Tools.Shell /o /c xcopy.exe c:\MyText.txt c:\Text\MyText.txt
```

## <a name="see-also"></a>См. также
 [Команды Visual Studio ](../../ide/reference/visual-studio-commands.md) [Command окно ](../../ide/reference/command-window.md) [Output окно ](../../ide/reference/output-window.md) [Find/Command ](../../ide/find-command-box.md) [командные псевдонимы команды Studio](../../ide/reference/visual-studio-command-aliases.md)
