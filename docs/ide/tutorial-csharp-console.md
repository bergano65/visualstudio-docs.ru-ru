---
title: Начало работы с консольными приложениями на C# в Visual Studio
description: Ознакомьтесь с пошаговыми инструкциями по созданию консольного приложения на C# в Visual Studio.
ms.custom: ''
ms.date: 09/28/2018
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.topic: tutorial
ms.devlang: CSharp
author: TerryGLee
ms.author: tglee
manager: douge
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: ad1ee95cb9cc754261502e7377cde6c91e5befce
ms.sourcegitcommit: ad5fb20f18b23eb8bd2568717f61edc6b7eee5e7
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47859514"
---
# <a name="tutorial-get-started-with-a-c-console-app-in-visual-studio"></a>Руководство. Начало работы с консольным приложением на C# в Visual Studio

В этом руководстве по C# вы создадите и запустите консольное приложение с помощью Visual Studio, а также ознакомитесь с некоторыми возможностями [интегрированной среды разработки (IDE) Visual Studio](visual-studio-ide.md).

Установите Visual Studio бесплатно со страницы [скачиваемых материалов Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017), если еще не сделали этого.

## <a name="create-a-project"></a>Создание проекта

Сначала мы создадим проект приложения на C#. Для этого типа проекта уже имеются все нужные файлы шаблонов, что избавляет вас от лишней работы.

1. Откройте Visual Studio 2017.

2. В верхней строке меню выберите **Файл** > **Создать** > **Проект**.

3. В левой области диалогового окна **Новый проект** разверните узел **C#** и выберите **.NET Core**. На средней панели выберите **Консольное приложение (.NET Core)**. Назовите файл *Calculator*.

   ![Шаблон проекта "Консольное приложение (.NET Core)" в диалоговом окне "Новый проект" в интегрированной среде разработки Visual Studio](../ide/media/new-project-csharp-calculator-console-app.png)

### <a name="add-a-workgroup-optional"></a>Добавление рабочей нагрузки (необязательно)

Если шаблон проекта **Консольное приложение (.NET Core)** отсутствует, его можно получить, добавив рабочую нагрузку **Кроссплатформенная разработка .NET Core**. Добавить ее можно одним из двух способов в зависимости от того, какие обновления Visual Studio 2017 установлены на вашем компьютере.

#### <a name="option-1-use-the-new-project-dialog-box"></a>Способ 1. Диалоговое окно "Новый проект"

1. Выберите ссылку **Открыть Visual Studio Installer** в левой области диалогового окна **Новый проект**.

   ![Выбор ссылки "Открыть Visual Studio Installer" в диалоговом окне "Новый проект"](../ide/media/csharp-open-visual-studio-installer-generic-dark.png)

1. Запускается Visual Studio Installer. Выберите рабочую нагрузку **Кроссплатформенная разработка .NET Core** и затем элемент **Изменить**.

   ![Рабочая нагрузка "Кроссплатформенная разработка .NET Core" в Visual Studio Installer](../ide/media/dot-net-core-xplat-dev-workload.png)

#### <a name="option-2-use-the-tools-menu-bar"></a>Способ 2. Меню "Сервис"

1. Закройте диалоговое окно **Новый проект** и в верхней строке меню выберите **Сервис** > **Получить средства и компоненты**.

1. Запускается Visual Studio Installer. Выберите рабочую нагрузку **Кроссплатформенная разработка .NET Core** и затем элемент **Изменить**.

## <a name="create-a-c-console-calculator-app"></a>Создание приложения "C# Console Calculator" (Консольный калькулятор на C#)

1. Откройте Visual Studio 2017 и в верхней строке меню выберите **Файл** > **Создать** > **Проект**.

1. В левой области диалогового окна **Новый проект** разверните узел **C#** и выберите **.NET Core**. На средней панели выберите **Консольное приложение (.NET Core)**. Назовите файл *Calculator*.

1. Введите или вставьте следующий код в редактор кода.

    ```csharp
    using System;

    namespace Calculator
    {
        class Program
        {
            static void Main(string[] args)
            {
                // Declare variables and then instantiate to zero
                double num1 = 0; double num2 = 0;

                // Display title as the C# console calculator app
                Console.WriteLine("Console Calculator in C#\r");
                Console.WriteLine("------------------------\n");

                // Ask the user to type the first number
                Console.WriteLine("Type a number, and then press Enter");
                num1 = Convert.ToDouble(Console.ReadLine());

                // Ask the user to type the second number
                Console.WriteLine("Type another number, and then press Enter");
                num2 = Convert.ToDouble(Console.ReadLine());

                // Ask the user to choose an option
                Console.WriteLine("Choose an option from the following list:");
                Console.WriteLine("\ta - Add");
                Console.WriteLine("\ts - Subtract");
                Console.WriteLine("\tm - Multiply");
                Console.WriteLine("\td - Divide");
                Console.Write("Your option? ");

                // Use a switch statement to do the math
                switch (Console.ReadLine())
                {
                    case "a":
                        Console.WriteLine($"Your result: {num1} + {num2} = " + (num1 + num2));
                        break;
                    case "s":
                        Console.WriteLine($"Your result: {num1} - {num2} = " + (num1 - num2));
                        break;
                    case "m":
                        Console.WriteLine($"Your result: {num1} * {num2} = " + (num1 * num2));
                        break;
                    case "d":
                        // Ask the user to enter a non-zero divisor until they do so
                        while (num2 == 0)
                        {
                            Console.WriteLine("Enter a non-zero divisor: ");
                            num2 = Convert.ToDouble(Console.ReadLine());
                        }
                        Console.WriteLine($"Your result: {num1} / {num2} = " + (num1 / num2));
                        break;
                    // Return text for an incorrect option entry
                    default:
                        Console.WriteLine("That is an incorrect option entry, please try again.");
                        break;
                }
                // Wait for the user to respond before closing
                Console.Write("Press any key to close the Calculator console app...");
                Console.ReadKey();
            }
        }
    }
    ```

   Код, отображающийся после `static void Main(string[] args)`, должен выглядеть так, как показано на следующем снимке экрана:

   ![Редактор кода с приложением C# Console Calculator](../ide/media/csharp-console-calculator-code.png)

1. Выберите **Calculator**, чтобы запустить программу, или нажмите клавишу **F5**.

   ![Нажмите кнопку Calculator, чтобы запустить приложение с панели инструментов](../ide/media/csharp-console-calculator-button.png)

1. Просмотрите результат в окне консоли. Когда вы следуете инструкциям на экране, приложение должно выглядеть, как на следующем снимке экрана:

    ![Окно консоли с приложением Calculator, в том числе запросы на выполнение действий.](../ide/media/csharp-console-calculator.png)

### <a name="close-the-app"></a>Закрытие приложения

1. Нажмите любую клавишу, чтобы закрыть приложение калькулятора.

1. Закройте область **вывода** в Visual Studio.

   ![Закрытие области вывода в Visual Studio](../ide/media/csharp-calculator-close-output-pane.png)

1. Закройте Visual Studio.

## <a name="quick-answers-faq"></a>Быстрые ответы на часто задаваемые вопросы

Ниже приведен краткий список вопросов и ответов, с помощью которого вы сможете ознакомиться с некоторыми основными понятиями.

### <a name="what-is-c"></a>Что такое C#?

C# — это типобезопасный язык программирования, который работает на базе .NET Framework и .NET Core. С помощью C# можно создавать приложения для Windows, клиент-серверные приложения, приложения для работы с базами данных, веб-службы XML, распределенные компоненты и многое другое.

### <a name="what-is-visual-studio"></a>Что такое Visual Studio?

Visual Studio — это интегрированный набор средств разработки. Его можно рассматривать как программу для создания приложений.

### <a name="what-is-a-console-app"></a>Что такое консольное приложение?

Консольное приложение принимает входные данные и выводит результаты в окне командной строки, также называемом консолью.

### <a name="what-is-net-core"></a>Что такое .NET Core?

.NET Core — это дальнейший этап развития платформы .NET Framework. В то время как платформа .NET Framework позволяла использовать один и тот же код в средах разных языков программирования, в .NET Core появилась возможность использовать один и тот же код на разных платформах. Более того, это платформа с открытым кодом.

(Как .NET Framework, так и .NET Core включают в себя библиотеки готовых функций. Также в них включена общеязыковая среда выполнения (CLR), которая выполняет роль виртуальной машины для запуска кода.)

## <a name="next-steps"></a>Следующие шаги

Поздравляем с завершением этого учебника! Для получения дополнительных сведений перейдите к следующим руководствам.

> [!div class="nextstepaction"]
> [Руководства по C#](/dotnet/csharp/tutorials/)

## <a name="see-also"></a>См. также

* Видеокурс [C# Fundamentals for Absolute Beginners](https://mva.microsoft.com/en-us/training-courses/c-fundamentals-for-absolute-beginners-16169) (Основы программирования на C# для начинающих)
