---
title: "Опубликовать в службе приложений Azure — Visual Studio | Документы Microsoft"
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
- azure
ms.openlocfilehash: 52da1a2e618d9ececa1c8fd0d90a86e651cd7fde
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/10/2018
---
# <a name="publish-an-aspnet-or-aspnet-core-app-to-azure-app-service-using-visual-studio"></a>Публикация приложений ASP.NET или ASP.NET Core для службы приложений Azure с помощью Visual Studio

Можно использовать **публикации** средство для публикации приложений ASP.NET, ASP.NET Core, Python, Node.js и .NET Core в службе приложений Azure.

Если вы еще нет учетной записи Azure, вы можете [регистрации здесь](https://azure.microsoft.com/free/?ref=microsoft.com&utm_source=microsoft.com&utm_medium=doc&utm_campaign=visualstudio).

## <a name="create-a-new-project"></a>Создание нового проекта 

1. В Visual Studio последовательно выберите **Файл > Создать проект**.

1. В разделе **Visual C#** или **Visual Basic**, выберите **Web**, а затем в средней области выберите **веб-приложения ASP.NET (.NET Framework)**(только C#) или **веб-приложения ASP.NET Core**, а затем нажмите кнопку **ОК**.

1. Выберите **MVC**, убедитесь, что **без проверки подлинности** выбран и нажмите кнопку **ОК**.

1. Введите имя, например **MyWebApp** и нажмите кнопку **ОК**.

    Visual Studio создаст проект.

1. Выберите **сборки > построить решение** для сборки проекта.

## <a name="publish-to-azure-app-service"></a>Публикация в службу приложений Azure

1. В обозревателе решений щелкните проект правой кнопкой мыши и выберите пункт **Опубликовать**.

    ![Выберите опубликовать](../deployment/media/quickstart-publish-aspnet.png "выберите публикации")

1. В **публикации** области, выберите **службу приложений Microsoft Azure**.

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

- [Развертывание приложения ASP.NET Core в Azure](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs)
- [Непрерывное развертывание ASP.NET Core в Azure с помощью Git](/aspnet/core/publishing/azure-continuous-deployment)
