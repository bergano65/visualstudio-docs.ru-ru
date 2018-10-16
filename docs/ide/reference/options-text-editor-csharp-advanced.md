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
ms.openlocfilehash: ab08de0c6993f57c719f69ccf27e30e3cbe41c32
ms.sourcegitcommit: 80f9daba96ff76ad7e228eb8716df3abfd115bc3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2018
ms.locfileid: "37433306"
---
# <a name="options-text-editor-c-advanced"></a>"Параметры", "Текстовый редактор", C#, "Дополнительно"

Страница **Дополнительно** позволяет изменять параметры для форматирования в редакторе, рефакторинга кода и комментариев XML-документации в C#. Для доступа к этой странице параметров выберите **Сервис** > **Параметры** и затем **Текстовый редактор** > **C#** > **Дополнительно**.

> [!NOTE]
> Здесь могут быть указаны не все параметры.

## <a name="analysis"></a>Анализ

- Включить полный анализ решения

   Включает анализ кода для всех, а не только открытых файлов в решении. Дополнительные сведения см. в разделе [Полный анализ решения](../../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md).

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