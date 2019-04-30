---
title: Пошаговое руководство. Отладка текстового шаблона, обращающегося к модели
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7e8b1ff717931286c5aa3aaaa69510ce05fb39a6
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63385977"
---
# <a name="walkthrough-debugging-a-text-template-that-accesses-a-model"></a>Пошаговое руководство. Отладка текстового шаблона, обращающегося к модели
При изменении или добавлении текстовых шаблонов в решении доменного языка, могут возникнуть ошибки, когда обработчик преобразует шаблон к исходному коду, или при компиляции созданного кода. Следующий пример демонстрирует некоторые из вещей, которые можно сделать, чтобы отладка текстового шаблона.

> [!NOTE]
> Дополнительные сведения о тексте шаблоны в целом, см. в разделе [создание кода и текстовые шаблоны T4](../modeling/code-generation-and-t4-text-templates.md). Дополнительные сведения об отладке текстовых шаблонов см. в разделе [Пошаговое руководство: Отладка текстового шаблона](debugging-a-t4-text-template.md).

## <a name="creating-a-domain-specific-language-solution"></a>Создание решений предметно ориентированного языка
 В этой процедуре вы создадите решение предметно ориентированного языка, которое имеет следующие характеристики:

- Имя. DebuggingTestLanguage

- Шаблон решения: Минимальный язык

- Расширение файла: .ddd

- Название организации: Fabrikam

  Дополнительные сведения о создании решений предметно ориентированного языка см. в разделе [как: создать решение на предметно-ориентированном языке](../modeling/how-to-create-a-domain-specific-language-solution.md).

## <a name="creating-a-text-template"></a>Создание текстового шаблона
 Добавьте текстовый шаблон в решение.

#### <a name="to-create-a-text-template"></a>Создание текстового шаблона

1. Выполните сборку решения и начать его выполнение в отладчике. (На **построения** меню, щелкните **Перестроить решение**, а затем на **Отладка** меню, нажмите кнопку **начать отладку**.) Новый экземпляр Visual Studio откроется проект "Отладка".

2. Добавьте в текстовый файл с именем `DebugTest.tt` на проект "Отладка".

3. Убедитесь, что **пользовательское средство** присваивается свойству файл DebugTest.tt `TextTemplatingFileGenerator`.

## <a name="debugging-directives-that-access-a-model-from-a-text-template"></a>Отладка директивы, которые обращаются к модели из текстового шаблона
 Для доступа к модели из эти инструкции и выражения в текстовом шаблоне, необходимо сначала вызвать генерируемым обработчиком директив. Вызов генерируемым обработчиком директив поставляет классы в модели в код текстового шаблона как свойства. Дополнительные сведения см. в разделе [доступ к моделям из текстовых шаблонов](../modeling/accessing-models-from-text-templates.md).

 В следующих процедурах необходимо отладить неверное имя директивы и неверным именем свойства.

#### <a name="to-debug-an-incorrect-directive-name"></a>Для отладки неверное имя директивы

1. Замените код в файл DebugTest.tt следующим кодом:

    > [!NOTE]
    > Код содержит ошибку. Чтобы выполнить его отладку Представляем ошибку.

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

2. В **обозревателе решений**, щелкните правой кнопкой мыши файл DebugTest.tt и нажмите кнопку **пользовательское средство**.

     **Список ошибок** окно отображает эту ошибку:

     **Процессор с именем «DebuggingTestLanguageDirectiveProcessor» не поддерживает директиву с именем «modelRoot». Преобразование не будет выполнено.**

     В этом случае вызова директивы содержит неверное имя директивы. Вы указали `modelRoot` как имя директивы, но правильное имя директивы по `DebuggingTestLanguage`.

3. Дважды щелкните ошибку в **список ошибок** окно, чтобы перейти к коду.

4. Чтобы исправить код, измените имя директивы для `DebuggingTestLanguage`.

     Изменение будет выделен.

    ```csharp
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=ExampleModel" #>
    ```

    ```vb
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=ExampleModel" #>
    ```

5. В **обозревателе решений**, щелкните правой кнопкой мыши файл DebugTest.tt и нажмите кнопку **пользовательское средство**.

     Теперь система преобразует текстовый шаблон и создает соответствующий файл выходных данных. Вы не увидите все ошибки в **список ошибок** окна.

#### <a name="to-debug-an-incorrect-property-name"></a>Для отладки неверным именем свойства

1. Замените код в файл DebugTest.tt следующим кодом:

    > [!NOTE]
    > Код содержит ошибку. Чтобы выполнить его отладку Представляем ошибку.

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

2. В **обозревателе решений**, щелкните правой кнопкой мыши файл DebugTest.tt и нажмите кнопку **пользовательское средство**.

     **Список ошибок** окна появляется и отображает одно из следующих ошибок:

     (C#)

     **Компиляция преобразования: Microsoft.VisualStudio.TextTemplating\<GUID>. GeneratedTextTransformation "содержит определение для «ExampleModel»**

     (Visual Basic)

     **Компиляция преобразования: «ExampleModel» не является членом "Microsoft.VisualStudio.TextTemplating\<GUID >. GeneratedTextTransformation ".**

     В этом случае код текстового шаблона содержит неверным именем свойства. Вы указали `ExampleModel` как имя свойства, но правильного свойства является имя `LibraryModel`. Можно найти правильное название свойства в поле параметра, как показано в следующем коде:

    ```
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=LibraryModel" #>
    ```

3. Дважды щелкните ошибку в окне списка ошибок, чтобы перейти к коду.

4. Чтобы исправить код, измените имя свойства в `LibraryModel` в код текстового шаблона.

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

5. В **обозревателе решений**, щелкните правой кнопкой мыши файл DebugTest.tt и нажмите кнопку **пользовательское средство**.

     Теперь система преобразует текстовый шаблон и создает соответствующий файл выходных данных. Вы не увидите все ошибки в **список ошибок** окна.