---
title: Создание подключаемого модуля нагрузочных тестов в Visual Studio | Документы Майкрософт
ms.date: 10/19/2016
ms.topic: conceptual
f1_keywords:
- vs.test.load.loadtestplugin
helpviewer_keywords:
- code, load tests
- plug-ins, load test
- load tests, plug-ins
ms.assetid: 27806972-1b15-4388-833d-6d0632816f1f
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-ide-test
ms.openlocfilehash: 6e585fe66bde573f8bb133b0c8cda0900b0d6d16
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-create-a-load-test-plug-in"></a>Практическое руководство. Создание подключаемого модуля нагрузочных тестов

Существует возможность создания подключаемого модуля нагрузочных тестов для запуска кода в различное время в процессе выполнения нагрузочного теста. Подключаемый модуль создается для расширения или изменения встроенных возможностей нагрузочного теста. Например, можно составить код подключаемого модуля для нагрузочного теста, позволяющий настраивать или изменять шаблон нагрузочного теста во время выполнения нагрузочного теста. Для этого необходимо создать класс, наследующий интерфейс <xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin>. В этом классе должен быть реализован метод <xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin.Initialize*> данного интерфейса. Дополнительные сведения см. в разделе <xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin>.

> [!NOTE]
> Можно также создавать подключаемые модули для веб-тестов производительности. Дополнительные сведения см. в разделе [Практическое руководство. Создание подключаемого модуля веб-тестов производительности](../test/how-to-create-a-web-performance-test-plug-in.md).

## <a name="to-create-a-load-test-plug-in-by-using-visual-c"></a>Создание подключаемого модуля нагрузочных тестов с помощью Visual C#

1.  Откройте проект веб-тестов производительности и нагрузочных тестов, содержащий веб-тест производительности.

2.  Добавьте нагрузочный тест в тестовый проект и настройте его для запуска веб-теста производительности.

     Дополнительные сведения см. в разделе [Краткое руководство. Создание проекта нагрузочного теста](../test/quickstart-create-a-load-test-project.md).

3.  В обозревателе решений щелкните правой кнопкой мыши решение, выберите команду **Добавить** и пункт **Новый проект**.

     Откроется диалоговое окно **Добавление нового проекта**.

4.  В области **Установленные шаблоны** выберите **Visual C#**.

5.  В списке шаблонов выберите элемент **Библиотека классов**.

6.  В текстовое поле **Имя** введите имя класса.

7.  Нажмите кнопку **ОК**.

8.  Новый проект библиотеки классов будет добавлен в обозреватель решений, а новый класс появится в редакторе кода.

9. В обозревателе решений щелкните правой кнопкой мыши папку **Ссылки** в новой библиотеке классов и выберите команду **Добавить ссылку**.

10. Появится диалоговое окно **Добавление ссылки**.

11. Перейдите на вкладку **.NET**, прокрутите вниз и выберите **Microsoft.VisualStudio.QualityTools.LoadTestFramework**.

12. Нажмите кнопку **ОК**.

     Ссылка на **Microsoft.VisualStudio.QualityTools.LoadTestFramework** будет добавлена в папку **Ссылки** в обозревателе решений.

13. В обозревателе решений щелкните правой кнопкой мыши верхний узел проекта веб-тестов производительности и нагрузочных тестов, в который требуется добавить подключаемый модуль нагрузочного теста, и выберите команду **Добавить ссылку**.

14. Появится диалоговое окно **Добавление ссылки**.

15. Перейдите на вкладку **Проекты** и выберите проект библиотеки классов.

16. Нажмите кнопку **ОК**.

17. В редакторе кода добавьте инструкцию `using` для пространства имен <xref:Microsoft.VisualStudio.TestTools.LoadTesting>.

18. Реализуйте интерфейс <xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin> для класса, созданного в проекте библиотеки классов. Образец реализации см. в приведенном ниже разделе "Пример".

19. После написания кода выполните построение нового проекта.

20. Щелкните правой кнопкой мыши верхний узел нагрузочного теста и выберите команду **Добавить подключаемый модуль нагрузочных тестов**.

     Откроется диалоговое окно **Добавить подключаемый модуль нагрузочных тестов**.

21. В области **Выберите подключаемый модуль** выберите свой класс подключаемого модуля нагрузочных тестов.

22. В области **Свойства выбранного подключаемого модуля** задайте начальные значения для подключаемого модуля, которые будут использоваться во время выполнения.

    > [!NOTE]
    > С помощью подключаемых модулей можно предоставить доступ к произвольному количеству свойств; их необходимо сделать общедоступными, задаваемыми и относящимися к базовому типу, например к целочисленному, логическому или строковому. Кроме того, свойства подключаемого модуля веб-теста производительности можно изменить позже в окне "Свойства".

23. Нажмите кнопку **ОК**.

     Подключаемый модуль будет добавлен в папку **Подключаемые модули нагрузочных тестов**.

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

В следующем примере показан подключаемый модуль нагрузочных тестов, выполняющий пользовательский код после наступления события LoadTestFinished. Если этот код выполняется на агенте тестирования на удаленном компьютере, а агент тестирования не имеет службы SMTP локального узла, нагрузочный тест останется в состоянии "Выполняется", поскольку открыто окно сообщения.

> [!NOTE]
>  В следующем фрагменте кода необходимо добавить ссылку на System.Windows.Forms.

```csharp
using System;
using Microsoft.VisualStudio.TestTools.LoadTesting;
using System.Net.Mail;
using System.Windows.Forms;

namespace LoadTestPluginTest
{
    public class MyLoadTestPlugin : ILoadTestPlugin
    {
        LoadTest myLoadTest;

        public void Initialize(LoadTest loadTest)
        {
            myLoadTest = loadTest;
            myLoadTest.LoadTestFinished += new
                EventHandler(myLoadTest_LoadTestFinished);
        }

        void myLoadTest_LoadTestFinished(object sender, EventArgs e)
        {
            try
            {
                // place custom code here
                MailAddress MyAddress = new MailAddress("someone@example.com");
                MailMessage MyMail = new MailMessage(MyAddress, MyAddress);
                MyMail.Subject = "Load Test Finished -- Admin Email";
                MyMail.Body = myLoadTest..Name + " has finished.";

                SmtpClient MySmtpClient = new SmtpClient("localhost");
                MySmtpClient.Send(MyMail);
            }

            catch (SmtpException ex)
            {
                MessageBox.Show(ex.InnerException.Message +
                    ".\r\nMake sure you have a valid SMTP.", "LoadTestPlugin", MessageBoxButtons.OK, MessageBoxIcon.Warning, MessageBoxDefaultButton.Button1);
            }
        }
    }
}
```

С нагрузочным тестом связано восемь событий, которые могут обрабатываться в подключаемом модуле нагрузочных тестов для запуска пользовательского кода. Ниже приведен список событий, обеспечивающих доступ к различным этапам запуска нагрузочного теста.

-   <xref:Microsoft.VisualStudio.TestTools.LoadTesting.LoadTest.LoadTestStarting>

-   <xref:Microsoft.VisualStudio.TestTools.LoadTesting.LoadTest.LoadTestFinished>

-   <xref:Microsoft.VisualStudio.TestTools.LoadTesting.LoadTest.LoadTestWarmupComplete>

-   <xref:Microsoft.VisualStudio.TestTools.LoadTesting.LoadTest.TestStarting>

-   <xref:Microsoft.VisualStudio.TestTools.LoadTesting.LoadTest.TestFinished>

-   <xref:Microsoft.VisualStudio.TestTools.LoadTesting.LoadTest.ThresholdExceeded>

-   <xref:Microsoft.VisualStudio.TestTools.LoadTesting.LoadTest.Heartbeat>

-   <xref:Microsoft.VisualStudio.TestTools.LoadTesting.LoadTest.LoadTestAborted>

## <a name="see-also"></a>См. также

- <xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin>
- [Создание пользовательского кода и подключаемых модулей для нагрузочных тестов](../test/create-custom-code-and-plug-ins-for-load-tests.md)
- [Практическое руководство. Создание подключаемого модуля веб-теста производительности](../test/how-to-create-a-web-performance-test-plug-in.md)