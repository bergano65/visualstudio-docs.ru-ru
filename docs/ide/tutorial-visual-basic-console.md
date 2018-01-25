---
title: "Начало работы с Visual Basic в Visual Studio | Документы Майкрософт"
ms.custom: 
ms.date: 12/08/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-acquisition
ms.tgt_pltfrm: 
ms.topic: tutorial
ms.devlang: vb
author: TerryGLee
ms.author: tglee
manager: ghogen
dev_langs: vb
ms.workload: multiple
ms.openlocfilehash: b1de10c76d6a974280bfe016490a7567d0807675
ms.sourcegitcommit: bd16e764134c436d2d2f46490f51234d5246ee50
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/22/2018
---
# <a name="getting-started-with-visual-basic-in-visual-studio"></a>Начало работы с Visual Basic в Visual Studio
В этом учебнике по Visual Basic вы используете среду Visual Studio для создания и запуска нескольких разных консольных приложений. В процессе работы вы ознакомитесь с некоторыми возможностями [интегрированной среды разработки (IDE)](visual-studio-ide.md) Visual Studio.

Установите Visual Studio бесплатно со страницы [скачиваемых материалов Visual Studio](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs), если еще не сделали этого.

## <a name="before-you-begin"></a>Подготовка к работе
Ниже приведен краткий список вопросов и ответов, с помощью которого вы сможете ознакомиться с некоторыми основными понятиями.
### <a name="what-is-visual-basic"></a>Что такое Visual Basic?
Visual Basic — это типобезопасный язык программирования, который прост в изучении. Он является производным от языка BASIC (Beginner's All-purpose Symbolic Instruction Code — универсальный код символических инструкций для начинающих).
### <a name="what-is-visual-studio"></a>Что такое Visual Studio?
Visual Studio — это интегрированный набор средств разработки. Его можно рассматривать как программу для создания приложений.  
### <a name="what-is-a-console-app"></a>Что такое консольное приложение?
Консольное приложение принимает входные данные и выводит результаты в окне командной строки, также называемом консолью.
### <a name="what-is-net-core"></a>Что такое .NET Core?
.NET Core — это дальнейший этап развития платформы .NET Framework. В то время как платформа .NET Framework позволяла использовать один и тот же код в средах разных языков программирования, в .NET Core появилась возможность использовать один и тот же код на разных платформах. Более того, это платформа с открытым кодом. (Как .NET Framework, так и .NET Core включают в себя готовые библиотеки, предоставляющие определенные функциональные возможности, а также среду CLR, которая выступает в роли виртуальной машины для выполнения кода.)

## <a name="start-developing"></a>Начало разработки
Готовы приступить к разработке? Вперед!

### <a name="create-a-project"></a>Создание проекта
Сначала мы создадим проект приложения Visual Basic. Для этого типа проекта уже имеются все нужные файлы шаблонов, что избавляет вас от лишней работы.

1. Откройте Visual Studio 2017.

2. В верхней строке меню выберите **Файл** > **Создать** > **Проект...**.

3. В левой области диалогового окна **Новый проект** разверните узел **Visual Basic** и выберите **.NET Core**. На средней панели выберите **Консольное приложение (.NET Core)**. Назовите файл *HelloWorld*.  

   ![Шаблон проекта "Консольное приложение (.NET Core)" в диалоговом окне "Новый проект" в интегрированной среде разработки Visual Studio](../ide/media/new-project-vb-dotnetcore-whatisyourname-console-app.png)

#### <a name="add-a-workgroup-optional"></a>Добавление рабочей нагрузки (необязательно)
Если шаблон проекта **Консольное приложение (.NET Core)** отсутствует, его можно получить, добавив рабочую нагрузку **Кроссплатформенная разработка .NET Core**. Добавить ее можно одним из двух способов в зависимости от того, какие обновления Visual Studio 2017 установлены на вашем компьютере.

##### <a name="option-1-use-the-new-project-dialog-box"></a>Способ 1. Диалоговое окно "Новый проект"
1. Щелкните ссылку **Открыть установщик Visual Studio** в левой области диалогового окна **Новый проект**.

  ![Выбор ссылки "Открыть Visual Studio Installer" в диалоговом окне "Новый проект"](../ide/media/vs-open-visual-studio-installer-generic.png)

2. Запускается Visual Studio Installer. Выберите рабочую нагрузку **Кроссплатформенная разработка .NET Core** и затем элемент **Изменить**.

   ![Рабочая нагрузка "Кроссплатформенная разработка .NET Core" в Visual Studio Installer](../ide/media/dot-net-core-xplat-dev-workload.png)

##### <a name="option-2-use-the-tools-menu-bar"></a>Способ 2. Меню "Сервис"
1. Закройте диалоговое окно **Новый проект** и в верхней строке меню выберите **Сервис** > **Получить средства и компоненты...**.

2. Запускается Visual Studio Installer. Выберите рабочую нагрузку **Кроссплатформенная разработка .NET Core** и затем элемент **Изменить**.   

## <a name="create-a-what-is-your-name-application"></a>Создание приложения для запроса имени
Давайте создадим приложение, которое запрашивает имя пользователя, а затем выводит его вместе с датой и временем. Это делается так.

1. Откройте проект *WhatIsYourName*, если он еще не открыт.

2. Введите следующий код Visual Basic между первой открывающей скобкой после строки `Sub Main(args As String())` и строкой `End Sub`:

     ```vb
     Console.WriteLine(vbCrLf + "What is your name? ")
     Dim name = Console.ReadLine()
     Dim currentDate = DateTime.Now
     Console.WriteLine($"{vbCrLf}Hello, {name}, on {currentDate:d} at {currentDate:t}")
     Console.Write(vbCrLf + "Press any key to exit... ")
     Console.ReadKey(True)
    ```

    Этот код заменяет существующие операторы <xref:System.Console.WriteLine%2A>, <xref:System.Console.Write%2A> и <xref:System.Console.ReadKey%2A>.

 ![Окно кода с кодом приложения](../ide/media/vb-codewindow-what-name.png)

3. Когда откроется окно консоли, введите свое имя. Окно консоли должно выглядеть так, как показано на следующем снимке экрана:

   ![Окно консоли с вопросом "What Is Your Name" (Как вас зовут), временем и датой, а также сообщением "Press any key to continue" (Чтобы продолжить, нажмите любую клавишу)](../ide/media/vb-console-what-name.png)

5. Для закрытия консольного окна нажмите любую клавишу.

## <a name="create-a-calculate-this-application"></a>Создание приложения "Калькулятор"
1. Откройте Visual Studio 2017 и в верхней строке меню выберите **Файл** > **Создать** > **Проект...**.

2. В левой области диалогового окна **Новый проект** разверните узел **Visual Basic** и выберите **.NET Core**. На средней панели выберите **Консольное приложение (.NET Core)**. Назовите файл *CalculateThis*.  

3. Введите следующий код между строками `Module Program` и `End Module`:

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

   ![Окно кода с кодом приложения "Калькулятор"](../ide/media/vb-codewindow-calculate-this.png)

4. Щелкните **CalculateThis**, чтобы запустить программу. Окно консоли должно выглядеть так, как показано на следующем снимке экрана:       

    ![Окно консоли с приложением CaluculateThis, включая предложения выполнить действия.](../ide/media/vb-console-calculate-this.png)

Поздравляем с завершением этого учебника!

## <a name="see-also"></a>См. также
* [Руководство по Visual Basic](/dotnet/visual-basic/index)
* [Новые возможности в Visual Basic](/dotnet/visual-basic/getting-started/whats-new)
* [IntelliSense для файлов кода Visual Basic](visual-basic-specific-intellisense.md)
* [Справочник по языку Visual Basic](/dotnet/visual-basic/language-reference/index)
* Видеокурс [Основы программирования на Visual Basic для начинающих](https://mva.microsoft.com/en-us/training-courses/visual-basic-fundamentals-for-absolute-beginners-16507)
