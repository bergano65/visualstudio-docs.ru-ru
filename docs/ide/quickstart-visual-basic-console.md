---
title: Создание первого консольного приложения на Visual Basic
description: Ознакомьтесь с пошаговыми инструкциями по созданию простого консольного приложения "Hello World" на Visual Basic в Visual Studio.
ms.custom: seodec18
ms.date: 03/23/2019
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: quickstart
ms.devlang: vb
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- vb
ms.workload:
- multiple
ms.openlocfilehash: c7da73ac3f47b6b63817ff905923b71e3354b06c
ms.sourcegitcommit: 44e9b1d9230fcbbd081ee81be9d4be8a485d8502
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/30/2019
ms.locfileid: "70180080"
---
# <a name="quickstart-create-your-first-console-app-in-visual-studio-with-visual-basic"></a>Краткое руководство. Создание первого консольного приложения на Visual Basic в Visual Studio

В рамках этого краткого (на 5–10 минут) знакомства с возможностями интегрированной среды разработки Visual Studio (IDE) вы создадите простое приложение на Visual Basic, выполняющееся в консоли.

::: moniker range="vs-2017"

Установите Visual Studio бесплатно со страницы [скачиваемых материалов Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download), если еще не сделали этого.

::: moniker-end

::: moniker range="vs-2019"

Установите Visual Studio бесплатно со страницы [скачиваемых материалов Visual Studio](https://visualstudio.microsoft.com/downloads), если еще не сделали этого.

::: moniker-end

## <a name="create-a-project"></a>Создание проекта

Сначала вы создадите проект приложения Visual Basic. Для этого типа проекта уже имеются все нужные файлы шаблонов, что избавляет вас от лишней работы.

::: moniker range="vs-2017"

1. Откройте Visual Studio 2017.

2. В верхней строке меню последовательно выберите **Файл** > **Создать** > **Проект**.

3. В левой области диалогового окна **Новый проект** разверните узел **Visual Basic** и выберите **.NET Core**. На средней панели выберите **Консольное приложение (.NET Core)** . Назовите проект *HelloWorld*.

   ![Шаблон проекта "Консольное приложение (.NET Core)" в диалоговом окне "Новый проект" в интегрированной среде разработки Visual Studio](../ide/media/new-project-vb-dotnetcore-helloworld-console-app.png)

     Если шаблон проекта **Консольное приложение (.NET Core)** отсутствует, выберите ссылку **Открыть Visual Studio Installer** в левой области диалогового окна **Новый проект**.

   ![Выбор ссылки "Открыть Visual Studio Installer" в диалоговом окне "Новый проект"](../ide/media/vb-open-visual-studio-installer-hello-world.png)

     Запускается Visual Studio Installer. Выберите рабочую нагрузку **Кроссплатформенная разработка .NET Core** и затем элемент **Изменить**.

     ![Рабочая нагрузка "Кроссплатформенная разработка .NET Core" в Visual Studio Installer](../ide/media/dot-net-core-xplat-dev-workload.png)

::: moniker-end

::: moniker range="vs-2019"

> [!NOTE]
> На некоторых снимках экрана в этом кратком руководстве используется темная тема. Если вы не используете темную тему, но хотите переключиться на нее, см. страницу [Персонализация интегрированной среды разработки и редактора Visual Studio](quickstart-personalize-the-ide.md).

1. Запустите Visual Studio 2019.

1. На начальном экране выберите **Создать проект**.

   ![Просмотр окна "Создание проекта"](../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. В поле поиска окна **Создание проекта** введите *консоль*. Затем выберите **Visual Basic** в списке языков и **Windows** в списке платформ. 

   Применив фильтры языка и платформы, выберите шаблон **Консольное приложение (.NET Core)** и нажмите кнопку **Далее**.

   ![Выбор шаблона Visual Basic для консольного приложения (.NET Framework)](../get-started/visual-basic/media/vs-2019/vb-create-new-project-search-console-net-core-filtered.png)

   > [!NOTE]
   > Если шаблон **Консольное приложение (.NET Core)** отсутствует, его можно установить из окна **Создание проекта**. В сообщении **Не нашли то, что искали?** выберите ссылку **Установка других средств и компонентов**.
   >
   > ![Ссылка "Установка других средств и компонентов" из сообщения "Не нашли то, что искали?" в окне "Создание проекта"](../get-started/media/vs-2019/not-finding-what-looking-for.png) 
   > 
   > После этого в Visual Studio Installer выберите рабочую нагрузку **Кроссплатформенная разработка .NET Core**.
   >
   > ![Рабочая нагрузка "Кроссплатформенная разработка .NET Core" в Visual Studio Installer](../get-started/media/dot-net-core-xplat-dev-workload.png)
   >
   > Затем нажмите кнопку **Изменить** в Visual Studio Installer. Вам может быть предложено сохранить результаты работы; в таком случае сделайте это. Выберите **Продолжить**, чтобы установить рабочую нагрузку. После этого вернитесь к шагу 2 в процедуре [Создание проекта](#create-a-project).

1. В поле **Имя проекта** окна **Настроить новый проект** введите *WhatIsYourName*. Затем нажмите **Создать**.

   ![В окне "Настроить новый проект" назовите проект "WhatIsYourName"](../get-started/visual-basic/media/vs-2019/vb-name-your-project-whatname.png)

   Новый проект открывается в Visual Studio.

::: moniker-end

## <a name="create-the-application"></a>Создание приложения

Когда вы выберете шаблон проекта Visual Basic и зададите имя проекта, Visual Studio создает простое приложение "Hello World". Он вызывает метод <xref:System.Console.WriteLine%2A> для отображения литеральной строки "Hello World!" в окне консоли.

![Просмотр кода "Hello World" по умолчанию на основе шаблона](../ide/media/vb-console-helloworld-template.png)

Вы можете запустить программу в режиме отладки, нажав кнопку **HelloWorld** в интегрированной среде разработки.

  ![Нажмите кнопку "HelloWorld", чтобы запустить программу в режиме отладки](../ide/media/vb-console-hello-world-button.png)

При этом окно консоли отображается на короткое время и затем сразу же закрывается. Это происходит потому, что метод `Main` завершается после выполнения его единственного оператора, после чего завершается работа приложения.

### <a name="add-some-code"></a>Добавление кода

Давайте добавим код, чтобы приостановить выполнение приложения и запросить ввод данных пользователем.

1. Добавьте следующий код сразу после вызова метода <xref:System.Console.WriteLine%2A>:

   ```vb
   Console.Write("Press any key to continue...")
   Console.ReadKey(true)
   ```

    Это приостанавливает выполнение программы до нажатия клавиши.

2. В строке меню выберите **Сборка** > **Собрать решение**.

   При этом программа компилируется в промежуточный язык IL, который затем преобразуется в двоичный код JIT-компилятором.

## <a name="run-the-application"></a>Запуск приложения

1. В панели инструментов нажмите кнопку **HelloWorld**.

   ![Нажмите кнопку "HelloWorld", чтобы запустить программу из панели инструментов](../ide/media/vb-console-hello-world-button.png)

2. Для закрытия консольного окна нажмите любую клавишу.

   ![Окно консоли с фразой "Hello World" и надписью "Чтобы продолжить, нажмите любую клавишу"](../ide/media/vb-console-hello-world-press-any-key.png)

## <a name="next-steps"></a>Следующие шаги

Поздравляем с завершением этого краткого руководства! Надеемся, что вы узнали нечто новое о Visual Basic и интегрированной среде разработки Visual Studio. Для получения дополнительных сведений перейдите к следующему учебнику.

> [!div class="nextstepaction"]
> [Начало работы с Visual Basic в Visual Studio](../get-started/visual-basic/tutorial-console.md)
