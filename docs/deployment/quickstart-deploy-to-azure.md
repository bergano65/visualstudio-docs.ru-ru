---
title: Опубликовать в службе приложений Azure — Visual Studio | Документы Microsoft
ms.custom: ''
ms.date: 11/22/2017
ms.technology: vs-ide-deployment
ms.topic: quickstart
helpviewer_keywords:
- deployment, website
ms.assetid: fc82b1f1-d342-4b82-9a44-590479f0a895
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- azure
ms.openlocfilehash: f91fd6e8c101b674b745c120978a47adb17c9b91
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/05/2018
ms.locfileid: "34765379"
---
# <a name="publish-an-aspnet-or-aspnet-core-app-to-azure-app-service-using-visual-studio"></a>Публикация приложений ASP.NET или ASP.NET Core для службы приложений Azure с помощью Visual Studio

Можно использовать **публикации** средство для публикации приложений ASP.NET, ASP.NET Core, Python, Node.js и .NET Core в службе приложений Azure.

Если вы еще нет учетной записи Azure, вы можете [регистрации здесь](https://azure.microsoft.com/free/?ref=microsoft.com&utm_source=microsoft.com&utm_medium=doc&utm_campaign=visualstudio).

## <a name="prerequisites"></a>Предварительные требования

* Необходимо иметь Visual Studio 2017 г. установлен и **ASP.NET и веб-разработки** рабочей нагрузки и. **NET разработки настольных приложений** рабочей нагрузки. Для приложения .NET Core, необходим. **NET Core** рабочей нагрузки.

    Установите Visual Studio бесплатно со страницы [скачиваемых материалов Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017), если еще не сделали этого.

## <a name="create-a-new-project"></a>Создание нового проекта 

1. В Visual Studio последовательно выберите **Файл > Создать проект**.

1. В разделе **Visual C#** или **Visual Basic**, выберите **Web**, а затем в средней области выберите **веб-приложения ASP.NET (.NET Framework)**(только C#) или **веб-приложения ASP.NET Core**, а затем нажмите кнопку **ОК**.

1. Выберите **MVC** (или выберите **веб-приложения (Model-View-Controller)** для .NET Core), убедитесь, что **без проверки подлинности** выбран и нажмите кнопку **ОК** .

1. Введите имя, например **MyWebApp** и нажмите кнопку **ОК**.

    Visual Studio создаст проект.

1. Выберите **сборки > построить решение** для сборки проекта.

## <a name="publish-to-azure-app-service"></a>Публикация в службу приложений Azure

1. В обозревателе решений щелкните проект правой кнопкой мыши и выберите пункт **Опубликовать**.

    ![Выберите опубликовать](../deployment/media/quickstart-publish-aspnet.png "выберите публикации")

1. Если были настроены ранее все профили публикации **публикации** появится область. Нажмите кнопку **Создание нового профиля**.

1. В **выбрать место назначения публикации** диалогового окна выберите **службы приложений**.

    ![Выберите службы приложений Azure](../deployment/media/quickstart-publish-azure.png "выберите службы приложений Azure")

1. Нажмите кнопку **Опубликовать**.

    **Создание приложения службы** откроется диалоговое окно.

    ![Создание приложения службы](../deployment/media/quickstart-publish-settings-app-service.png "создания службы приложений Azure")
    
1. Если вы не вошли в Visual Studio, войдите и заполните поля параметров по умолчанию приложение службы.

    Профиль публикации, параметры, откроется диалоговое окно.

    ![Выберите папку](../deployment/media/quickstart-publish-settings-web.png "выберите папку")

    В этом диалоговом окне можно выберите подписку, которую вы используете, выбрать или создать группы ресурсов Azure и т. д.

1. Нажмите кнопку **Создать**.

    Visual Studio развертывает приложение в службе приложений Azure, и загружает веб-приложения в браузере.

    В сводке **публикации** панели отображается URL-адрес сайта для новой службы приложения Azure.

## <a name="next-steps"></a>Следующие шаги

В этом кратком руководстве вы узнали, как использовать Visual Studio для создания профиля публикации для развертывания в Azure. Вы можете также настроить публикацию профиля путем импорта параметрами публикации из службы приложений Azure.

> [!div class="nextstepaction"]
> [Импорт параметров публикации и развертывание в Azure](tutorial-import-publish-settings-azure.md)
