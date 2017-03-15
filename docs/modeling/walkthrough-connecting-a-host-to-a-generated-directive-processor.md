---
title: "Пошаговое руководство: Подключение узла созданный процессора директив | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- walkthroughs [text templates], connecting host to processor
- text templates, custom directive hosts
ms.assetid: 254540d9-90d6-42de-8c1c-068affd56e83
caps.latest.revision: 47
author: alancameronwills
ms.author: awills
manager: douge
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 3d07f82ea737449fee6dfa04a61e195654ba35fa
ms.openlocfilehash: 3cdbd2adb7b956849e5582e8a5b1ca80a6f5166d
ms.lasthandoff: 02/22/2017

---
# <a name="walkthrough-connecting-a-host-to-a-generated-directive-processor"></a>Пошаговое руководство. Связывание основного приложения с генерируемым обработчиком директив
Можно написать собственный узел, который обрабатывает текстовые шаблоны. Демонстрируется базовый пользовательское основное приложение в [Пошаговое руководство: создание пользовательское основное приложение текстового шаблона](../modeling/walkthrough-creating-a-custom-text-template-host.md). Вы можете расширить этот узел для добавления функций, таких как создание нескольких выходных файлов.  
  
 В этом пошаговом руководстве разверните пользовательское основное приложение, чтобы он поддерживал текстовых шаблонов, которые вызывают процессоры директив. При определении доменного языка, он создает *процессора директив* для модели домена. Процессор директив упрощает запись шаблонов, доступ к модели, избавляя от необходимости писать сборки и импортировать директивы в шаблонах.  
  
> [!WARNING]
>  В этом пошаговом руководстве основано руководство [Пошаговое руководство: Создание пользовательского хост-класса шаблона текста](../modeling/walkthrough-creating-a-custom-text-template-host.md). Сначала выполните для этого пошагового руководства.  
  
 В этом пошаговом руководстве рассматриваются следующие задачи:  
  
-   С помощью [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] для создания процессор директив, который основан на модели домена.  
  
-   Подключение основное приложение текстового шаблона созданный процессора директив.  
  
-   Тестирование пользовательского основного приложения с генерируемым обработчиком директив.  
  
## <a name="prerequisites"></a>Предварительные требования  
 Для определения доменного языка необходимо установить следующие компоненты.  
  
|||  
|-|-|  
|[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]|[http://go.Microsoft.com/fwlink/?LinkId=185579](http://go.microsoft.com/fwlink/?LinkId=185579)|  
|[!INCLUDE[vssdk_current_short](../modeling/includes/vssdk_current_short_md.md)]|[http://go.Microsoft.com/fwlink/?LinkId=185580](http://go.microsoft.com/fwlink/?LinkId=185580)|  
|Пакет SDK для визуализации и моделирования в Visual Studio||  

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
  
 Кроме того, необходимо иметь преобразования пользовательских текстовых шаблонов, созданных в [Пошаговое руководство: создание пользовательское основное приложение текстового шаблона](../modeling/walkthrough-creating-a-custom-text-template-host.md).  
  
## <a name="using-domain-specific-language-tools-to-generate-a-directive-processor"></a>Создание процессора директив с помощью средств доменного языка  
 В этом пошаговом руководстве используется мастер конструктора доменного языка для создания доменного языка для решения DSLMinimalTest.  
  
#### <a name="to-use-domain-specific-language-tools-to-generate-a-directive-processor-that-is-based-on-a-domain-model"></a>Для использования средств доменного языка для создания процессор директив, который основан на модели домена  
  
1.  Создайте решение доменного языка, которое имеет следующие характеристики:  
  
    -   Имя: DSLMinimalTest  
  
    -   Шаблон решения: минимальный язык  
  
    -   Расширение файла: мин.  
  
    -   Название организации: Fabrikam  
  
     Дополнительные сведения о создании решений доменного языка см. в разделе [как: создайте решение доменного языка](../modeling/how-to-create-a-domain-specific-language-solution.md).  
  
2.  В меню **Сборка** выберите **Собрать решение**.  
  
    > [!IMPORTANT]
    >  Этот шаг создает процессор директив и добавляет ключ в реестре.  
  
3.  На **отладки** меню, щелкните **начать отладку**.  
  
     Второй экземпляр [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] открывает.  
  
4.  В экспериментальном построении в **обозревателе решений**, дважды щелкните файл **sample.min**.  
  
     Файл откроется в конструкторе. Обратите внимание, что модель имеет два элемента, ExampleElement1 и ExampleElement2 и связи между ними.  
  
5.  Закройте второй экземпляр [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
6.  Сохраните решение, а затем закройте конструктор доменного языка.  
  
## <a name="connecting-a-custom-text-template-host-to-a-directive-processor"></a>Подключение основное приложение текстового шаблона для процессора директив  
 После создания процессор директив подключении процессора директив и основное приложение текстового шаблона, созданный в [Пошаговое руководство: создание пользовательское основное приложение текстового шаблона](../modeling/walkthrough-creating-a-custom-text-template-host.md).  
  
#### <a name="to-connect-a-custom-text-template-host-to-the-generated-directive-processor"></a>Для подключения основное приложение текстового шаблона созданный процессора директив  
  
1.  Откройте решение CustomHost.  
  
2.  На **проекта** меню, щелкните **добавить ссылку**.  
  
     **Добавить ссылку** откроется диалоговое окно с **.NET** отображается вкладка.  
  
3.  Добавьте следующие ссылки:  
  
    -   Microsoft.VisualStudio.Modeling.Sdk.11.0  
  
    -   Microsoft.VisualStudio.Modeling.Sdk.Diagrams.11.0  
  
    -   Microsoft.VisualStudio.TextTemplating.11.0  
  
    -   Microsoft.VisualStudio.TextTemplating.Interfaces.11.0  
  
    -   Microsoft.VisualStudio.TextTemplating.Modeling.11.0  
  
    -   Microsoft.VisualStudio.TextTemplating.VSHost.11.0  
  
4.  В верхней части Program.cs или Module1.vb добавьте следующую строку кода:  
  
    ```c#  
    using Microsoft.Win32;  
    ```  
  
    ```vb#  
    Imports Microsoft.Win32  
    ```  
  
5.  Найдите код для свойства `StandardAssemblyReferences`и замените его следующим кодом:  
  
    > [!NOTE]
    >  На этом этапе добавить ссылки на сборки, необходимые созданный процессор директив, будут поддерживать вашего узла.  
  
    ```c#  
    //the host can provide standard assembly references  
    //the engine will use these references when compiling and  
    //executing the generated transformation class  
    //--------------------------------------------------------------  
    public IList<string> StandardAssemblyReferences  
    {  
        get  
        {  
            return new string[]  
            {  
                //if this host searches standard paths and the GAC  
                //we can specify the assembly name like this:  
                //"System"  
                //since this host only resolves assemblies from the   
                //fully qualified path and name of the assembly  
                //this is a quick way to get the code to give us the  
                //fully qualified path and name of the System assembly  
                //---------------------------------------------------------  
                typeof(System.Uri).Assembly.Location,  
                            typeof(System.Uri).Assembly.Location,  
                typeof(Microsoft.VisualStudio.Modeling.ModelElement).Assembly.Location,  
                typeof(Microsoft.VisualStudio.Modeling.Diagrams.BinaryLinkShape).Assembly.Location,  
                typeof(Microsoft.VisualStudio.TextTemplating.VSHost.ITextTemplating).Assembly.Location,  
                typeof(Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation).Assembly.Location  
  
            };  
        }  
    }  
    ```  
  
6.  Найдите код для функции `ResolveDirectiveProcessor`и замените его следующим кодом:  
  
    > [!IMPORTANT]
    >  Этот код содержит жестко запрограммированные ссылки на имя созданного процессор директив, к которому необходимо подключиться. Можно легко сделать это более общие, в этом случае он ищет все процессоры директив, перечисленных в реестре и пытается найти соответствие. В этом случае узел будет работать с любой созданный процессора директив.  
  
    ```c#  
    //the engine calls this method based on the directives the user has   
            //specified it in the text template  
            //this method can be called 0, 1, or more times  
            //---------------------------------------------------------------------  
            public Type ResolveDirectiveProcessor(string processorName)  
            {  
                //check the processor name, and if it is the name of the processor the   
                //host wants to support, return the type of the processor  
                //---------------------------------------------------------------------  
                if (string.Compare(processorName, "DSLMinimalTestDirectiveProcessor", StringComparison.InvariantCultureIgnoreCase) == 0)  
                {  
                    try  
                    {  
                        string keyName = @"Software\Microsoft\VisualStudio\10.0Exp_Config\TextTemplating\DirectiveProcessors\DSLMinimalTestDirectiveProcessor";  
                        using (RegistryKey specificKey = Registry.CurrentUser.OpenSubKey(keyName))  
                        {  
                            if (specificKey != null)  
                            {  
                                List<string> names = new List<String>(specificKey.GetValueNames());  
                                string classValue = specificKey.GetValue("Class") as string;  
                                if (!string.IsNullOrEmpty(classValue))  
                                {  
                                    string loadValue = string.Empty;  
                                    System.Reflection.Assembly processorAssembly = null;  
                                    if (names.Contains("Assembly"))  
                                    {  
                                        loadValue = specificKey.GetValue("Assembly") as string;  
                                        if (!string.IsNullOrEmpty(loadValue))  
                                        {  
                                            //the assembly must be installed in the GAC  
                                            processorAssembly = System.Reflection.Assembly.Load(loadValue);  
                                        }  
                                    }  
                                    else if (names.Contains("CodeBase"))  
                                    {  
                                        loadValue = specificKey.GetValue("CodeBase") as string;  
                                        if (!string.IsNullOrEmpty(loadValue))  
                                        {  
                                            //loading local assembly  
                                            processorAssembly = System.Reflection.Assembly.LoadFrom(loadValue);  
                                        }  
                                    }  
                                    if (processorAssembly == null)  
                                    {  
                                        throw new Exception("Directive Processor not found");  
                                    }  
                                    Type processorType = processorAssembly.GetType(classValue);  
                                    if (processorType == null)  
                                    {  
                                        throw new Exception("Directive Processor not found");  
                                    }  
                                    return processorType;  
                                }  
                            }  
                        }  
                    }  
                    catch (Exception e)  
                    {  
                        //if the directive processor can not be found, throw an error  
                        throw new Exception("Directive Processor not found");  
                    }  
                }  
  
                //if the directive processor is not one this host wants to support  
                throw new Exception("Directive Processor not supported");  
            }  
    ```  
  
7.  На **файл** меню, щелкните **сохранить все**.  
  
8.  В меню **Сборка** выберите **Собрать решение**.  
  
## <a name="testing-the-custom-host-with-the-directive-processor"></a>Тестирование пользовательского основного приложения с процессора директив  
 Чтобы проверить основное приложение текстового шаблона, необходимо написать текстовый шаблон, вызывает созданный процессор директив. Затем вы запустите пользовательское основное приложение, передать ему имя текстового шаблона и проверить, правильно обработан директивы.  
  
#### <a name="to-create-a-text-template-to-test-the-custom-host"></a>Создание текстового шаблона для тестирования пользовательского ведущего приложения  
  
1.  Создайте текстовый файл и назовите его `TestTemplateWithDP.tt`. Можно использовать любой текстовый редактор, например Блокнот, чтобы создать файл.  
  
2.  Добавьте в текстовый файл следующий текст:  
  
    > [!NOTE]
    >  Язык программирования текстового шаблона не должны совпадать с пользовательского основного приложения.  
  
    ```c#  
    Text Template Host Test  
  
    <#@ template debug="true" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation" #>  
    <# //this is the call to the examplemodel directive in the generated directive processor #>  
    <#@ DSLMinimalTest processor="DSLMinimalTestDirectiveProcessor" requires="fileName='<Your Path>\Sample.min'" provides="ExampleModel=ExampleModel" #>  
    <# //uncomment this line to test that the host allows the engine to set the extension #>  
    <# //@ output extension=".htm" #>  
  
    <# //uncomment this line if you want to see the generated transformation class #>  
    <# //System.Diagnostics.Debugger.Break(); #>  
    <# //this code uses the results of the examplemodel directive #>  
    <#  
        foreach ( ExampleElement box in this.ExampleModel.Elements )   
        {   
            WriteLine("Box: {0}", box.Name);  
  
            foreach (ExampleElement linkedTo in box.Targets)  
            {  
                WriteLine("Linked to: {0}", linkedTo.Name);  
            }  
  
            foreach (ExampleElement linkedFrom in box.Sources)  
            {  
                WriteLine("Linked from: {0}", linkedFrom.Name);  
            }  
  
            WriteLine("");  
        }   
    #>  
    ```  
  
    ```vb#  
    Text Template Host Test  
  
    <#@ template debug="true" language="VB" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation" #>  
  
    <# 'this is the call to the examplemodel directive in the generated directive processor #>  
    <#@ DSLMinimalTest processor="DSLMinimalTestDirectiveProcessor" requires="fileName='<Your Path>\Sample.min'" provides="ExampleModel=ExampleModel" #>  
  
    <# 'Uncomment this line to test that the host allows the engine to set the extension. #>  
    <# '@ output extension=".htm" #>  
  
    <# 'Uncomment this line if you want to see the generated transformation class. #>  
    <# 'System.Diagnostics.Debugger.Break() #>  
  
    <# 'this code uses the results of the examplemodel directive #>  
  
    <#      
       For Each box as ExampleElement In Me.ExampleModel.Elements   
  
           WriteLine("Box: {0}", box.Name)  
  
            For Each LinkedTo as ExampleElement In box.Targets  
                WriteLine("Linked to: {0}", LinkedTo.Name)  
            Next  
  
            For Each LinkedFrom as ExampleElement In box.Sources  
                WriteLine("Linked from: {0}", LinkedFrom.Name)  
            Next  
  
            WriteLine("")  
  
       Next   
    #>  
    ```  
  
3.  В коде, замените \<свой путь настроек с путь к файлу Sample.min от разработки конкретного языка, созданный в первой процедуре.  
  
4.  Сохраните и закройте файл.  
  
#### <a name="to-test-the-custom-host"></a>Тестирование пользовательского ведущего приложения  
  
1.  Откройте окно командной строки.  
  
2.  Введите путь к исполняемому файлу пользовательского ведущего приложения, но пока не нажимайте клавишу ВВОД.  
  
     Например, введите:  
  
     `<YOUR PATH>CustomHost\bin\Debug\CustomHost.exe`  
  
    > [!NOTE]
    >  Вместо того чтобы вводить адрес, можно просмотреть файл CustomHost.exe в **проводника Windows**, а затем перетащите файл в окне командной строки.  
  
3.  Введите пробел.  
  
4.  Введите путь к файлу текстового шаблона и нажмите клавишу ВВОД.  
  
     Например, введите:  
  
     `<YOUR PATH>TestTemplateWithDP.txt`  
  
    > [!NOTE]
    >  Вместо того чтобы вводить адрес, можно перейти к файлу TestTemplateWithDP.txt в **Windows Explorer**и перетащить его в окно командной строки.  
  
     Пользовательское основное приложение запускается и начинает процесс преобразования текстового шаблона.  
  
5.  В **Windows Explorer**, перейдите к папке, содержащей файл TestTemplateWithDP.txt.  
  
     Папка также содержит файл TestTemplateWithDP1.txt.  
  
6.  Откройте этот файл, чтобы увидеть результаты преобразования текстового шаблона.  
  
     Сгенерированный текстовый вывод результатов отображается и должен выглядеть следующим образом:  
  
    ```  
    Text Template Host Test  
  
    Box: ExampleElement1  
    Linked to: ExampleElement2  
  
    Box: ExampleElement2  
    Linked from: ExampleElement1  
    ```  
  
## <a name="see-also"></a>См. также  
 [Пошаговое руководство. Создание пользовательского хост-класса для текстовых шаблонов](../modeling/walkthrough-creating-a-custom-text-template-host.md)

