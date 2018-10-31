---
title: "\"Параметры\", \"Текстовый редактор\", C#, \"Дополнительно\""
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Outlining
- VS.ToolsOptionsPages.Text_Editor.CSharp.Advanced
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 16c92111fc29071447d4af5e736b881fa7c7a769
ms.sourcegitcommit: e680e8ac675f003ebcc8f8c86e27f54ff38da662
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/16/2018
ms.locfileid: "49356747"
---
# <a name="options-text-editor-c-advanced"></a>"Параметры", "Текстовый редактор", C#, "Дополнительно"

Страница **Дополнительно** позволяет изменять параметры для форматирования в редакторе, рефакторинга кода и комментариев XML-документации в C#. Для доступа к этой странице параметров выберите **Сервис** > **Параметры** и затем **Текстовый редактор** > **C#** > **Дополнительно**.

> [!NOTE]
> Здесь могут быть указаны не все параметры.

## <a name="analysis"></a>Анализ

- Включить полный анализ решения

   Включает анализ кода для всех, а не только открытых файлов в решении. Дополнительные сведения см. в разделе [Полный анализ решения](../../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md).

## <a name="using-directives"></a>Директивы using

- Располагать директивы "System" первыми при сортировке using

   При выборе команды **Remove and Sort Usings** (Удалить и сортировать директивы using) в контекстном меню выполняется сортировка директив `using` и помещение пространств имен System в верхнюю часть списка.

   До сортировки:

   ```csharp
   using AutoMapper;
   using FluentValidation;
   using System.Collections.Generic;
   using System.Linq;
   using Newtonsoft.Json;
   using System;
   ```
   
   После сортировки:

   ```csharp
   using System;
   using System.Collections.Generic;
   using System.Linq;
   using AutoMapper;
   using FluentValidation;
   using Newtonsoft.Json;
   ```
   
- Разделять группы директив using

   При выборе команды **Удалить и сортировать директивы using** в контекстном меню выполняется отделение `using` путем вставки пустой строки между группами директив, у которых одно и то же корневое пространство имен.

   До сортировки:

   ```csharp
   using AutoMapper;
   using FluentValidation;
   using System.Collections.Generic;
   using System.Linq;
   using Newtonsoft.Json;
   using System;
   ```
   
   После сортировки:
   
   ```csharp
   using AutoMapper;
   
   using FluentValidation;
   
   using Newtonsoft.Json;
   
   using System;
   using System.Collections.Generic;
   using System.Linq;
   ```
   
- Добавление директив using для типов в базовых сборках и пакетах NuGet 

   При выборе доступна команда [Быстрое действие](../quick-actions.md) для установки пакета NuGet и добавления директивы `using` для типов, на которые нет ссылок.

   ![Быстрое действие для установки пакета NuGet в Visual Studio](media/nuget-lightbulb.png)
  
## <a name="highlighting"></a>Выделение

- Выделить ссылки на символ под курсором

   Когда курсор находится внутри символа либо вы щелкаете его, выделяются все экземпляры этого символа в файле кода.

## <a name="outlining"></a>структуризация

- Переходить в режим структурирования после открытия файлов

   При выборе автоматически структурирует файл кода, создавая свертываемые блоки кода. При первом открытии файла блоки #regions и неактивные блоки кода свертываются.

## <a name="editor-help"></a>Справка по редактору

- Создавать комментарии XML-документации для ///

   Когда параметр выбран, после ввода начала комментария `///` в XML-документации вставляются XML-элементы для комментариев. Дополнительные сведения о XML-документации см. в разделе [Комментарии к XML-документации (руководство по программированию на C#)](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments).

## <a name="see-also"></a>См. также

- [Практическое руководство. Вставка XML-комментариев для создания документации](../../ide/reference/generate-xml-documentation-comments.md)
- [Комментарии к XML-документации (руководство по программированию на C#)](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments)
- [Документирование кода с помощью XML-комментариев (руководство по C#)](/dotnet/csharp/codedoc)
- [Настройка языковых параметров редактора](../../ide/reference/setting-language-specific-editor-options.md)
- [C# IntelliSense](../../ide/visual-csharp-intellisense.md)
