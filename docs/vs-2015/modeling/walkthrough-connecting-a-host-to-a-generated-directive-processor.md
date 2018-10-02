---
title: 'Пошаговое руководство: Связывание основного приложения с генерируемым обработчиком директив | Документация Майкрософт'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- walkthroughs [text templates], connecting host to processor
- text templates, custom directive hosts
ms.assetid: 254540d9-90d6-42de-8c1c-068affd56e83
caps.latest.revision: 49
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 451dcf21e8965de9ea350577c819daefb150a5d1
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47559455"
---
# <a name="walkthrough-connecting-a-host-to-a-generated-directive-processor"></a>Пошаговое руководство. Связывание основного приложения с генерируемым обработчиком директив
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [Пошаговое руководство: подключение узла к процессора директив создается](https://docs.microsoft.com/visualstudio/modeling/walkthrough-connecting-a-host-to-a-generated-directive-processor).  
  
Вы можете написать собственный узел, который обрабатывает текстовые шаблоны. Демонстрируется базовый пользовательского ведущего приложения в [Пошаговое руководство: Создание пользовательского хост текстовых шаблонов](../modeling/walkthrough-creating-a-custom-text-template-host.md). Можно расширить для добавления функций, таких как создание нескольких выходных файлов, на которых размещены.  
  
 В этом пошаговом руководстве разверните вашего пользовательского ведущего приложения так, чтобы она поддерживала текстовые шаблоны, которые вызывают процессоры директив. При определении доменного языка, он создает *процессора директив* для доменной модели. Процессор директив помогает пользователям создавать шаблоны, которые обращаются к модели, уменьшая необходимость создать сборку и импортировать директивы в шаблонах.  
  
> [!WARNING]
>  Это пошаговое руководство построено [Пошаговое руководство: Создание пользовательского хост-класса шаблона текста](../modeling/walkthrough-creating-a-custom-text-template-host.md). Сначала выполните для этого пошагового руководства.  
  
 В этом пошаговом руководстве рассматриваются следующие задачи:  
  
-   С помощью [!INCLUDE[dsl](../includes/dsl-md.md)] для создания процессора директив, основанный на модели домена.  
  
-   Связывание основного приложения пользовательский текстовый шаблон генерируемым обработчиком директив.  
  
-   Тестирование пользовательского ведущего приложения с генерируемым обработчиком директив.  
  
## <a name="prerequisites"></a>Предварительные требования  
 Для определения доменного языка необходимо установить следующие компоненты.  
  
|||  
|-|-|  
|[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]|[http://go.microsoft.com/fwlink/?LinkId=185579](http://go.microsoft.com/fwlink/?LinkId=185579)|  
|[!INCLUDE[vssdk_current_short](../includes/vssdk-current-short-md.md)]|[http://go.microsoft.com/fwlink/?LinkId=185580](http://go.microsoft.com/fwlink/?LinkId=185580)|  
|Пакет SDK для визуализации и моделирования в Visual Studio|[http://go.microsoft.com/fwlink/?LinkID=186128](http://go.microsoft.com/fwlink/?LinkID=186128)|  
  
 Кроме того, необходимо иметь преобразование настраиваемых текстовых шаблонов, созданных в [Пошаговое руководство: Создание пользовательского хост текстовых шаблонов](../modeling/walkthrough-creating-a-custom-text-template-host.md).  
  
## <a name="using-domain-specific-language-tools-to-generate-a-directive-processor"></a>Использование средств доменного языка для создания процессора директив  
 В этом пошаговом руководстве использовать мастера конструктора доменного языка для создания доменного языка для решения DSLMinimalTest.  
  
#### <a name="to-use-domain-specific-language-tools-to-generate-a-directive-processor-that-is-based-on-a-domain-model"></a>Использование средства доменного языка для создания процессора директив, основанный на модели домена  
  
1.  Создайте решение доменного языка, которое имеет следующие характеристики:  
  
    -   Имя: DSLMinimalTest  
  
    -   Шаблон решения: минимальный язык  
  
    -   Расширение файла: мин.  
  
    -   Название компании: Fabrikam  
  
     Дополнительные сведения о создании решений предметно ориентированного языка см. в разделе [как: создайте решение доменного языка](../modeling/how-to-create-a-domain-specific-language-solution.md).  
  
2.  В меню **Сборка** выберите **Собрать решение**.  
  
    > [!IMPORTANT]
    >  Этот шаг создает процессора директив и добавляет ключ для него в реестре.  
  
3.  В меню **Отладка** щелкните **Начать отладку**.  
  
     Второй экземпляр [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] открывает.  
  
4.  В экспериментальном построении в **обозревателе решений**, дважды щелкните файл **sample.min**.  
  
     Файл откроется в конструкторе. Обратите внимание на то, что модель имеет два элемента, ExampleElement1 и ExampleElement2 и связь между ними.  
  
5.  Закройте второй экземпляр [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
6.  Сохраните решение, а затем закройте конструктор доменного языка.  
  
## <a name="connecting-a-custom-text-template-host-to-a-directive-processor"></a>Связывание основного приложения пользовательский текстовый шаблон процессора директив  
 После создания процессор директив, подключении процессора директив и основное приложение текстового шаблона, созданный в [Пошаговое руководство: Создание пользовательского хост текстовых шаблонов](../modeling/walkthrough-creating-a-custom-text-template-host.md).  
  
#### <a name="to-connect-a-custom-text-template-host-to-the-generated-directive-processor"></a>Для подключения пользовательского хост текстовых шаблонов генерируемым обработчиком директив  
  
1.  Откройте решение CustomHost.  
  
2.  В меню **Проект** щелкните команду **Добавить ссылку**.  
  
     **Добавить ссылку** откроется диалоговое окно с **.NET** отображается вкладка.  
  
3.  Добавьте следующие ссылки:  
  
    -   Microsoft.VisualStudio.Modeling.Sdk.11.0  
  
    -   Microsoft.VisualStudio.Modeling.Sdk.Diagrams.11.0  
  
    -   Microsoft.VisualStudio.TextTemplating.11.0  
  
    -   Microsoft.VisualStudio.TextTemplating.Interfaces.11.0  
  
    -   Microsoft.VisualStudio.TextTemplating.Modeling.11.0  
  
    -   Microsoft.VisualStudio.TextTemplating.VSHost.11.0  
  
4.  В верхней части Program.cs или Module1.vb добавьте следующую строку кода:  
  
    ```csharp  
    using Microsoft.Win32;  
    ```  
  
    ```vb  
    Imports Microsoft.Win32  
    ```  
  
5.  Найдите код для свойства `StandardAssemblyReferences`и замените его следующим кодом:  
  
    > [!NOTE]
    >  На этом шаге добавьте ссылки на сборки, которые требуются генерируемым обработчиком директив, которые будет поддерживать ваш узел.  
  
    ```csharp  
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
    >  Этот код содержит жестко запрограммированные ссылки на имя генерируемым обработчиком директив, к которому необходимо подключиться. Можно легко сделать это более общие, в этом случае он ищет все процессоры директив, перечисленных в реестре и пытается найти совпадение. В этом случае узел будет работать с любой генерируемым обработчиком директив.  
  
    ```csharp  
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
  
## <a name="testing-the-custom-host-with-the-directive-processor"></a>Тестирование пользовательского ведущего приложения с помощью процессора директив  
 Чтобы протестировать пользовательский текстовый шаблон узла, необходимо написать текстовый шаблон, который вызывает генерируемым обработчиком директив. Затем вы запустите пользовательское ведущее, передайте в него имя текстового шаблона и убедитесь, что директива будут обработаны правильно.  
  
#### <a name="to-create-a-text-template-to-test-the-custom-host"></a>Создание текстового шаблона для тестирования пользовательского ведущего приложения  
  
1.  Создайте текстовый файл и назовите его `TestTemplateWithDP.tt`. Можно использовать любой текстовый редактор, например в блокноте, чтобы создать файл.  
  
2.  Добавьте в текстовый файл следующий текст:  
  
    > [!NOTE]
    >  Язык программирования текстового шаблона не совпадали с пользовательского ведущего приложения.  
  
    ```csharp  
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
  
    ```vb  
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
  
3.  В коде, замените \<ВАШ путь > путь к файлу Sample.min из конструктора ориентированного языка, созданной в первой процедуре.  
  
4.  Сохраните и закройте файл.  
  
#### <a name="to-test-the-custom-host"></a>Тестирование пользовательского ведущего приложения  
  
1.  Откройте окно командной строки.  
  
2.  Введите путь к исполняемому файлу пользовательского ведущего приложения, но пока не нажимайте клавишу ВВОД.  
  
     Например, введите:  
  
     `<YOUR PATH>CustomHost\bin\Debug\CustomHost.exe`  
  
    > [!NOTE]
    >  Вместо того чтобы вводить адрес, вы можно найти файл CustomHost.exe в **Windows Explorer**, а затем перетащите файл в окне командной строки.  
  
3.  Введите пробел.  
  
4.  Введите путь к файлу текстового шаблона и нажмите клавишу ВВОД.  
  
     Например, введите:  
  
     `<YOUR PATH>TestTemplateWithDP.txt`  
  
    > [!NOTE]
    >  Вместо того чтобы вводить адрес, можно просмотреть в файле TestTemplateWithDP.txt в **Windows Explorer**, а затем перетащите файл в окне командной строки.  
  
     Пользовательское ведущее приложение запускается и начинает процесс преобразования текстового шаблона.  
  
5.  В **Windows Explorer**, перейдите к папке, содержащей файл TestTemplateWithDP.txt.  
  
     Папка также содержит файл TestTemplateWithDP1.txt.  
  
6.  Откройте этот файл, чтобы увидеть результаты преобразования текстового шаблона.  
  
     Результаты в создаваемый выходной текст отображается, а должен выглядеть следующим образом:  
  
    ```  
    Text Template Host Test  
  
    Box: ExampleElement1  
    Linked to: ExampleElement2  
  
    Box: ExampleElement2  
    Linked from: ExampleElement1  
    ```  
  
## <a name="see-also"></a>См. также  
 [Пошаговое руководство. Создание пользовательского хост-класса для текстовых шаблонов](../modeling/walkthrough-creating-a-custom-text-template-host.md)



