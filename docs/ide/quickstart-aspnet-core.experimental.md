---
title: Создание веб-приложения ASP.NET Core в C# с помощью Visual Studio
description: Пошаговые инструкции по созданию в Visual Studio приложения Hello World на C# и ASP.NET Core
ms.custom: mvc
ms.date: 10/29/2018
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
ms.openlocfilehash: e85650f6671684f2d0ed313603f1af88e608e1d9
ms.sourcegitcommit: 401be39a42ffe007593528b5bba62583ca9fcafd
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/30/2018
ms.locfileid: "50244428"
---
# <a name="quickstart-use-visual-studio-to-create-your-first-aspnet-core-web-app"></a>Краткое руководство. Создание первого веб-приложения ASP.NET Core с помощью Visual Studio

В этом введении в использование Visual Studio (которое займет от 5 до 10 минут) с помощью шаблона проекта ASP.NET и языка программирования C# будет создано простое веб-приложение "Hello, World".

## <a name="before-you-begin"></a>Подготовка к работе

### <a name="install-visual-studio"></a>Установка Visual Studio

Установите Visual Studio бесплатно со страницы [скачиваемых материалов Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017), если еще не сделали этого.

### <a name="update-visual-studio"></a>Обновление Visual Studio

Если вы уже установили Visual Studio, убедитесь, что используется самый последний выпуск среды. Дополнительные сведения об обновлении установки см. на странице [Обновление до последнего выпуска Visual Studio 2017](../install/update-visual-studio.md).

### <a name="choose-your-theme-optional"></a>Выбор темы (необязательно)

В этом кратком руководстве содержатся снимки экрана, использующие темную тему. Если вы не используете темную тему, но хотите переключиться на нее, см. страницу [Персонализация интегрированной среды разработки и редактора Visual Studio](quickstart-personalize-the-ide.md).

## <a name="create-a-project"></a>Создание проекта

Сначала вы создадите проект веб-приложения ASP.NET Core. Ниже описывается порядок действий.

1. Откройте Visual Studio 2017.

1. В верхней строке меню выберите **Файл** > **Создать** > **Проект**.

1. В левой панели диалогового окна **Новый проект** разверните узел **Visual C#** и выберите **.NET Core**. В средней области выберите **Веб-приложение ASP.NET Core**. Затем назовите файл `HelloWorld` и нажмите кнопку **ОК**.

1. В диалоговом окне **Создание веб-приложения ASP.NET Core** в верхнем раскрывающемся меню выберите **ASP.NET Core 2.0** или более позднюю версию, а затем щелкните **Веб-приложение**.

   > [!NOTE]
   > Если **ASP.NET Core 2.0** или более поздняя версия не отображается в верхнем раскрывающемся меню, убедитесь, что вы используете самый последний выпуск Visual Studio. Дополнительные сведения об обновлении установки см. на странице [Обновление до последнего выпуска Visual Studio 2017](../install/update-visual-studio.md).

   ![Просмотрите анимированный GIF-файл, демонстрирующий создание проекта ASP.NET Core в Visual Studio на C#.](../ide/media/csharp-aspnet-animated-create-project.gif)

   Через некоторое время файл проекта откроется в Visual Studio.

   > [!NOTE]
   > Если категория шаблона проекта **.NET Core** отсутствует, выберите слева ссылку **Открыть Visual Studio Installer**. (В зависимости от параметров отображения может потребоваться выполнить прокрутку.)
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

1. В Visual Studio в разделе **Обозреватель решений** разверните папку **Страницы**. Затем выберите **About.cshtml**.

   ![Выбор файла About.cshtml из обозревателя решений](../ide/media/csharp-aspnet-about-page-html-file.png)

   Этот файл соответствует странице с заголовком **О программе** веб-приложения, которое запускается в веб-браузере.

   ![Страница "О программе" в веб-приложении](../ide/media/csharp-aspnet-about-page.png)

1. В редакторе кода Visual Studio измените текст additional information (дополнительные сведения) на **Hello World!**.

1. В **обозревателе решений** разверните **About.cshtml** и выберите **About.cshtml.cs**.

1. Измените текст сообщения для чтения "описание приложения" на **Мое сообщение**.

1. Выберите **IIS Express** или нажмите клавиши **CTRL**+**F5**, чтобы запустить приложение и открыть его в веб-браузере.

   ![Просмотрите анимированный GIF-файл, демонстрирующий создание и запуск веб-приложения ASP.NET Core в Visual Studio на C#.](../ide/media/csharp-aspnet-animated-hello-world.gif)

   > [!NOTE]
   > Если выводится сообщение об ошибке с текстом **Не удается подключиться к веб-серверу IIS Express** или сообщение об ошибке, где упоминается SSL-сертификат, закройте Visual Studio. После этого откройте Visual Studio с помощью пункта **Запуск от имени администратора** контекстного меню. Затем снова запустите приложение.

1. В веб-браузере убедитесь, что страница **О программе** содержит введенный вами текст.

1. Закройте веб-браузер.

Поздравляем с завершением этого краткого руководства! Надеемся, что вы узнали что-то новое о C#, ASP.NET Core и интегрированной среде разработки Visual Studio IDE.

## <a name="next-steps"></a>Следующие шаги

Для получения дополнительных сведений перейдите к следующему руководству:

> [!div class="nextstepaction"]
> [Начало работы с C# и ASP.NET в Visual Studio](tutorial-csharp-aspnet-core.md)

## <a name="see-also"></a>См. также

[Публикация веб-приложения в службе приложений Azure с помощью Visual Studio](..//deployment/quickstart-deploy-to-azure.md)
