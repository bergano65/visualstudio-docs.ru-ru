---
title: Создание подключаемого модуля записи для веб-тестов производительности в Visual Studio
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- Web performance tests, recorder plug-in
ms.assetid: 6fe13be1-aeb5-4927-9bff-35950e194da9
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 008275d4e0ff094c7933b4e0bae89055acd4bf8e
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
ms.locfileid: "31978181"
---
# <a name="how-to-create-a-recorder-plug-in"></a>Практическое руководство. Создание подключаемого модуля записи

Подключаемый модуль <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRecorderPlugin> позволяет изменять записанные веб-тесты производительности. Изменение происходит после нажатия кнопки **Стоп** на панели инструментов средства записи веб-тестов производительности, но до сохранения и отображения теста в редакторе веб-тестов производительности.

Подключаемый модуль записи позволяет выполнять настраиваемую корреляцию динамических параметров. Используя встроенные функции корреляции, веб-тесты производительности обнаруживают динамические параметры в веб-записи после ее завершения или при нажатии кнопки **Преобразование динамических параметров в параметры веб-теста** на панели инструментов редактора веб-тестов производительности. Однако встроенные функции обнаружения не всегда позволяют найти все динамические параметры. Например, не удается определять идентификатор сеанса, который, как правило, изменяет свое значение каждые 5–30 минут. Поэтому приходится вручную выполнять процесс корреляции.

<xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRecorderPlugin> позволяет написать код для пользовательского подключаемого модуля. С помощью этого подключаемого модуля можно выполнять корреляцию или изменять веб-тест производительности самыми различными способами до его сохранения и отображения в редакторе веб-тестов производительности. Поэтому если пользователь определяет, что корреляцию некоторой динамической переменной следует выполнить для множества записей, он может автоматизировать процесс корреляции.

Подключаемый модуль записи можно также использовать для других целей, например для добавления правил извлечения и проверки, параметров контекста, а также для преобразования комментариев в транзакции в веб-тесте производительности.

В следующих процедурах описываются процессы создания элементарного кода для подключаемого модуля записи, развертывания этого подключаемого модуля и его выполнения. В примере кода, который представлен после описания процедур, демонстрируется использование Visual C# для создания пользовательского подключаемого модуля записи для корреляции динамических параметров.

## <a name="creating-a-recorder-plug-in"></a>Создание подключаемого модуля записи

### <a name="to-create-a-recorder-plug-in"></a>Создание подключаемого модуля записи

1.  Откройте решение, содержащее проект веб-тестов производительности и нагрузочных тестов с веб-тестом производительности, для которого нужно создать подключаемый модуль записи.

2.  В обозревателе решений щелкните правой кнопкой мыши решение, выберите команду **Добавить** и пункт **Новый проект**.

     Откроется диалоговое окно **Добавление нового проекта**.

3.  В области **Установленные шаблоны** выберите **Visual C#**.

4.  В списке шаблонов выберите элемент **Библиотека классов**.

5.  В текстовом поле **Имя** введите имя подключаемого модуля записи.

     В обозреватель решений добавляется библиотека классов, а в редакторе кода открывается новый класс.

6.  В обозревателе решений щелкните правой кнопкой мыши папку **Ссылки** в папке проекта библиотеки классов и выберите команду **Добавить ссылку**.

    > [!TIP]
    > В качестве примера используется папка нового проекта библиотеки классов **RecorderPlugins**.

     Появится диалоговое окно **Добавление ссылки**.

7.  Выберите вкладку **.NET**.

8.  Прокрутите список вниз, выберите пункт **Microsoft.VisualStudio.QualityTools.WebTestFramework** и нажмите кнопку **ОК**.

     **Microsoft.VisualStudio.QualityTools.WebTestFramework** добавляется в папку **Ссылки** в обозревателе решений.

9. Напишите код подключаемого модуля записи. Сначала создайте открытый класс, производный от класса <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRecorderPlugin>.

10. Переопределите метод <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRecorderPlugin.PostWebTestRecording*>.

    ```csharp
    public class Class1 : WebTestRecorderPlugin
        {
            public override void PostWebTestRecording(object sender, PostWebTestRecordingEventArgs e)
            {
                base.PostWebTestRecording(sender, e);
            }
        }
    ```

     Аргументы события предоставляют два объекта, доступных для работы: записанный результат и записанный веб-тест производительности. Это позволяет перебирать объекты результата для поиска определенных значений и затем переходить к тому же запросу в веб-тесте производительности для выполнения изменений. Если необходимо добавить параметр контекста или параметризовать части URL-адреса, можно непосредственно изменить веб-тест производительности.

    > [!NOTE]
    > После внесения изменений в веб-тест производительности необходимо также установить для свойства <xref:Microsoft.VisualStudio.TestTools.WebTesting.PostWebTestRecordingEventArgs.RecordedWebTestModified*> значение true: `e.RecordedWebTestModified = true;`

11. Добавьте дополнительный код в соответствии с задачами, которые должен выполнять подключаемый модуль записи после завершения веб-записи. Например, можно добавить код для обработки пользовательской корреляции, как показано в расположенном ниже примере. Можно также создать подключаемый модуль записи для таких операций, как преобразование комментариев в транзакции или добавление правил проверки в веб-тест производительности.

12. В меню **Сборка** выберите пункт "Сборка \<имя проекта библиотеки классов>".

13. После этого необходимо развернуть подключаемый модуль записи для его регистрации в Visual Studio.

### <a name="deploy-the-recorder-plug-in"></a>Развертывание подключаемого модуля записи

Завершив компиляцию подключаемого модуля записи, необходимо поместить итоговую библиотеку DLL в одну из двух папок:

-   %ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\PrivateAssemblies\WebTestPlugins

-   %USERPROFILE%\My Documents\Visual Studio \<*версия*>\WebTestPlugins

> [!WARNING]
> После копирования подключаемого модуля записи в одну из этих двух папок необходимо перезапустить Visual Studio для регистрации подключаемого модуля записи.

### <a name="to-execute-the-recorder-plug-in"></a>Выполнение подключаемого модуля записи

1.  Создайте новый веб-тест производительности.

     Откроется диалоговое окно **Включить WebTestRecordPlugins**.

2.  Установите флажок для соответствующего подключаемого модуля записи и нажмите кнопку "ОК".

     После завершения записи веб-теста производительности выполняется новый подключаемый модуль записи.

    > [!WARNING]
    > При запуске веб-теста производительности или нагрузочного теста, использующего данный подключаемый модуль, может появиться ошибка примерно следующего вида:
    >
    > **Сбой запроса. Исключение в событии \<подключаемый модуль>: не удалось загрузить файл или сборку "Файл \<"Имя подключаемого модуля".dll>, Version=\<n.n.n.n>, Culture=neutral, PublicKeyToken=null" или одну из зависимостей. Не удается найти указанный файл.**
    >
    > Это происходит, если в один из подключаемых модулей внесены изменения кода и создана новая версия библиотеки DLL **(Version=0.0.0.0)**, однако подключаемый модуль по-прежнему ссылается на исходную версию подключаемого модуля. Чтобы устранить эту проблему, выполните следующие действия.
    >
    > 1.  В ссылках проекта веб-тестов производительности и нагрузочных тестов появится предупреждение. Удалите и вновь добавьте ссылку на библиотеку DLL подключаемого модуля.
    > 2.  Удалите подключаемый модуль из теста или соответствующего расположения, а затем снова добавьте его.

## <a name="example"></a>Пример

В этом примере демонстрируется создание настраиваемого подключаемого модуля записи веб-теста производительности для выполнения пользовательской корреляции динамических параметров.

> [!NOTE]
> Полный текст этого примера кода расположен в конце данного раздела.

 **Обзор примера кода**

## <a name="iterate-through-the-result-to-find-first-page-with-reportsession"></a>Перебор объектов результата для поиска первой страницы с параметром ReportSession

В этой части примера кода перебираются все записанные объекты и выполняется поиск параметра ReportSession в теле ответа.

```csharp
foreach (WebTestResultUnit unit in e.RecordedWebTestResult.Children)
 {
     WebTestResultPage page = unit as WebTestResultPage;
     if (page != null)
     {
         if (!foundId)
         {
             int indexOfReportSession = page.RequestResult.Response.BodyString.IndexOf("ReportSession");
             if (indexOfReportSession > -1)
             {
```

## <a name="add-an-extraction-rule"></a>Добавление правила извлечения

После обнаружения ответа необходимо добавить правило извлечения. В этой части примера кода создается правило извлечения с помощью класса <xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionRuleReference>, а затем выполняется поиск соответствующего запроса в веб-тесте производительности для добавления в него правила извлечения. К каждому объекту результата добавляется новое свойство DeclarativeWebTestItemId, которое используется в коде для получения соответствующего запроса из веб-теста производительности.

```csharp
ExtractionRuleReference ruleReference = new ExtractionRuleReference();
     ruleReference.Type = typeof(ExtractText);
     ruleReference.ContextParameterName = "SessionId";
     ruleReference.Properties.Add(new PluginOrRuleProperty("EndsWith", "&ControlID="));
     ruleReference.Properties.Add(new PluginOrRuleProperty("HtmlDecode", "True"));
     ruleReference.Properties.Add(new PluginOrRuleProperty("IgnoreCase", "True"));
     ruleReference.Properties.Add(new PluginOrRuleProperty("Index", "0"));
     ruleReference.Properties.Add(new PluginOrRuleProperty("Required", "True"));
     ruleReference.Properties.Add(new PluginOrRuleProperty("StartsWith", "ReportSession="));
     ruleReference.Properties.Add(new PluginOrRuleProperty("UseRegularExpression", "False"));

     WebTestRequest requestInWebTest = e.RecordedWebTest.GetItem(page.DeclarativeWebTestItemId) as WebTestRequest;
     if (requestInWebTest != null)
     {
         requestInWebTest.ExtractionRuleReferences.Add(ruleReference);
         e.RecordedWebTestModified = true;
     }
```

## <a name="replace-query-string-parameters"></a>Замена параметров строки запроса

Теперь выполняется поиск параметров строки запроса, которым присвоено имя ReportSession, и изменяется значение на {{SessionId}}, как показано в следующей части примера кода:

```csharp
WebTestRequest requestInWebTest = e.RecordedWebTest.GetItem(page.DeclarativeWebTestItemId) as WebTestRequest;
if (requestInWebTest != null)
{
    foreach (QueryStringParameter param in requestInWebTest.QueryStringParameters)
    {
         if (param.Name.Equals("ReportSession"))
         {
             param.Value = "{{SessionId}}";
         }
     }
 }
```

```csharp
using System.ComponentModel;
using Microsoft.VisualStudio.TestTools.WebTesting;
using Microsoft.VisualStudio.TestTools.WebTesting.Rules;

namespace RecorderPlugin
{
    [DisplayName("Correlate ReportSession")]
    [Description("Adds extraction rule for Report Session and binds this to querystring parameters that use ReportSession")]
    public class CorrelateSessionId : WebTestRecorderPlugin
    {
        public override void PostWebTestRecording(object sender, PostWebTestRecordingEventArgs e)
        {
            //first find the session id
            bool foundId = false;
            foreach (WebTestResultUnit unit in e.RecordedWebTestResult.Children)
            {
                WebTestResultPage page = unit as WebTestResultPage;
                if (page != null)
                {
                    if (!foundId)
                    {
                        int indexOfReportSession = page.RequestResult.Response.BodyString.IndexOf("ReportSession");
                        if (indexOfReportSession > -1)
                        {
                            //add an extraction rule to this request
                            // Get the corresponding request in the Declarative Web performance test
                            ExtractionRuleReference ruleReference = new ExtractionRuleReference();

                            ruleReference.Type = typeof(ExtractText);
                            ruleReference.ContextParameterName = "SessionId";
                            ruleReference.Properties.Add(new PluginOrRuleProperty("EndsWith", "&ControlID="));
                            ruleReference.Properties.Add(new PluginOrRuleProperty("HtmlDecode", "True"));
                            ruleReference.Properties.Add(new PluginOrRuleProperty("IgnoreCase", "True"));
                            ruleReference.Properties.Add(new PluginOrRuleProperty("Index", "0"));
                            ruleReference.Properties.Add(new PluginOrRuleProperty("Required", "True"));
                            ruleReference.Properties.Add(new PluginOrRuleProperty("StartsWith", "ReportSession="));
                            ruleReference.Properties.Add(new PluginOrRuleProperty("UseRegularExpression", "False"));

                            WebTestRequest requestInWebTest = e.RecordedWebTest.GetItem(page.DeclarativeWebTestItemId) as WebTestRequest;
                            if (requestInWebTest != null)
                            {
                                requestInWebTest.ExtractionRuleReferences.Add(ruleReference);
                                e.RecordedWebTestModified = true;
                            }
                            foundId = true;

                        }
                    }
                    else
                    {
                        //now update query string parameters
                        WebTestRequest requestInWebTest = e.RecordedWebTest.GetItem(page.DeclarativeWebTestItemId) as WebTestRequest;
                        if (requestInWebTest != null)
                        {
                            foreach (QueryStringParameter param in requestInWebTest.QueryStringParameters)
                            {
                                if (param.Name.Equals("ReportSession"))
                                {
                                    param.Value = "{{SessionId}}";
                                }
                            }
                        }
                    }
                }
            }
        }
    }
}
```

## <a name="see-also"></a>См. также

- <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRecorderPlugin.PostWebTestRecording*>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionRuleReference>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRecorderPlugin.PostWebTestRecording*>
- [Создание пользовательского кода и подключаемых модулей для нагрузочных тестов](../test/create-custom-code-and-plug-ins-for-load-tests.md)
- [Создание и запуск закодированного веб-теста производительности](../test/generate-and-run-a-coded-web-performance-test.md)