---
title: Создание первого консольного приложения на C# в Visual Studio
titleSuffix: ''
description: Ознакомьтесь с пошаговыми инструкциями по созданию простого консольного приложения "Hello World" на C# в Visual Studio.
ms.date: 09/21/2018
ms.prod: visual-studio-dev15
ms.custom: seodec18
ms.topic: quickstart
ms.devlang: vb
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: c41aac277136de164ba7148e26fc9c0f422b2eef
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "55014618"
---
# <a name="quickstart-use-visual-studio-to-create-your-first-c-console-app"></a>Краткое руководство. Создание первого консольного приложения на C# в Visual Studio

Изучение этого ознакомительного руководства по возможностям интегрированной среды разработки Visual Studio (IDE) займет 5–10 минут. В его рамках вы создадите простое приложение на C#, выполняющееся в консоли.

Установите Visual Studio бесплатно со страницы [скачиваемых материалов Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017), если еще не сделали этого.

## <a name="create-a-project"></a>Создание проекта

Сначала вы создадите проект приложения на C#. Для этого типа проекта уже имеются все нужные файлы шаблонов, что избавляет вас от лишней работы.

1. Откройте Visual Studio 2017.

2. В верхней строке меню выберите **Файл** > **Создать** > **Проект**.

3. В левой области диалогового окна **Новый проект** разверните узел **C#** и выберите **.NET Core**. На средней панели выберите **Консольное приложение (.NET Core)**. Назовите проект *HelloWorld*.

   ![Шаблон проекта "Консольное приложение (.NET Core)" в диалоговом окне "Новый проект" в интегрированной среде разработки Visual Studio](../ide/media/new-project-csharp-dotnetcore-helloworld-console-app.png)

     Если шаблона проекта **Console App (.NET Core)** (Консольное приложение (.NET Core)) нет, выберите ссылку **Открыть Visual Studio Installer** в левой области диалогового окна **Новый проект**.

   ![Выбор ссылки "Открыть Visual Studio Installer" в диалоговом окне "Новый проект"](../ide/media/csharp-open-visual-studio-installer-hello-world.png)

     Запускается Visual Studio Installer. Выберите рабочую нагрузку **Кроссплатформенная разработка .NET Core** и затем элемент **Изменить**.

     ![Рабочая нагрузка "Кроссплатформенная разработка .NET Core" в Visual Studio Installer](../ide/media/dot-net-core-xplat-dev-workload.png)

## <a name="create-the-application"></a>Создание приложения

Когда вы выберете шаблон проекта на C# и зададите имя проекта, Visual Studio создаст простое приложение "Hello World".

(Visual Studio вызывает метод <xref:System.Console.WriteLine%2A> для отображения строкового литерала "Hello World!" в окне консоли.)

   ![Просмотр кода "Hello World" по умолчанию на основе шаблона](../ide/media/csharp-console-helloworld-template.png)

Если нажать клавишу **F5**, программа запустится в режиме отладки. Но окно консоли отображается на короткое время, перед тем как закрыться.

(Это происходит потому, что метод `Main` завершается после выполнения его единственного оператора, после чего завершается работа приложения.)

### <a name="add-some-code"></a>Добавление кода

Добавим код для приостановки работы приложения, чтобы окно консоли не закрывалось, пока вы не нажмете клавишу **ВВОД**.

1. Добавьте следующий код сразу после вызова метода <xref:System.Console.WriteLine%2A>:

   ```csharp
   Console.ReadLine();
   ```

1. Убедитесь, что он выглядит в редакторе кода следующим образом:

   ![Добавление кода для приостановки приложения "Hello World"](../ide/media/csharp-console-helloworld-add-code.png)

## <a name="run-the-application"></a>Запуск приложения

1. Нажмите кнопку **HelloWorld** на панели инструментов, чтобы запустить приложение в режиме отладки. (Или нажмите клавишу **F5**.)

   ![Кнопка HelloWorld для запуска программы с панели инструментов](../ide/media/csharp-console-hello-world-button.png)

1. Просмотрите результат в окне консоли.

   ![Текст "Hello World!" в окне консоли](../ide/media/csharp-console-hello-world.png)

### <a name="close-the-application"></a>Закрытие приложения

1. Нажмите клавишу **ВВОД**, чтобы закрыть окно консоли.

1. Закройте область **вывода** в Visual Studio.

   ![Закрытие области вывода в Visual Studio](../ide/media/csharp-hello-world-close-output-pane.png)

1. Закройте Visual Studio.

## <a name="next-steps"></a>Следующие шаги

Поздравляем с завершением этого краткого руководства! Надеемся, что вы узнали кое-что новое о C# и интегрированной среде разработки Visual Studio. Дополнительные сведения см. по представленной ниже ссылке.

> [!div class="nextstepaction"]
> [Начало работы с консольным приложением на C# в Visual Studio](../get-started/csharp/tutorial-console.md)
