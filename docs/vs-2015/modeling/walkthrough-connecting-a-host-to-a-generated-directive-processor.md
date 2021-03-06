---
title: Пошаговое руководство. подключение узла к созданному обработчику директив | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- walkthroughs [text templates], connecting host to processor
- text templates, custom directive hosts
ms.assetid: 254540d9-90d6-42de-8c1c-068affd56e83
caps.latest.revision: 49
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 17ec8199e99e76d5995e49570c82ad8523505ebe
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/13/2020
ms.locfileid: "75915995"
---
# <a name="walkthrough-connecting-a-host-to-a-generated-directive-processor"></a>Пошаговое руководство. Связывание основного приложения с генерируемым обработчиком директив
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Можно написать собственный узел, обрабатывающий текстовые шаблоны. Базовый пользовательский узел демонстрируется в [разделе Пошаговое руководство. Создание узла пользовательского текстового шаблона](../modeling/walkthrough-creating-a-custom-text-template-host.md). Можно расширить этот узел, добавив в него такие функции, как создание нескольких выходных файлов.

 В этом пошаговом руководстве вы развернете пользовательский узел, чтобы он поддерживал текстовые шаблоны, вызывающие обработчики директив. При определении доменного языка он создает *процессор директив* для модели предметной области. Процессор директив упрощает для пользователей написание шаблонов, обращающихся к модели, уменьшая необходимость написания директив сборки и импорта в шаблонах.

> [!WARNING]
> В этом пошаговом руководстве строится [Пошаговое руководство. Создание узла пользовательского текстового шаблона](../modeling/walkthrough-creating-a-custom-text-template-host.md). Сначала выполните это пошаговое руководство.

 В этом пошаговом руководстве рассматриваются следующие задачи:

- Использование [!INCLUDE[dsl](../includes/dsl-md.md)] для создания процессора директив, основанного на модели предметной области.

- Подключение узла пользовательского текстового шаблона к созданному обработчику директив.

- Тестирование пользовательского узла с помощью созданного обработчика директив.

## <a name="prerequisites"></a>Prerequisites
 Для определения доменного языка необходимо установить следующие компоненты.

|||
|-|-|
|[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]|[https://www.visualstudio.com/](https://www.visualstudio.com/)|
|[!INCLUDE[vssdk_current_short](../includes/vssdk-current-short-md.md)]|[Пакет SDK для Visual Studio](../extensibility/visual-studio-sdk.md)|
|Пакет SDK для визуализации и моделирования в Visual Studio|[Загрузка пакета SDK для моделирования](https://www.microsoft.com/download/details.aspx?id=48148)|

 Кроме того, необходимо создать преобразование пользовательского текстового шаблона, созданное в [разделе Пошаговое руководство. Создание узла пользовательского текстового шаблона](../modeling/walkthrough-creating-a-custom-text-template-host.md).

## <a name="using-domain-specific-language-tools-to-generate-a-directive-processor"></a>Использование Средства предметно-ориентированных языков для создания обработчика директив
 В этом пошаговом руководстве используется мастер Конструктор предметно-ориентированных языков для создания доменного языка для решения Дслминималтест.

#### <a name="to-use-domain-specific-language-tools-to-generate-a-directive-processor-that-is-based-on-a-domain-model"></a>Использование Средства предметно-ориентированных языков для создания процессора директив, основанного на модели предметной области

1. Создайте решение доменного языка со следующими характеристиками:

   - Имя: Дслминималтест

   - Шаблон решения: Минимальный язык

   - Расширение файла: мин

   - Название организации: Fabrikam

     Дополнительные сведения о создании решения для доменного языка см. в разделе [как создать решение доменного языка](../modeling/how-to-create-a-domain-specific-language-solution.md).

2. В меню **Сборка** выберите **Собрать решение**.

   > [!IMPORTANT]
   > На этом шаге создается процессор директив и добавляется ключ для него в реестр.

3. В меню **Отладка** щелкните **Начать отладку**.

    Откроется второй экземпляр [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

4. В экспериментальной сборке в **Обозреватель решений**дважды щелкните файл **Sample. min**.

    Файл откроется в конструкторе. Обратите внимание, что модель содержит два элемента, ExampleElement1 и ExampleElement2, и связь между ними.

5. Закройте второй экземпляр [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

6. Сохраните решение и закройте Конструктор предметно-ориентированных языков.

## <a name="connecting-a-custom-text-template-host-to-a-directive-processor"></a>Подключение узла пользовательского текстового шаблона к обработчику директив
 После создания процессора директив вы подключаете процессор директив и узел пользовательского текстового шаблона, созданный в [разделе Пошаговое руководство. Создание узла пользовательского текстового шаблона](../modeling/walkthrough-creating-a-custom-text-template-host.md).

#### <a name="to-connect-a-custom-text-template-host-to-the-generated-directive-processor"></a>Подключение узла пользовательского текстового шаблона к созданному обработчику директив

1. Откройте решение Кустомхост.

2. В меню **Проект** щелкните команду **Добавить ссылку**.

     Откроется диалоговое окно **Добавление ссылки** с отображаемой вкладкой **.NET** .

3. Добавьте следующие ссылки.

    - Microsoft.VisualStudio.Modeling.Sdk.11.0

    - Microsoft.VisualStudio.Modeling.Sdk.Diagrams.11.0

    - Microsoft.VisualStudio.TextTemplating.11.0

    - Microsoft.VisualStudio.TextTemplating.Interfaces.11.0

    - Microsoft.VisualStudio.TextTemplating.Modeling.11.0

    - Microsoft.VisualStudio.TextTemplating.VSHost.11.0

4. В верхней части Program.cs или Module1. vb добавьте следующую строку кода:

    ```csharp
    using Microsoft.Win32;
    ```

    ```vb
    Imports Microsoft.Win32
    ```

5. Выберите код для свойства `StandardAssemblyReferences`и замените его следующим кодом:

    > [!NOTE]
    > На этом шаге вы добавите ссылки на сборки, необходимые для созданного обработчика директив, который будет поддерживаться вашим узлом.

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

6. Выберите код для функции `ResolveDirectiveProcessor`и замените его следующим кодом:

    > [!IMPORTANT]
    > Этот код содержит жестко запрограммированные ссылки на имя созданного обработчика директив, к которому необходимо подключиться. Вы можете легко сделать это более общим, в этом случае он ищет все процессоры директив, перечисленные в реестре, и пытается найти совпадение. В этом случае узел будет работать с любым созданным обработчиком директив.

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

7. В меню **Файл** выберите команду **Сохранить все**.

8. В меню **Сборка** выберите **Собрать решение**.

## <a name="testing-the-custom-host-with-the-directive-processor"></a>Тестирование пользовательского узла с помощью процессора директив
 Чтобы протестировать основное приложение текстового шаблона, сначала необходимо написать текстовый шаблон, который вызывает созданный обработчик директив. Затем запустите настраиваемый узел, передайте ему имя текстового шаблона и убедитесь, что директива обрабатывается правильно.

#### <a name="to-create-a-text-template-to-test-the-custom-host"></a>Создание текстового шаблона для тестирования пользовательского ведущего приложения

1. Создайте текстовый файл и назовите его `TestTemplateWithDP.tt`. Для создания файла можно использовать любой текстовый редактор, например Блокнот.

2. Добавьте в текстовый файл следующий текст:

    > [!NOTE]
    > Язык программирования текстового шаблона не обязательно должен совпадать с языком пользовательского хоста.

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

3. В коде замените \<путь > с путем к примеру файла Sample. min из языка, созданного в первой процедуре.

4. Сохраните и закройте файл.

#### <a name="to-test-the-custom-host"></a>Тестирование пользовательского основного приложения

1. Откройте окно командной строки.

2. Введите путь к исполняемому файлу пользовательского ведущего приложения, но пока не нажимайте клавишу ВВОД.

     Например, введите: .

     `<YOUR PATH>CustomHost\bin\Debug\CustomHost.exe`

    > [!NOTE]
    > Вместо того чтобы вводить адрес, можно перейти к файлу Кустомхост. exe в **проводнике Windows**, а затем перетащить файл в окно командной строки.

3. Введите пробел.

4. Введите путь к файлу текстового шаблона и нажмите клавишу ВВОД.

     Например, введите: .

     `<YOUR PATH>TestTemplateWithDP.txt`

    > [!NOTE]
    > Вместо того чтобы вводить адрес, можно перейти к файлу Тесттемплатевисдп. txt в **проводнике Windows**, а затем перетащить файл в окно командной строки.

     Пользовательское ведущее приложение запускается и запускает процесс преобразования текстовых шаблонов.

5. В **проводнике**перейдите к папке, содержащей файл тесттемплатевисдп. txt.

     Папка также содержит файл TestTemplateWithDP1. txt.

6. Откройте этот файл, чтобы увидеть результаты преобразования текстового шаблона.

     Отобразятся результаты созданного текстового выхода, который должен выглядеть следующим образом:

    ```
    Text Template Host Test

    Box: ExampleElement1
    Linked to: ExampleElement2

    Box: ExampleElement2
    Linked from: ExampleElement1
    ```

## <a name="see-also"></a>См. также раздел
 [Пошаговое руководство. Создание пользовательского хост-класса для текстовых шаблонов](../modeling/walkthrough-creating-a-custom-text-template-host.md)
