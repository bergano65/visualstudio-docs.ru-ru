---
title: Учебник. Расширение простого консольного приложения C#
description: Ознакомьтесь с пошаговыми инструкциями по разработке консольного приложения на C# в Visual Studio.
ms.custom: get-started
ms.date: 07/09/2020
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: tutorial
ms.devlang: CSharp
author: ghogen
ms.author: ghogen
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: fd0d2b3e112a4bf08481fa8f043f70121d827010
ms.sourcegitcommit: cea9e5787ff33e0e18aa1942bf4236748e0ef547
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2020
ms.locfileid: "92197482"
---
# <a name="tutorial-extend-a-simple-c-console-app"></a>Учебник. Расширение простого консольного приложения C#

В этом руководстве вы узнаете, как использовать Visual Studio для расширения консольного приложения, созданного в первой части. Вы узнаете о некоторых функциях Visual Studio, необходимых для повседневной разработки, таких как управление несколькими проектами и создание ссылок на сторонние пакеты.

Если вы только что завершили [первую часть](tutorial-console.md) этой серии, у вас уже есть консольное приложение калькулятора.  Чтобы пропустить первую часть, можно открыть проект из репозитория GitHub. Приложение калькулятора на C# находится в репозитории [vs-tutorial-samples repo](https://github.com/MicrosoftDocs/vs-tutorial-samples), поэтому просто следуйте инструкциям в разделе [Учебник. Открытие проекта из репозитория](../tutorial-open-project-from-repo.md), чтобы начать работу.

## <a name="add-a-new-project"></a>Добавление нового проекта

Реальный код связан со множеством проектов, объединенных в решение. Давайте добавим еще один проект в приложение калькулятора. Это будет библиотека классов, предоставляющая некоторые функции калькулятора.

1. В Visual Studio можно использовать команду меню верхнего уровня **Файл** > **Добавить** > **Новый проект** , чтобы добавить новый проект, но можно также щелкнуть правой кнопкой мыши имя существующего проекта ("узел проекта") и открыть контекстное меню проекта. Это контекстное меню предлагает различные варианты добавления функциональных возможностей в проекты. Щелкните правой кнопкой мыши узел проекта в **обозревателе решений** и последовательно выберите **Добавить** > **Новый проект** .

1. Выберите шаблон проекта C# **Библиотека классов (.NET Standard)** .

   ![Снимок экрана: выбор шаблона проекта "Библиотека классов"](media/vs-2019/calculator2-add-project-dark.png)

1. Введите имя проекта **CalculatorLibrary** и щелкните **Создать** . Visual Studio создаст новый проект и добавит его в решение.

   ![Снимок экрана: обозреватель решений с добавленным проектом библиотеки классов CalculatorLibrary](media/vs-2019/calculator2-solution-explorer-with-class-library-dark2.png)

1. Вместо *Class1.cs* переименуйте файл в **CalculatorLibrary.cs** . Можно щелкнуть имя в **обозреватель решений** , чтобы указать другое имя, или щелкнуть правой кнопкой мыши и выбрать **Переименовать** или нажать клавишу **F2** .

   Возможно, вам будет предложено переименовать все ссылки на `Class1` в файле. Вы можете выбрать любой ответ, так как вы замените код на следующем шаге.

1. Теперь необходимо добавить ссылку на проект, чтобы первый проект мог использовать API, предоставляемые новой библиотекой классов.  Щелкните правой кнопкой мыши узел **Ссылки** в первом проекте и выберите **Добавить ссылку на проект** .

   ![Снимок экрана: пункт меню "Добавить ссылку на проект"](media/vs-2019/calculator2-add-project-reference-dark.png)

   Откроется диалоговое окно **Диспетчер ссылок** . Это диалоговое окно позволяет добавлять ссылки на другие проекты, а также сборки и библиотеки DLL COM, необходимые вашим проектам.

   ![Снимок экрана: диалоговое окно "Диспетчер ссылок"](media/vs-2019/calculator2-ref-manager-dark.png)

1. В диалоговом окне **Диспетчер ссылок** установите флажок для проекта **CalculatorLibrary** и выберите **ОК** .  Ссылка на проект отображается в узле **Проекты** в **обозревателе решений** .

   ![Снимок экрана: обозреватель решений со ссылкой на проект](media/vs-2019/calculator2-solution-explorer-with-project-reference-dark2.png)

1. В файле *Program.cs* выберите класс `Calculator` и весь его код и нажмите **CTRL+X** , чтобы вырезать его из Program.cs. Затем в **CalculatorLibrary** , в файле *CalculatorLibrary.cs* , вставьте код в пространство имен `CalculatorLibrary`. Затем объявите класс калькулятора как `public`, чтобы предоставить его за пределами библиотеки. Теперь код в *CalculatorLibrary.cs* должен выглядеть следующим образом:

   ```csharp
   using System;

    namespace CalculatorLibrary
    {
        public class Calculator
        {
            public static double DoOperation(double num1, double num2, string op)
            {
                double result = double.NaN; // Default value is "not-a-number" which we use if an operation, such as division, could result in an error.

                // Use a switch statement to do the math.
                switch (op)
                {
                    case "a":
                        result = num1 + num2;
                        break;
                    case "s":
                        result = num1 - num2;
                        break;
                    case "m":
                        result = num1 * num2;
                        break;
                    case "d":
                        // Ask the user to enter a non-zero divisor.
                        if (num2 != 0)
                        {
                            result = num1 / num2;
                        }
                        break;
                    // Return text for an incorrect option entry.
                    default:
                        break;
                }
                return result;
            }
        }
    }
   ```

1. Первый проект содержит ссылку, но вы увидите ошибку, так как вызов Calculator.DoOperation не разрешается. Это связано с тем, что CalculatorLibrary находится в другом пространстве имен, поэтому добавьте пространство имен `CalculatorLibrary` для полной ссылки.

   ```csharp
   result = CalculatorLibrary.Calculator.DoOperation(cleanNum1, cleanNum2, op);
   ```

   Попробуйте добавить директиву using в начало файла:

   ```csharp
   using CalculatorLibrary;
   ```

   Это изменение позволяет удалить пространство имен CalculatorLibrary из места вызова, но это приводит к неоднозначности. Является ли `Calculator` классом в CalculatorLibrary или Calculator является пространством имен?  Чтобы устранить неоднозначность, переименуйте пространство имен `CalculatorProgram`.

   ```csharp
   namespace CalculatorProgram
   ```

## <a name="reference-net-libraries-write-to-a-log"></a>Ссылки на библиотеки .NET: запись в журнал

1. Предположим, что теперь нужно добавить журнал всех операций и записать его в текстовый файл. Класс .NET `Trace` предоставляет эти функции. (Это удобно и для основных методов отладки вывода.)  Класс Trace находится в пространстве имен System.Diagnostics. Поскольку нам понадобятся классы System.IO, такие как `StreamWriter`, следует начать с добавления директив using.

   ```csharp
   using System.IO;
   using System.Diagnostics;
   ```

1. Просмотрев, как используется класс Trace, придерживайтесь ссылки на класс, связанный с файловым потоком. Это означает, что калькулятор будет работать лучше в качестве объекта, поэтому добавим конструктор.

   ```csharp
   public Calculator()
        {
            StreamWriter logFile = File.CreateText("calculator.log");
            Trace.Listeners.Add(new TextWriterTraceListener(logFile));
            Trace.AutoFlush = true;
            Trace.WriteLine("Starting Calculator Log");
            Trace.WriteLine(String.Format("Started {0}", System.DateTime.Now.ToString()));
        }

    public double DoOperation(double num1, double num2, string op)
        {
   ```

1. И нам нужно изменить статический метод `DoOperation` на метод-член.  Давайте также добавим выходные данные в каждый расчет для журнала, чтобы DoOperation выглядел следующим образом:

   ```csharp
   public double DoOperation(double num1, double num2, string op)
   {
        double result = double.NaN; // Default value is "not-a-number" which we use if an operation, such as division, could result in an error.

        // Use a switch statement to do the math.
        switch (op)
        {
            case "a":
                result = num1 + num2;
                Trace.WriteLine(String.Format("{0} + {1} = {2}", num1, num2, result));
                break;
            case "s":
                result = num1 - num2;
                Trace.WriteLine(String.Format("{0} - {1} = {2}", num1, num2, result));
                break;
            case "m":
                result = num1 * num2;
                Trace.WriteLine(String.Format("{0} * {1} = {2}", num1, num2, result));
                break;
            case "d":
                // Ask the user to enter a non-zero divisor.
                if (num2 != 0)
                {
                    result = num1 / num2;
                    Trace.WriteLine(String.Format("{0} / {1} = {2}", num1, num2, result));
                }
                    break;
            // Return text for an incorrect option entry.
            default:
                break;
        }
        return result;
    }
   ```

1. Теперь вернемся к файлу Program.cs. Статический вызов помечен красной волнистой линией. Чтобы устранить эту проблему, создайте переменную `calculator`, добавив следующую строку непосредственно перед циклом while:

   ```csharp
   Calculator calculator = new Calculator();
   ```

   Измените сайт вызова для `DoOperation` следующим образом:

   ```csharp
   result = calculator.DoOperation(cleanNum1, cleanNum2, op);
   ```

1. Запустите программу еще раз, а затем щелкните правой кнопкой мыши узел проекта, выберите **Открыть папку в проводнике файлов** , перейдите к выходной папке, например *bin/Debug/netcoreapp3.1* , и откройте файл *calculator.log* .

    ```output
    Starting Calculator Log
    Started 7/9/2020 1:58:19 PM
    1 + 2 = 3
    3 * 3 = 9
    ```

## <a name="add-a-nuget-package-write-to-a-json-file"></a>Добавление пакета NuGet: запись в JSON-файл

1. Теперь предположим, что мы хотим вывести операции в формате JSON — популярном и переносимом формате для хранения данных объекта. Чтобы реализовать эту функциональность, необходимо сослаться на пакет NuGet Newtonsoft.Json. Пакеты NuGet являются основным средством распространения библиотек классов .NET. В **обозревателе решений** щелкните правой кнопкой мыши узел **Ссылки** для проекта CalculatorLibrary и выберите **Управление пакетами NuGet** .

   ![Снимок экрана: "Управление пакетами NuGet" в контекстном меню.](media/vs-2019/calculator2-manage-nuget-packages-dark2.png)

   Откроется диспетчер пакетов NuGet.

   ![Снимок экрана: диспетчер пакетов NuGet](media/vs-2019/calculator2-nuget-package-manager-dark.png)

1. Найдите пакет Newtonsoft.Json и нажмите **Установить** .

   ![Снимок экрана: сведения о пакете NuGet Newtonsoft](media/vs-2019/calculator2-nuget-newtonsoft-json-dark2.png)

   Пакет будет загружен и добавлен в проект, а в узле "Ссылки" в **обозревателе решений** появится новая запись.

1. Добавьте директиву using для System.IO и пакета Newtonsoft.Json в начало файла *CalculatorLibrary.cs* .

   ```csharp
   using Newtonsoft.Json;
   ```

1. Теперь замените конструктор для калькулятора на следующий код и создайте объект члена JsonWriter:

   ```csharp
        JsonWriter writer;

        public Calculator()
        {
            StreamWriter logFile = File.CreateText("calculatorlog.json");
            logFile.AutoFlush = true;
            writer = new JsonTextWriter(logFile);
            writer.Formatting = Formatting.Indented;
            writer.WriteStartObject();
            writer.WritePropertyName("Operations");
            writer.WriteStartArray();
        }
   ```

1. Измените метод `DoOperation`, чтобы добавить код модуля записи JSON:

   ```csharp
        public double DoOperation(double num1, double num2, string op)
        {
            double result = double.NaN; // Default value is "not-a-number" which we use if an operation, such as division, could result in an error.
            writer.WriteStartObject();
            writer.WritePropertyName("Operand1");
            writer.WriteValue(num1);
            writer.WritePropertyName("Operand2");
            writer.WriteValue(num2);
            writer.WritePropertyName("Operation");
            // Use a switch statement to do the math.
            switch (op)
            {
                case "a":
                    result = num1 + num2;
                    writer.WriteValue("Add");
                    break;
                case "s":
                    result = num1 - num2;
                    writer.WriteValue("Subtract");
                    break;
                case "m":
                    result = num1 * num2;
                    writer.WriteValue("Multiply");
                    break;
                case "d":
                    // Ask the user to enter a non-zero divisor.
                    if (num2 != 0)
                    {
                        result = num1 / num2;
                        writer.WriteValue("Divide");
                    }
                    break;
                // Return text for an incorrect option entry.
                default:
                    break;
            }
            writer.WritePropertyName("Result");
            writer.WriteValue(result);
            writer.WriteEndObject();

            return result;
        }
   ```

1. Необходимо добавить метод для завершения синтаксиса JSON после ввода пользователем всех данных для операции.

   ```csharp
    public void Finish()
    {
        writer.WriteEndArray();
        writer.WriteEndObject();
        writer.Close();
    }
   ```

1. В *Program.cs* добавьте вызов Finish в конце.

   ```csharp
            // And call to close the JSON writer before return
            calculator.Finish();
            return;
        }
   ```

1. Выполните сборку приложения и запустите его. Попробуйте выполнить несколько операций и закройте приложение, используя команду "n".  Теперь откройте файл calculatorlog.json, который будет содержать примерно следующее.

   ```json
   {
    "Operations": [
        {
        "Operand1": 2.0,
        "Operand2": 3.0,
        "Operation": "Add",
        "Result": 5.0
        },
        {
        "Operand1": 3.0,
        "Operand2": 4.0,
        "Operation": "Multiply",
        "Result": 12.0
        }
    ]
   }
   ```

## <a name="next-steps"></a>Следующие шаги

Поздравляем с завершением этого учебника! Для получения дополнительных сведений перейдите к следующим руководствам.

> [!div class="nextstepaction"]
> [Продолжайте изучение учебников по C#](/dotnet/csharp/tutorials/)

> [!div class="nextstepaction"]
> [Продолжайте обзор интегрированной среды разработки Visual Studio](/../visual-studio-ide.md)

## <a name="see-also"></a>См. также

* [C# IntelliSense](../../ide/visual-csharp-intellisense.md)
* [Сведения об отладке кода C# в Visual Studio](tutorial-debugger.md)
