---
title: Команда Add New Item
description: Сведения о том, как с помощью команды "Добавить новый элемент" выполнить добавление нового элемента или набора фреймов в текущее решение.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Add New Item command
- File.AddNewItem command
ms.assetid: 63b7df32-db83-463b-bbe7-7ff011fe5298
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 37742f1a9adda219e359d734b80f44679509ee03
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99846339"
---
# <a name="add-new-item-command"></a>Команда Add New Item
Добавляет новый элемент решения, такой как HTM, CSS, TXT или набор фреймов, в текущее решение и открывает его.

## <a name="syntax"></a>Синтаксис

```cmd
File.AddNewItem [filename] [/t:templatename] [/e:editorname]
```

## <a name="arguments"></a>Аргументы
`filename`\
Необязательный элемент. Путь и имя файла элемента, который необходимо добавить в решение.

## <a name="switches"></a>Коммутаторы
/t: `templatename`\
Необязательный элемент. Указывает тип создаваемого файла. Если имя шаблона не задано, по умолчанию создается текстовый файл.

В синтаксической структуре аргумента /t:`templatename` используются данные, находящиеся в диалоговом окне **Добавление нового элемента решения**. Вам необходимо ввести полную категорию, затем тип файла, отделив имя категории от типа файла обратной косой чертой (`\`) и заключив всю строку в кавычки.

Например, чтобы создать текстовый файл, для аргумента /t:`templatename` необходимо ввести следующую строку:

```cmd
/t:"General\Style Sheet"
```

/e: `editorname`\
Необязательный элемент. Имя редактора, в котором будет открыт файл. Если аргумент указан, но имя редактора не предоставляется, отображается диалоговое окно **Открыть с помощью**.

В синтаксической структуре аргумента /e:`editorname` имена редакторов используются в том виде, в каком они отображаются в диалоговом окне **Открыть с помощью**, с заключением в кавычки.

Например, чтобы открыть таблицу стилей в редакторе исходного кода, необходимо ввести для аргумента /e:`editorname` следующую строку:

```cmd
/e:"Source Code (text) Editor"
```

## <a name="example"></a>Пример
В приведенном примере в текущее решение добавляется новый элемент решения MyHTMLpg.

```cmd
>File.AddNewItem MyHTMLpg /t:"General\HTML Page"
```

## <a name="see-also"></a>См. также раздел

- [Команды Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Командное окно](../../ide/reference/command-window.md)
- [Поле "Поиск/команда"](../../ide/find-command-box.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
