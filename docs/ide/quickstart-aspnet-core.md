---
title: Создание веб-приложения ASP.NET Core на C#
description: Пошаговые инструкции по созданию в Visual Studio приложения Hello World на C# и ASP.NET Core
ms.date: 10/29/2018
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.custom: mvc,seodec18
ms.topic: quickstart
author: TerryGLee
ms.author: tglee
manager: douge
dev_langs:
- CSharp
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: fb9dbc94d06bbb260884a2379e2427969fec1031
ms.sourcegitcommit: 0cdd8e8a53fb4fd5e869f07c35204419fa12783d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/10/2018
ms.locfileid: "53159247"
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

Сначала вы создадите проект веб-приложения ASP.NET Core. Для этого типа проекта уже имеются все нужные файлы шаблонов, необходимые для создания веб-приложения, что избавляет вас от лишней работы.

1. Откройте Visual Studio 2017.

1. В верхней строке меню выберите **Файл** > **Создать** > **Проект**.

1. В левой панели диалогового окна **Новый проект** разверните узел **Visual C#** и выберите **.NET Core**. В средней области выберите **Веб-приложение ASP.NET Core**. Затем назовите файл `HelloWorld` и нажмите кнопку **ОК**.

   ![Создание проекта веб-приложения ASP.NET Core для C#](../ide/media/csharp-aspnet-choose-template-name-file.png)

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

1. В верхнем раскрывающемся меню диалогового окна **Создание веб-приложения ASP.NET Core** выберите **ASP.NET Core 2.0** или более позднюю версию.

   > [!NOTE]
   > Если **ASP.NET Core 2.0** или более поздняя версия не отображается, убедитесь, что вы используете самый последний выпуск Visual Studio. Дополнительные сведения об обновлении установки см. на странице [Обновление до последнего выпуска Visual Studio 2017](../install/update-visual-studio.md).

1. Затем выберите **Веб-приложение** и нажмите кнопку **ОК**.

   ![Диалоговое окно "Создать веб-приложение ASP.NET Core"](../ide/media/quickstart-aspnet-core20.png)

Через некоторое время файл проекта откроется в Visual Studio.

## <a name="create-the-app"></a>Создание приложения

1. В **обозревателе решений** разверните папку **Страницы** и выберите **About.cshtml**.

   ![Выбор файла About.cshtml из обозревателя решений](../ide/media/csharp-aspnet-about-page-html-file.png)

   Этот файл соответствует странице веб-приложения с именем **О программе**.

   ![Страница "О программе" в веб-приложении](../ide/media/csharp-aspnet-about-page.png)

   В редакторе на странице **О программе** появится HTML-код для области дополнительной информации.

   ![Код HTML для области дополнительной информации в редакторе Visual Studio](../ide/media/csharp-aspnet-about-cshtml-page.png)

1. Измените текст для чтения "дополнительная информация" на **Hello World!**.

   ![Изменение значения по умолчанию кода HTML для области дополнительной информации в редакторе Visual Studio](../ide/media/csharp-aspnet-about-cshtml-page-hello-world.png)

1. В **обозревателе решений** разверните **About.cshtml** и выберите **About.cshtml.cs**. (Файл также соответствует странице веб-приложения **О программе**.)

   ![Выбор файла About.cshtml из обозревателя решений](../ide/media/csharp-aspnet-about-page-code-file.png)

   В редакторе появится код C#, который содержит текст для области описания приложения на странице **О программе**.

   ![Код C# для области описания приложения в редакторе Visual Studio](../ide/media/csharp-aspnet-about-cshtml-cs-code.png)

1. Измените текст сообщения для чтения "описание приложения" на **Мое сообщение**.

   ![Изменение текста сообщения по умолчанию для области описания приложения в редакторе Visual Studio](../ide/media/csharp-aspnet-about-cshtml-cs-message.png)

## <a name="run-the-app"></a>Запуск приложения

1. Нажмите клавиши **CTRL**+**F5**, чтобы запустить приложение и открыть его в веб-браузере.

   > [!NOTE]
   > Если выводится сообщение об ошибке с текстом **Не удается подключиться к веб-серверу IIS Express** или сообщение об ошибке, где упоминается SSL-сертификат, закройте Visual Studio. После этого откройте Visual Studio с помощью пункта **Запуск от имени администратора** контекстного меню. Затем снова запустите приложение.

1. В верхней части веб-страницы выберите **О программе**.

   ![Выбор пункта "О программе" на веб-странице](../ide/media/csharp-aspnet-home-page-about.png)

1. Просмотрите обновленный текст, который был добавлен на страницу **О программе**.

   ![Просмотр обновленной страницы "О программе", в которую был добавлен текст.](../ide/media/csharp-aspnet-about-page-hello-world.png)

1. Закройте веб-браузер.

Поздравляем с завершением этого краткого руководства! Надеемся, что вы узнали что-то новое о C#, ASP.NET Core и интегрированной среде разработки Visual Studio IDE.

## <a name="next-steps"></a>Следующие шаги

Для получения дополнительных сведений перейдите к следующему руководству:

> [!div class="nextstepaction"]
> [Начало работы с C# и ASP.NET в Visual Studio](tutorial-csharp-aspnet-core.md)

## <a name="see-also"></a>См. также

[Публикация веб-приложения в службе приложений Azure с помощью Visual Studio](../deployment/quickstart-deploy-to-azure.md)
