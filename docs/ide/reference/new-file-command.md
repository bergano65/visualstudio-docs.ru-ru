---
title: Команда New File
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- file.newfile
helpviewer_keywords:
- File.NewFile command
- New File command
ms.assetid: 767868d6-a525-425b-a43b-2198f636ab6b
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9d6707d2e9ed8e001762939cb08ffee58f1c1cdc
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62950900"
---
# <a name="new-file-command"></a>Команда New File
Создает файл и открывает его. Файл отображается в папке "Прочие файлы".

## <a name="syntax"></a>Синтаксис

```cmd
File.NewFile [filename] [/t:templatename] [/editor:editorname]
```

## <a name="arguments"></a>Аргументы
 `filename`

 Необязательный параметр. Имя файла. Если имя не указано, задается имя по умолчанию. Если не указано имя шаблона, создается текстовый файл.

## <a name="switches"></a>Переключатели
 /t:`templatename`

 Необязательный параметр. Указывает тип создаваемого файла.

 В синтаксической структуре аргумента /t:`templatename` используются данные из диалогового окна "Создание файла". Введите имя категории, обратную косую черту (`\`) и имя шаблона, а затем заключите всю строку в кавычки.

 Например, чтобы создать исходный файл [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)], для аргумента /t:`templatename` нужно ввести следующее:

```cmd
/t:"Visual C++\C++ File (.cpp)"
```

 В приведенном выше примере указано, что шаблон файла C++ находится внутри категории Visual C++ в диалоговом окне **Новый файл**.

 /e:`editorname`

 Необязательный параметр. Имя редактора, в котором будет открыт файл. Если аргумент указан, но имя редактора не предоставляется, отображается диалоговое окно **Открыть с помощью**.

 В синтаксической структуре аргумента /e:`editorname` имена редакторов используются в том виде, в каком они отображаются в диалоговом окне "Открыть с помощью", с заключением в кавычки.

 Например, чтобы открыть файл в редакторе исходного кода, нужно ввести для аргумента /e:`editorname` следующую строку:

```cmd
/e:"Source Code (text) Editor"
```

## <a name="example"></a>Пример
 Этот пример создает веб-страницу "test1.htm" и открывает ее в редакторе исходного кода.

```cmd
>File.NewFile test1 /t:"General\HTML Page" /e:"Source Code (text) Editor"
```

## <a name="see-also"></a>См. также раздел

- [Команды Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Командное окно](../../ide/reference/command-window.md)
- [Окно интерпретации](../../ide/reference/immediate-window.md)
- [Поле "Поиск/команда"](../../ide/find-command-box.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)