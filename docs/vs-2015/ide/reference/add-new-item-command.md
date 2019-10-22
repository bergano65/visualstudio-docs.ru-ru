---
title: Команда "Добавить новый элемент" | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- project.addnewitem
helpviewer_keywords:
- Add New Item command
- File.AddNewItem command
ms.assetid: 63b7df32-db83-463b-bbe7-7ff011fe5298
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e6237ace96799961683b0b0431f5dad3ab679e24
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670200"
---
# <a name="add-new-item-command"></a>Команда Add New Item
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Добавляет новый элемент решения, такой как HTM, CSS, TXT или набор фреймов, в текущее решение и открывает его.

## <a name="syntax"></a>Синтаксис

```
File.AddNewItem [filename] [/t:templatename] [/e:editorname]
```

## <a name="arguments"></a>Аргументы
 `filename` Необязательный. Путь и имя файла элемента, который необходимо добавить в решение.

## <a name="switches"></a>Переключатели
 /t: `templatename` Необязательный. Указывает тип создаваемого файла. Если имя шаблона не задано, по умолчанию создается текстовый файл.

 В синтаксической структуре аргумента /t:`templatename` используются данные, находящиеся в диалоговом окне **Добавление нового элемента решения**. Вам необходимо ввести полную категорию, затем тип файла, отделив имя категории от типа файла обратной косой чертой (`\`) и заключив всю строку в кавычки.

 Например, чтобы создать текстовый файл, для аргумента /t:`templatename` необходимо ввести следующую строку:

```
/t:"General\Style Sheet"
```

 /e: `editorname` Необязательный. Имя редактора, в котором будет открыт файл. Если аргумент указан, но имя редактора не предоставляется, отображается диалоговое окно **Открыть с помощью**.

 В синтаксической структуре аргумента /e:`editorname` имена редакторов используются в том виде, в каком они отображаются в диалоговом окне **Открыть с помощью**, с заключением в кавычки.

 Например, чтобы открыть таблицу стилей в редакторе исходного кода, необходимо ввести для аргумента /e:`editorname` следующую строку:

```
/e:"Source Code (text) Editor"
```

## <a name="example"></a>Пример
 В приведенном примере в текущее решение добавляется новый элемент решения MyHTMLpg.

```
>File.AddNewItem MyHTMLpg /t:"General\HTML Page"
```

## <a name="see-also"></a>См. также
 Команды [Visual Studio командное](../../ide/reference/visual-studio-commands.md) [окно](../../ide/reference/command-window.md) [Найти/Команда](../../ide/find-command-box.md) командные [псевдонимы команд Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
