---
title: Команда "Создать файл" | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- file.newfile
helpviewer_keywords:
- File.NewFile command
- New File command
ms.assetid: 767868d6-a525-425b-a43b-2198f636ab6b
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8e0d25d585f518c854ad6176ae4ae7a5f27b22ad
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671965"
---
# <a name="new-file-command"></a>Команда New File
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Создает файл и открывает его. Файл отображается в папке "Прочие файлы".

## <a name="syntax"></a>Синтаксис

```
File.NewFile [filename] [/t:templatename] [/editor:editorname]
```

## <a name="arguments"></a>Аргументы
 `filename` Необязательный. Имя файла. Если имя не указано, задается имя по умолчанию. Если не указано имя шаблона, создается текстовый файл.

## <a name="switches"></a>Коммутаторы
 /t:`templatename` (необязательно). Указывает тип создаваемого файла.

 В синтаксической структуре аргумента /t:`templatename` используются данные из диалогового окна "Создание файла". Введите имя категории, обратную косую черту (`\`) и имя шаблона, а затем заключите всю строку в кавычки.

 Например, чтобы создать исходный файл [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)], для аргумента /t:`templatename` нужно ввести следующее:

```
/t:"Visual C++\C++ File (.cpp)"
```

 В приведенном выше примере указано, что шаблон файла C++ находится внутри категории Visual C++ в диалоговом окне **Новый файл**.

 /e:`editorname` (необязательно). Имя редактора, в котором будет открыт файл. Если аргумент указан, но имя редактора не предоставляется, отображается диалоговое окно **Открыть с помощью**.

 В синтаксической структуре аргумента /e:`editorname` имена редакторов используются в том виде, в каком они отображаются в диалоговом окне "Открыть с помощью", с заключением в кавычки.

 Например, чтобы открыть файл в редакторе исходного кода, нужно ввести для аргумента /e:`editorname` следующую строку:

```
/e:"Source Code (text) Editor"
```

## <a name="example"></a>Пример
 Этот пример создает веб-страницу "test1.htm" и открывает ее в редакторе исходного кода.

```
>File.NewFile test1 /t:"General\HTML Page" /e:"Source Code (text) Editor"
```

## <a name="see-also"></a>См. также:
 [Командное окно команды Visual Studio](../../ide/reference/visual-studio-commands.md) [Command Window](../../ide/reference/command-window.md) [Immediate Window](../../ide/reference/immediate-window.md) команда ["найти/командное окно" Поиск/команда](../../ide/find-command-box.md) [Visual Studio псевдонимы команд](../../ide/reference/visual-studio-command-aliases.md)
