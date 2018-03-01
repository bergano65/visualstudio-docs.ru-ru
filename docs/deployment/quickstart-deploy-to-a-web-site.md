---
title: "Опубликовать на веб-сайт - Visual Studio | Документы Microsoft"
ms.custom: 
ms.date: 11/22/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: quickstart
helpviewer_keywords:
- deployment, website
ms.assetid: fc82b1f1-d342-4b82-9a44-590479f0a895
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: e324869eb90cd60cba68d9ed7b2e3fdb1ebb588d
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/10/2018
---
# <a name="publish-a-web-app-or-a-net-core-app-to-a-web-site-using-the-visual-studio-publish-tool"></a>Публикация веб-приложения или приложения .NET Core на веб-сайт, используя средство публикации Visual Studio

Можно использовать **публикации** средство для публикации приложения ASP.NET на веб-сайт.

Эти шаги применимы к ASP.NET, ASP.NET Core, .NET Core и Python приложений в Visual Studio. Для Node.js действия поддерживаются, но пользовательский интерфейс отличается.

## <a name="create-a-new-project"></a>Создание нового проекта 

1. В Visual Studio последовательно выберите **Файл > Создать проект**.

1. В разделе **Visual C#** или **Visual Basic**, выберите **Web**, а затем в средней области выберите **веб-приложения ASP.NET (.NET Framework)**(только C#) или **веб-приложения ASP.NET Core**, а затем нажмите кнопку **ОК**.

1. Выберите **MVC**, убедитесь, что **без проверки подлинности** выбран и нажмите кнопку **ОК**.

1. Введите имя, например **MyWebApp** и нажмите кнопку **ОК**.

    Visual Studio создаст проект.

1. Выберите **сборки > построить решение** для сборки проекта.

## <a name="publish-to-a-web-site"></a>Опубликовать на веб-сайт

1. В обозревателе решений щелкните проект правой кнопкой мыши и выберите пункт **Опубликовать**.

    ![Выберите опубликовать](../deployment/media/quickstart-publish-aspnet.png "выберите публикации")

1. В **публикации** области, выберите **IIS, FTP, и т. д**.

    ![Выберите IIS, FTP, т. д.](../deployment/media/quickstart-publish-iis-ftp.png "выберите IIS, FTP и т. д.")

1. Нажмите кнопку **Опубликовать**.

    Профиль публикации, параметры, откроется диалоговое окно.

    ![Выберите папку](../deployment/media/quickstart-publish-settings-web.png "выберите папку")

1. В **метод публикации** поля, такие как выбрать метод **веб-развертывания** или **FTP**.

    Параметры, которые вы видите рядом соответствуют способа публикации.

1. Настроить необходимые параметры для метода публикации и нажмите кнопку **проверить подключение**.

    Если сервер или целевой доступен, и все настройки указаны правильно, вы увидите сообщение, которое указывает соединение, которое проверяется, и вы готовы к публикации.

    ![Проверка подключения к](../deployment/media/quickstart-publish-web-deploy.png "Проверка подключения к")

1. Если вы хотите настроить другие параметры развертывания, нажмите кнопку **параметры**.

    Можно настроить параметры, как развернуть конфигурацию отладки или выпуска, а затем нажмите кнопку **Сохранить**. При удаленной отладке конфигурации отладки является обязательным.

1. Чтобы опубликовать, нажмите кнопку **публикации**.

    В окне вывода отображаются ход выполнения развертывания и результатов.

## <a name="next-steps"></a>Следующие шаги

- [Развертывание ASP.NET в службах IIS](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45)
