---
title: Краткое руководство. Создание веб-службы ASP.NET Core в F#
description: Пошаговые инструкции по созданию веб-службы ASP.NET Core в Visual Studio на F#.
ms.date: 08/24/2018
ms.topic: quickstart
author: cartermp
ms.author: phcart
manager: andrehal
dev_langs:
- FSharp
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: 166ff1fae5cbc494fe287a47a2983fc52364493b
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2019
ms.locfileid: "55934670"
---
# <a name="quickstart-use-visual-studio-to-create-your-first-aspnet-core-web-service-in-f"></a>Краткое руководство. Создание первой веб-службы ASP.NET Core на F# с помощью Visual Studio

В этом кратком руководстве по F# в Visual Studio рассматривается создание веб-приложения ASP.NET Core на F#.

Установите Visual Studio бесплатно со страницы [скачиваемых материалов Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017), если еще не сделали этого.

## <a name="create-a-project"></a>Создание проекта

Сначала вы создадите проект веб-API ASP.NET Core. Для этого типа проекта имеются файлы шаблонов, составляющие рабочую веб-службу, — пока вам даже не пришлось ничего делать!

1. Откройте Visual Studio 2017.

2. В верхней строке меню выберите **Файл** > **Создать** > **Проект**.

3. В левой области диалогового окна **Новый проект** разверните узел **Visual F#** и выберите **Веб**. В средней области выберите **Веб-приложение ASP.NET Core** и нажмите кнопку **ОК**.

     Если категория шаблона проекта **.NET Core** отсутствует, выберите слева ссылку **Открыть Visual Studio Installer**. Запускается Visual Studio Installer. Выберите рабочую нагрузку **ASP.NET и разработка веб-приложений**, а затем щелкните **Изменить**.

     ![Рабочая нагрузка ASP.NET в установщике Visual Studio](../ide/media/quickstart-aspnet-workload.png)

4. В верхнем раскрывающемся меню диалогового окна **Создать веб-приложение ASP.NET Core** выберите **ASP.NET Core 2.1**. (Если вы не видите **ASP.NET Core 2.1** в списке, установите его, пройдя по ссылке **скачивание**, которая должна появиться на желтой панели в верхней части диалогового окна.) Нажмите кнопку **ОК**.

## <a name="explore-the-ide"></a>Изучение интегрированной среды разработки

1. На панели инструментов **обозревателя решений** разверните папку **Контроллеры** и выберите файл **ValuesController.fs**, чтобы открыть его в редакторе.

   ![Обозреватель решений с папкой контроллеров, развернутой в проекте веб-API F#](../ide/media/hello-world-fs-sln-explorer.png)

2. Затем замените член `Get()` на следующий код:

   ```fsharp
   [<HttpGet>]
   member this.Get() =
       let values = [|"Hello"; "World"; "First F#/ASP.NET Core web API!"|]
       ActionResult<string[]>(values)
   ```

Код простой. Массив значений F# привязывается к имени `values`, а затем передается на платформу ASP.NET Core MVC как `ActionResult`. Остальное ASP.NET Core берет на себя.

В редакторе он должен выглядеть следующим образом:

![Измененный член Get](../ide/media/hello-world-fs-get-member.png)

## <a name="run-the-application"></a>Запуск приложения

1. Нажмите клавиши **CTRL**+**F5**, чтобы запустить приложение и открыть его в веб-браузере.

2. Страница должна перейти на маршрут `/api/values`, но, если этого не случится, введите `https://localhost:44396/api/values` в адресную строку браузера.

В веб-браузере отобразится JSON, соответствующий введенному вами ранее коду.

## <a name="next-steps"></a>Следующие шаги

Поздравляем с завершением этого краткого руководства! Надеемся, что вы узнали что-то новое о F#, ASP.NET Core и интегрированной среде разработки Visual Studio. Чтобы просмотреть приложение, работающее на общедоступном сервере, нажмите указанную ниже кнопку.

> [!div class="nextstepaction"]
> [Развертывание приложения в Службе приложений Azure](../deployment/quickstart-deploy-to-azure.md)

Чтобы узнать больше о языке F#, ознакомьтесь с официальным [руководством по F#](/dotnet/fsharp/index).