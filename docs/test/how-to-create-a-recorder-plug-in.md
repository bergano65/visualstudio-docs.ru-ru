---
title: Создание подключаемого модуля записи для веб-тестов производительности
description: Сведения о том, как подключаемый модуль WebTestRecorderPlugin позволяет вам изменить записанный веб-тест производительности после нажатия кнопки остановки в панели инструментов средства записи в веб-тесте производительности.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- Web performance tests, recorder plug-in
ms.assetid: 6fe13be1-aeb5-4927-9bff-35950e194da9
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: da17af68f7aebe52ad208bf2b83d3221a0640be6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99877984"
---
# <a name="how-to-create-a-recorder-plug-in"></a>Практическое руководство. Создание подключаемого модуля записи

Подключаемый модуль <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRecorderPlugin> позволяет изменять записанные веб-тесты производительности. Изменение происходит после нажатия кнопки **Стоп** на панели инструментов **средства записи веб-тестов производительности**, но до сохранения и отображения теста в редакторе веб-тестов производительности.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Подключаемый модуль записи позволяет выполнять настраиваемую корреляцию динамических параметров. Используя встроенные функции корреляции, веб-тесты производительности обнаруживают динамические параметры в веб-записи после ее завершения или при нажатии кнопки **Преобразование динамических параметров в параметры веб-теста** на панели инструментов **редактора веб-тестов производительности**. Однако встроенные функции обнаружения не всегда позволяют найти все динамические параметры. Например, не удается определять идентификатор сеанса, который, как правило, изменяет свое значение каждые 5–30 минут. Поэтому приходится вручную выполнять процесс корреляции.

<xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRecorderPlugin> позволяет написать код для пользовательского подключаемого модуля. С помощью этого подключаемого модуля можно выполнять корреляцию или изменять веб-тест производительности самыми различными способами до его сохранения и отображения в редакторе веб-тестов производительности. Поэтому если пользователь определяет, что корреляцию некоторой динамической переменной следует выполнить для множества записей, он может автоматизировать процесс корреляции.

Подключаемый модуль записи можно также использовать для других целей, например для добавления правил извлечения и проверки, параметров контекста, а также для преобразования комментариев в транзакции в веб-тесте производительности.

В следующих процедурах описываются процессы создания элементарного кода для подключаемого модуля записи, развертывания этого подключаемого модуля и его выполнения. В примере кода, который представлен после описания процедур, демонстрируется использование Visual C# для создания пользовательского подключаемого модуля записи для корреляции динамических параметров.

## <a name="create-a-recorder-plug-in"></a>Создание подключаемого модуля записи

### <a name="to-create-a-recorder-plug-in"></a>Создание подключаемого модуля записи

1. Откройте решение, содержащее проект веб-тестов производительности и нагрузочных тестов с веб-тестом производительности, для которого нужно создать подключаемый модуль записи.

2. Добавьте в решение новый проект **Библиотека классов**.

3. В **обозревателе решений** щелкните правой кнопкой мыши папку **Ссылки** в папке проекта библиотеки классов и выберите команду **Добавить ссылку**.

    > [!TIP]
    > В качестве примера используется папка нового проекта библиотеки классов **RecorderPlugins**.

     Появится диалоговое окно **Добавление ссылки**.

4. Выберите вкладку **.NET**.

5. Прокрутите список вниз, выберите пункт **Microsoft.VisualStudio.QualityTools.WebTestFramework** и нажмите кнопку **ОК**.

     **Microsoft.VisualStudio.QualityTools.WebTestFramework** добавляется в папку **Ссылки** в **обозревателе решений**.

6. Напишите код подключаемого модуля записи. Сначала создайте открытый класс, производный от класса <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRecorderPlugin>.

7. Переопределите метод <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRecorderPlugin.PostWebTestRecording*> .

    ```csharp
    public class Class1 : WebTestRecorderPlugin
        {
            public override void PostWebTestRecording(object sender, PostWebTestRecordingEventArgs e)
            {
                base.PostWebTestRecording(sender, e);
            }
        }
    ```

     Аргументы события предоставляют два объекта, доступных для работы: записанный результат и записанный веб-тест производительности. Это позволяет выполнить итерацию по результату для поиска определенных значений, а затем перейти к тому же запросу в веб-тесте производительности для внесения изменений. Если требуется добавить параметр контекста или параметризовать части URL-адреса, также можно непосредственно изменить веб-тест производительности.

    > [!NOTE]
    > После внесения изменений в веб-тест производительности необходимо также установить для свойства <xref:Microsoft.VisualStudio.TestTools.WebTesting.PostWebTestRecordingEventArgs.RecordedWebTestModified*> значение true: `e.RecordedWebTestModified = true;`

8. Добавьте дополнительный код в соответствии с задачами, которые должен выполнять подключаемый модуль записи после завершения веб-записи. Например, можно добавить код для обработки пользовательской корреляции, как показано в расположенном ниже примере. Можно также создать подключаемый модуль записи для таких операций, как преобразование комментариев в транзакции или добавление правил проверки в веб-тест производительности.

9. В меню **Сборка** выберите **Сборка\<class library project name>** .

После этого разверните подключаемый модуль записи для его регистрации в Visual Studio.

### <a name="deploy-the-recorder-plug-in"></a>Развертывание подключаемого модуля записи

Завершив компиляцию подключаемого модуля записи, поместите полученную библиотеку DLL в одно из двух расположений:

- *%ProgramFiles(x86)%\Microsoft Visual Studio\\[версия]\\[выпуск]\Common7\IDE\PrivateAssemblies\WebTestPlugins*

- *%USERPROFILE%\Documents\Visual Studio [версия]\WebTestPlugins*

> [!WARNING]
> После копирования подключаемого модуля записи в одну из этих двух папок необходимо перезапустить Visual Studio для регистрации подключаемого модуля записи.

### <a name="execute-the-recorder-plug-in"></a>Выполнение подключаемого модуля записи

1. Создайте веб-тест производительности.

     Откроется диалоговое окно **Включить WebTestRecordPlugins**.

2. Установите флажок для соответствующего подключаемого модуля записи и нажмите кнопку **ОК**.

     После завершения записи веб-теста производительности будет выполняться новый подключаемый модуль записи.

    > [!WARNING]
    > При запуске веб-теста производительности или нагрузочного теста, в которых используется этот подключаемый модуль, может возникнуть ошибка примерно следующего вида:
    >
    > **Сбой запроса. Исключение в событии \<plug-in>: не удалось загрузить файл или сборку "\<"Plug-in name".dll file>, Version=\<n.n.n.n>, Culture=neutral, PublicKeyToken=null" или одну из зависимостей. Не удается найти указанный файл.**
    >
    > Это происходит, если в один из подключаемых модулей внесены изменения кода и создана новая версия библиотеки DLL **(Version=0.0.0.0)** , однако подключаемый модуль по-прежнему ссылается на исходную версию подключаемого модуля. Чтобы устранить эту проблему, выполните следующие действия.
    >
    > 1. В ссылках проекта веб-тестов производительности и нагрузочных тестов появится предупреждение. Удалите и вновь добавьте ссылку на библиотеку DLL подключаемого модуля.
    > 2. Удалите подключаемый модуль из теста или соответствующего расположения, а затем снова добавьте его.

## <a name="example"></a>Пример

В этом примере демонстрируется создание настраиваемого подключаемого модуля записи веб-теста производительности для выполнения пользовательской корреляции динамических параметров.

> [!NOTE]
> Полный текст этого примера кода расположен в конце данного раздела.

### <a name="iterate-through-the-result-to-find-first-page-with-reportsession"></a>Перебор объектов результата для поиска первой страницы с параметром ReportSession

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

### <a name="add-an-extraction-rule"></a>Добавление правила извлечения

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

### <a name="replace-query-string-parameters"></a>Замена параметров строки запроса

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
