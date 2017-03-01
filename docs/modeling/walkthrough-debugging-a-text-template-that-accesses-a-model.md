---
title: "Пошаговое руководство: Отладка текстового шаблона, который обращается к модели | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: af46a7fe-6b98-4d3d-b816-0bbf8e81e220
caps.latest.revision: 6
author: alancameronwills
ms.author: awills
manager: douge
translationtype: Machine Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: 7bbe2b592dc315bc0885e1f1ca4c890e4e66255d
ms.lasthandoff: 02/22/2017

---
# <a name="walkthrough-debugging-a-text-template-that-accesses-a-model"></a>Пошаговое руководство. Отладка текстового шаблона, обращающегося к модели
При изменении или добавлении текстовых шаблонов в решении доменного языка, могут возникнуть ошибки, когда обработчик преобразует шаблон к исходному коду, или во время компиляции созданного кода. Следующий пример демонстрирует некоторые из вещей, которые можно сделать для отладки текстового шаблона.  
  
> [!NOTE]
>  Дополнительные сведения о тексте шаблоны в общем разделе [создание кода и текстовые шаблоны T4](../modeling/code-generation-and-t4-text-templates.md). Дополнительные сведения об отладке текстовых шаблонов см. в разделе [Пошаговое руководство: отладка текстового шаблона](http://msdn.microsoft.com/Library/5c3fd3b7-c110-4e86-a22f-d5756be6b94f).  
  
## <a name="creating-a-domain-specific-language-solution"></a>Создание доменного языка  
 В этой процедуре создается решение доменного языка, которое имеет следующие характеристики:  
  
-   Имя: DebuggingTestLanguage  
  
-   Шаблон решения: минимальный язык  
  
-   Расширение файла: .ddd  
  
-   Название организации: Fabrikam  
  
 Дополнительные сведения о создании решений доменного языка см. в разделе [как: создайте решение доменного языка](../modeling/how-to-create-a-domain-specific-language-solution.md).  
  
## <a name="creating-a-text-template"></a>Создание текстового шаблона  
 Добавьте в текстовый шаблон в решение.  
  
#### <a name="to-create-a-text-template"></a>Создание текстового шаблона  
  
1.  Постройте решение и запустить его выполнение в отладчике. (На **построения** меню, щелкните **Перестроить решение**, а затем на **отладки** меню, нажмите кнопку **начать отладку**.) Новый экземпляр Visual Studio откроется проект "Отладка".  
  
2.  Добавьте текстовый файл с именем `DebugTest.tt` для отладки проекта.  
  
3.  Убедитесь, что **пользовательское средство** файл DebugTest.tt свойств `TextTemplatingFileGenerator`.  
  
## <a name="debugging-directives-that-access-a-model-from-a-text-template"></a>Отладка директивы, доступ к модели из текстового шаблона  
 Модели можно получить из инструкции и выражения в текстовом шаблоне, необходимо сначала вызвать созданный процессора директив. Вызов созданного процессор директив делает классы в модели для код текстового шаблона как свойства. Дополнительные сведения см. в разделе [доступ к моделям из текстовых шаблонов](../modeling/accessing-models-from-text-templates.md).  
  
 В следующей процедуре вы отладите неверное имя директивы и неверным именем свойства.  
  
#### <a name="to-debug-an-incorrect-directive-name"></a>Для отладки неверное имя директивы  
  
1.  Замените код в файл DebugTest.tt следующим кодом:  
  
    > [!NOTE]
    >  Код содержит ошибку. Эта ошибка вводится для его отладки.  
  
    ```c#  
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
  
    ```vb#  
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
  
2.  В **обозревателе решений**, щелкните правой кнопкой мыши файл DebugTest.tt и нажмите кнопку **пользовательское средство**.  
  
     **Список ошибок** окно отображает эту ошибку:  
  
     **Процессор с именем «DebuggingTestLanguageDirectiveProcessor» не поддерживает директиву с именем «modelRoot». Преобразование не будет выполняться.**  
  
     В этом случае вызова директивы содержит неверное имя директивы. Вы указали `modelRoot` как имя директивы, но правильное имя директивы `DebuggingTestLanguage`.  
  
3.  Дважды щелкните ошибку в **список ошибок** окно, чтобы перейти к коду.  
  
4.  Чтобы исправить код, измените имя директивы для `DebuggingTestLanguage`.  
  
     Изменения выделены.  
  
    ```c#  
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=ExampleModel" #>  
    ```  
  
    ```vb#  
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=ExampleModel" #>  
    ```  
  
5.  В **обозревателе решений**, щелкните правой кнопкой мыши файл DebugTest.tt и нажмите кнопку **пользовательское средство**.  
  
     Теперь система преобразует текстовый шаблон и сгенерирует соответствующий выходной файл. Вы увидите не все ошибки в **список ошибок** окна.  
  
#### <a name="to-debug-an-incorrect-property-name"></a>Для отладки неверным именем свойства  
  
1.  Замените код в файл DebugTest.tt следующим кодом:  
  
    > [!NOTE]
    >  Код содержит ошибку. Эта ошибка вводится для его отладки.  
  
    ```c#  
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
  
    ```vb#  
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
  
2.  В **обозревателе решений**, щелкните правой кнопкой мыши файл DebugTest.tt и нажмите кнопку **пользовательское средство**.  
  
     **Список ошибок** окна появляется и отображает один из этих ошибок:  
  
     (C#)  
  
     **Компиляция преобразования: Microsoft.VisualStudio.TextTemplating\<GUID настроек. GeneratedTextTransformation "не содержит определение для «ExampleModel»**  
  
     (Visual Basic)  
  
     **Компиляция преобразования: «ExampleModel» не является членом "Microsoft.VisualStudio.TextTemplating\<GUID настроек. GeneratedTextTransformation ".**  
  
     В этом случае код текстового шаблона содержит неверным именем свойства. Вы указали `ExampleModel` как имя свойства, но свойство правильное имя — `LibraryModel`. Можно найти правильное имя свойства в предоставляет параметр, как показано в следующем коде:  
  
    ```  
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=LibraryModel" #>  
    ```  
  
3.  Дважды щелкните ошибку в окне списка ошибок, чтобы перейти к коду.  
  
4.  Чтобы исправить код, измените имя свойства в `LibraryModel` в код текстового шаблона.  
  
     Изменения выделены.  
  
    ```c#  
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
  
    ```vb#  
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
  
5.  В **обозревателе решений**, щелкните правой кнопкой мыши файл DebugTest.tt и нажмите кнопку **пользовательское средство**.  
  
     Теперь система преобразует текстовый шаблон и сгенерирует соответствующий выходной файл. Вы увидите не все ошибки в **список ошибок** окна.
