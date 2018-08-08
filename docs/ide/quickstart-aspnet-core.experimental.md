---
title: Создание веб-приложения ASP.NET Core в C# с помощью Visual Studio
description: Пошаговые инструкции по созданию веб-приложения ASP.NET Core в Visual Studio на C#.
ms.custom: mvc
ms.date: 07/30/2018
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.topic: quickstart
author: TerryGLee
ms.author: tglee
manager: douge
dev_langs:
- CSharp
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: 9978a7eb80a833eeb81796694b958a62a35cd347
ms.sourcegitcommit: 0cf1e63b6e0e6a0130668278489b21a6e5038084
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/02/2018
ms.locfileid: "39469143"
---
# <a name="quickstart-use-visual-studio-to-create-your-first-aspnet-core-web-app"></a>Краткое руководство. Создание первого веб-приложения ASP.NET Core с помощью Visual Studio

В этом введении в использование Visual Studio (которое займет от 5 до 10 минут) с помощью шаблона проекта ASP.NET и языка программирования C# будет создано простое веб-приложение "Hello, World".

Установите Visual Studio бесплатно со страницы [скачиваемых материалов Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017), если еще не сделали этого.

## <a name="create-a-project"></a>Создание проекта

Сначала вы создадите проект веб-приложения ASP.NET Core. Ниже описывается порядок действий.

1. Откройте Visual Studio 2017.

1. В верхней строке меню выберите **Файл** > **Создать** > **Проект**.

1. В левой панели диалогового окна **Новый проект** разверните узел **Visual C#** и выберите **.NET Core**. В средней области выберите **Веб-приложение ASP.NET Core**. Затем назовите файл `HelloWorld` и нажмите кнопку **ОК**.

1. Убедитесь, что в верхнем раскрывающемся меню диалогового окна **Создать веб-приложение ASP.NET Core** появилось **ASP.NET Core 2.0**. Затем выберите **Веб-приложение** и нажмите кнопку **ОК**.

  ![Просмотрите анимированный GIF-файл, демонстрирующий создание проекта ASP.NET Core в Visual Studio на C#.](../ide/media/csharp-aspnet-animated-create-project.gif)

  Через некоторое время файл проекта откроется в Visual Studio.

   > [!NOTE]
   > Если категория шаблона проекта **.NET Core** отсутствует, выберите слева ссылку **Открыть Visual Studio Installer**.
   >
   > ![Открыть Visual Studio Installer в диалоговом окне "Новый проект"](../ide/media/open-visual-studio-installer.png)
   >
   > Запускается Visual Studio Installer. Выберите рабочую нагрузку **ASP.NET и разработка веб-приложений**, а затем щелкните **Изменить**.
   >
   > ![Рабочая нагрузка ASP.NET в установщике Visual Studio](../ide/media/quickstart-aspnet-workload.png)
   >
   > (Возможно, перед тем как продолжить установку рабочей нагрузки, придется закрыть Visual Studio.)

## <a name="create-and-run-the-app"></a>Создание и запуск приложения

Далее вы создадите и запустите веб-приложение "Hello World". Ниже описывается порядок действий.

1. В **обозревателе решений** разверните папку **Страницы** и выберите **About.cshtml**.

   Этот файл соответствует странице веб-приложения с именем **О программе**.

   ![Страница "О программе" в веб-приложении](../ide/media/csharp-aspnet-about-page.png)

1. Измените текст для чтения "дополнительная информация" на **Hello World!**.

1. В **обозревателе решений** разверните **About.cshtml** и выберите **About.cshtml.cs**.

1. Измените текст сообщения для чтения "описание приложения" на **Мое сообщение**.

1. Выберите **IIS Express** или нажмите клавиши **CTRL**+**F5**, чтобы запустить приложение и открыть его в веб-браузере.

  ![Просмотрите анимированный GIF-файл, демонстрирующий создание и запуск веб-приложения ASP.NET Core в Visual Studio на C#.](../ide/media/csharp-aspnet-animated-hello-world.gif)

   > [!NOTE]
   > Если появляется сообщение об ошибке **Не удается подключиться к веб-серверу "IIS Express"**, закройте среду Visual Studio и откройте ее с помощью пункта **Запуск от имени администратора** в контекстном меню. Затем снова запустите приложение.

1. Проверьте, содержится ли на странице **О программе** обновленный текст.

1. Закройте веб-браузер.

Поздравляем с завершением этого краткого руководства! Надеемся, что вы узнали что-то новое о C#, ASP.NET Core и интегрированной среде разработки Visual Studio IDE.

## <a name="next-steps"></a>Следующие шаги

Для получения дополнительных сведений перейдите к следующему руководству:

> [!div class="nextstepaction"]
> [Начало работы с C# и ASP.NET в Visual Studio](tutorial-csharp-aspnet-core.md)

## <a name="see-also"></a>См. также

[Публикация веб-приложения в службе приложений Azure с помощью Visual Studio](..//deployment/quickstart-deploy-to-azure.md)
