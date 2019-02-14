---
title: Учебник. Начало работы с Visual Basic
description: Ознакомьтесь с пошаговыми инструкциями по созданию простого консольного приложения на Visual Basic в Visual Studio.
ms.custom: seodec18, get-started
ms.date: 08/10/2018
ms.technology: vs-ide-general
ms.topic: tutorial
ms.devlang: vb
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- vb
ms.workload:
- multiple
ms.openlocfilehash: 146a0cdb5e553f262bea0b5b7dd5f592592cf6ad
ms.sourcegitcommit: 34940a18f5b03a59567f54c7024a0b16d4272f1e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/12/2019
ms.locfileid: "56155699"
---
# <a name="tutorial-get-started-with-visual-basic-in-visual-studio"></a>Учебник. Начало работы с Visual Basic в Visual Studio

В этом руководстве по Visual Basic вы будете работать со средой Visual Studio для создания и запуска нескольких разных консольных приложений. Вы также ознакомитесь с некоторыми возможностями [интегрированной среды разработки (IDE) Visual Studio](visual-studio-ide.md).

Установите Visual Studio бесплатно со страницы [скачиваемых материалов Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017), если еще не сделали этого.

## <a name="create-a-project"></a>Создание проекта

Сначала мы создадим проект приложения Visual Basic. Для этого типа проекта уже имеются все нужные файлы шаблонов, что избавляет вас от лишней работы.

1. Откройте Visual Studio 2017.

2. В верхней строке меню выберите **Файл** > **Создать** > **Проект**.

3. В левой области диалогового окна **Новый проект** разверните узел **Visual Basic** и выберите **.NET Core**. На средней панели выберите **Консольное приложение (.NET Core)**. Назовите файл *HelloWorld*.

   ![Шаблон проекта "Консольное приложение (.NET Core)" в диалоговом окне "Новый проект" в интегрированной среде разработки Visual Studio](media/new-project-vb-dotnetcore-whatisyourname-console-app.png)

### <a name="add-a-workgroup-optional"></a>Добавление рабочей нагрузки (необязательно)

Если шаблон проекта **Консольное приложение (.NET Core)** отсутствует, его можно получить, добавив рабочую нагрузку **Кроссплатформенная разработка .NET Core**. Добавить ее можно одним из двух способов в зависимости от того, какие обновления Visual Studio 2017 установлены на вашем компьютере.

#### <a name="option-1-use-the-new-project-dialog-box"></a>Вариант 1: использование диалогового окна "Новый проект"

1. Щелкните ссылку **Открыть установщик Visual Studio** в левой области диалогового окна **Новый проект**.

   ![Выбор ссылки "Открыть Visual Studio Installer" в диалоговом окне "Новый проект"](../media/vs-open-visual-studio-installer-generic.png)

1. Запускается Visual Studio Installer. Выберите рабочую нагрузку **Кроссплатформенная разработка .NET Core** и затем элемент **Изменить**.

   ![Рабочая нагрузка "Кроссплатформенная разработка .NET Core" в Visual Studio Installer](../media/tutorial-aspnet-workload.png)

#### <a name="option-2-use-the-tools-menu-bar"></a>Вариант 2: использование меню "Сервис"

1. Закройте диалоговое окно **Новый проект** и в верхней строке меню выберите **Сервис** > **Получить средства и компоненты**.

1. Запускается Visual Studio Installer. Выберите рабочую нагрузку **Кроссплатформенная разработка .NET Core** и затем элемент **Изменить**.

## <a name="create-a-what-is-your-name-application"></a>Создание приложения для запроса имени

Давайте создадим приложение, которое запрашивает имя пользователя, а затем выводит его вместе с датой и временем. Это делается так.

1. Откройте проект *WhatIsYourName*, если он еще не открыт.

1. Введите следующий код Visual Basic между первой открывающей скобкой после строки `Sub Main(args As String())` и строкой `End Sub`:

     ```vb
     Console.WriteLine(vbCrLf + "What is your name? ")
     Dim name = Console.ReadLine()
     Dim currentDate = DateTime.Now
     Console.WriteLine($"{vbCrLf}Hello, {name}, on {currentDate:d} at {currentDate:t}")
     Console.Write(vbCrLf + "Press any key to exit... ")
     Console.ReadKey(True)
    ```

    Этот код заменяет существующие операторы <xref:System.Console.WriteLine%2A>, <xref:System.Console.Write%2A> и <xref:System.Console.ReadKey%2A>.

   ![Окно кода с кодом приложения](media/vb-codewindow-what-name.png)

1. Когда откроется окно консоли, введите свое имя. Окно консоли должно выглядеть так, как показано на следующем снимке экрана:

   ![Окно консоли с вопросом "What Is Your Name" (Как вас зовут), временем и датой, а также сообщением "Press any key to continue" (Чтобы продолжить, нажмите любую клавишу)](media/vb-console-what-name.png)

1. Для закрытия консольного окна нажмите любую клавишу.

## <a name="create-a-calculate-this-application"></a>Создание приложения "Калькулятор"

1. Откройте Visual Studio 2017 и в верхней строке меню выберите **Файл** > **Создать** > **Проект**.

1. В левой области диалогового окна **Новый проект** разверните узел **Visual Basic** и выберите **.NET Core**. На средней панели выберите **Консольное приложение (.NET Core)**. Назовите файл *CalculateThis*.

1. Введите следующий код между строками `Module Program` и `End Module`:

   ```vb
   Public num1 As Integer
   Public num2 As Integer
   Public answer As Integer
   Sub Main()
       Console.WriteLine("Type a number and press Enter")
       num1 = Console.ReadLine()
       Console.WriteLine("Type another number to add to it and press Enter")
       num2 = Console.ReadLine()
       answer = num1 + num2
       Console.WriteLine("The answer is " & answer)
       Console.ReadLine()
   End Sub
   ```

   Окно кода должно выглядеть так, как показано на следующем снимке экрана:

   ![Окно кода с кодом приложения "Калькулятор"](media/vb-codewindow-calculate-this.png)

1. Щелкните **CalculateThis**, чтобы запустить программу. Окно консоли должно выглядеть так, как показано на следующем снимке экрана:

    ![Окно консоли с приложением CaluculateThis, включая предложения выполнить действия.](media/vb-console-calculate-this.png)

## <a name="quick-answers-faq"></a>Быстрые ответы на часто задаваемые вопросы

Ниже приведен краткий список вопросов и ответов, с помощью которого вы сможете ознакомиться с некоторыми основными понятиями.

### <a name="what-is-visual-basic"></a>Что такое Visual Basic?

Visual Basic — это типобезопасный язык программирования, который прост в изучении. Он является производным от языка BASIC (Beginner's All-purpose Symbolic Instruction Code — универсальный код символических инструкций для начинающих).

### <a name="what-is-visual-studio"></a>Что такое Visual Studio?

Visual Studio — это интегрированный набор средств разработки. Его можно рассматривать как программу для создания приложений.

### <a name="what-is-a-console-app"></a>Что такое консольное приложение?

Консольное приложение принимает входные данные и выводит результаты в окне командной строки, также называемом консолью.

### <a name="what-is-net-core"></a>Что такое .NET Core?

.NET Core — это дальнейший этап развития платформы .NET Framework. В то время как платформа .NET Framework позволяла использовать один и тот же код в средах разных языков программирования, в .NET Core появилась возможность использовать один и тот же код на разных платформах. Более того, это платформа с открытым кодом. (Как .NET Framework, так и .NET Core включают в себя готовые библиотеки, предоставляющие определенные функциональные возможности, а также среду CLR, которая выступает в роли виртуальной машины для выполнения кода.)

## <a name="next-steps"></a>Следующие шаги

Поздравляем с завершением этого учебника! Для получения дополнительных сведений перейдите к следующему руководству.

> [!div class="nextstepaction"]
> [Создание библиотеки .NET Standard с помощью Visual Basic и пакета SDK для .NET Core в Visual Studio 2017](/dotnet/core/tutorials/vb-library-with-visual-studio)

## <a name="see-also"></a>См. также

* [Пошаговые руководства по Visual Basic](/dotnet/visual-basic/walkthroughs)
* [Справочник по языку Visual Basic](/dotnet/visual-basic/language-reference/index)
* [IntelliSense для файлов кода Visual Basic](../../ide/visual-basic-specific-intellisense.md)
