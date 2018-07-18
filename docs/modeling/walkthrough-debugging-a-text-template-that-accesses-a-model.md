---
title: Пошаговое руководство. Отладка текстового шаблона, обращающегося к модели
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 560849eaeefc8efd8337cbc98ad3de91e4d15fd9
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
ms.locfileid: "31968124"
---
# <a name="walkthrough-debugging-a-text-template-that-accesses-a-model"></a>Пошаговое руководство. Отладка текстового шаблона, обращающегося к модели
При изменении или добавлении текстовых шаблонов в решении доменный язык, могут возникнуть ошибки, когда обработчик преобразует шаблона к исходному коду, или во время компиляции созданного кода. Следующий пример демонстрирует некоторые задачи, которые можно выполнить отладку текстового шаблона.

> [!NOTE]
>  Дополнительные сведения о тексте шаблонов в общем случае см. раздел [создание кода и текстовые шаблоны T4](../modeling/code-generation-and-t4-text-templates.md). Дополнительные сведения об отладке текстовых шаблонов см. в разделе [Пошаговое руководство: отладка текстового шаблона](http://msdn.microsoft.com/Library/5c3fd3b7-c110-4e86-a22f-d5756be6b94f).

## <a name="creating-a-domain-specific-language-solution"></a>Создание решения доменного языка
 В этой процедуре создается решение доменный язык, имеет следующие характеристики:

-   Имя: DebuggingTestLanguage

-   Шаблон решения: минимальный языка

-   Расширение файла: .ddd

-   Название организации: Fabrikam

 Дополнительные сведения о создании решений доменного языка см. в разделе [как: создание решения доменный язык](../modeling/how-to-create-a-domain-specific-language-solution.md).

## <a name="creating-a-text-template"></a>Создание текстового шаблона
 Добавьте в текстовый шаблон в решение.

#### <a name="to-create-a-text-template"></a>Создание текстового шаблона

1.  Выполните сборку решения и начать его выполнение в отладчике. (На **построения** меню, нажмите кнопку **Перестроить решение**, а затем на **отладки** меню, нажмите кнопку **начать отладку**.) Новый экземпляр Visual Studio откроется проект отладка.

2.  Добавьте текстовый файл с именем `DebugTest.tt` для отладки проекта.

3.  Убедитесь, что **пользовательский инструмент** из файл DebugTest.tt свойству `TextTemplatingFileGenerator`.

## <a name="debugging-directives-that-access-a-model-from-a-text-template"></a>Отладка директивы, доступ к модели из текстового шаблона
 Модели можно получить из инструкции и выражения в текстовом шаблоне, необходимо сначала вызвать созданный процессора директив. Вызов созданного процессора директив делает классы в модели для код текстового шаблона как свойства. Дополнительные сведения см. в разделе [доступ к модели из текстовых шаблонов](../modeling/accessing-models-from-text-templates.md).

 В следующих процедурах необходимо отладить неверное имя директивы и имя свойства.

#### <a name="to-debug-an-incorrect-directive-name"></a>Для отладки неверное имя директивы

1.  Замените код в файл DebugTest.tt следующим кодом:

    > [!NOTE]
    >  Код содержит ошибку. Чтобы выполнить отладку этого Представляем ошибку.

    ```csharp
    <#@ template language="C#" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation"#>
    <#@ output extension=".txt" #>
    <#@ modelRoot processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=ExampleModel" #>

    Model: <#= this.ExampleModel #>
    <#
    foreach (ExampleElement element in this.ExampleModel.Elements)
    {
    #>
        Element: <#= element.Name #>
    <#
    }
    #>
    ```

    ```vb
    <#@ template language="VB" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation"#>
    <#@ output extension=".txt" #>
    <#@ modelRoot processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=ExampleModel" #>

    Model: <#= Me.ExampleModel #>
    <#
    For Each element as ExampleElement in Me.ExampleModel.Elements
    #>
        Element: <#= element.Name #>
    <#
    Next
    #>
    ```

2.  В **обозревателе решений**, щелкните правой кнопкой мыши файл DebugTest.tt и нажмите кнопку **запустить пользовательский инструмент**.

     **Список ошибок** окне отображаются ошибки:

     **Процессор с именем «DebuggingTestLanguageDirectiveProcessor» не поддерживает директиву с именем «modelRoot». Преобразование не будет выполнено.**

     В этом случае вызова директивы содержит неверное имя директивы. Вы указали `modelRoot` как имя директивы, но правильное имя директивы `DebuggingTestLanguage`.

3.  Дважды щелкните ошибку в **список ошибок** окна, чтобы перейти к коду.

4.  Чтобы исправить код, измените имя директивы для `DebuggingTestLanguage`.

     Это изменение будет выделен.

    ```csharp
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=ExampleModel" #>
    ```

    ```vb
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=ExampleModel" #>
    ```

5.  В **обозревателе решений**, щелкните правой кнопкой мыши файл DebugTest.tt и нажмите кнопку **запустить пользовательский инструмент**.

     Теперь система преобразует текстовый шаблон и создает соответствующий выходной файл. Вы увидите не все ошибки в **список ошибок** окна.

#### <a name="to-debug-an-incorrect-property-name"></a>Для имени свойства отладки

1.  Замените код в файл DebugTest.tt следующим кодом:

    > [!NOTE]
    >  Код содержит ошибку. Чтобы выполнить отладку этого Представляем ошибку.

    ```csharp
    <#@ template language="C#" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation"#>
    <#@ output extension=".txt" #>
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=LibraryModel" #>

    Model: <#= this.ExampleModel #>
    <#
    foreach (ExampleElement element in this.ExampleModel.Elements)
    {
    #>
        Element: <#= element.Name #>
    <#
    }
    #>
    ```

    ```vb
    <#@ template language="VB" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation"#>
    <#@ output extension=".txt" #>
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=LibraryModel" #>

    Model: <#= Me.ExampleModel #>
    <#
    For Each element as ExampleElement in Me.ExampleModel.Elements
    #>
        Element: <#= element.Name #>
    <#
    Next
    #>
    ```

2.  В **обозревателе решений**, щелкните правой кнопкой мыши файл DebugTest.tt и нажмите кнопку **запустить пользовательский инструмент**.

     **Список ошибок** появляется окно и отображает одно из следующих ошибок:

     (C#)

     **Компиляция преобразования: Microsoft.VisualStudio.TextTemplating\<GUID >. GeneratedTextTransformation "не содержит определение для «ExampleModel»**

     (Visual Basic)

     **Компиляция преобразования: «ExampleModel» не является членом "Microsoft.VisualStudio.TextTemplating\<GUID >. GeneratedTextTransformation ".**

     В этом случае код текстового шаблона содержит имя свойства. Вы указали `ExampleModel` как имя свойства, но свойство правильное имя — `LibraryModel`. Можно найти правильное имя свойства в поле параметра, как показано в следующем коде:

    ```
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=LibraryModel" #>
    ```

3.  Дважды щелкните ошибку в окне списка ошибок, чтобы перейти к коду.

4.  Чтобы исправить код, измените имя свойства для `LibraryModel` в код текстового шаблона.

     Изменения выделены.

    ```csharp
    <#@ template language="C#" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation"#>
    <#@ output extension=".txt" #>
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=LibraryModel" #>

    Model: <#= this.LibraryModel #>
    <#
    foreach (ExampleElement element in this.LibraryModel.Elements)
    {
    #>
        Element: <#= element.Name #>
    <#
    }
    #>
    ```

    ```vb
    <#@ template language="VB" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation"#>
    <#@ output extension=".txt" #>
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=LibraryModel" #>

    Model: <#= Me.LibraryModel #>
    <#
    For Each element as ExampleElement in Me.LibraryModel.Elements
    #>
        Element: <#= element.Name #>
    <#
    Next
    #>
    ```

5.  В **обозревателе решений**, щелкните правой кнопкой мыши файл DebugTest.tt и нажмите кнопку **запустить пользовательский инструмент**.

     Теперь система преобразует текстовый шаблон и создает соответствующий выходной файл. Вы увидите не все ошибки в **список ошибок** окна.