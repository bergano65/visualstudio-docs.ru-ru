---
title: Публикация на веб-сайте
description: Узнайте, как использовать средство публикации для публикации приложений ASP.NET, ASP.NET Core, .NET Core и Python на веб-сайте из Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 01/29/2019
ms.topic: quickstart
helpviewer_keywords:
- deployment, website
ms.assetid: fc82b1f1-d342-4b82-9a44-590479f0a895
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: bf4248b9155e780b63faf48983adfca866440b98
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99927422"
---
# <a name="publish-a-web-app-to-a-web-site-using-visual-studio"></a>Публикация веб-приложения на веб-сайте с помощью Visual Studio

Вы можете использовать средство **публикации** для публикации приложений ASP.NET, ASP.NET Core, .NET Core и Python на веб-сайте из Visual Studio. Для Node.js эти действия поддерживаются, однако отличается пользовательский интерфейс.

[!INCLUDE [quickstart-prereqs](includes/quickstart-prereqs.md)]

> [!NOTE]
> Если вам нужно опубликовать классическое приложение Windows в общую сетевую папку, см. раздел [Развертывание классического приложения с помощью ClickOnce](how-to-publish-a-clickonce-application-using-the-publish-wizard.md) (C# или Visual Basic). Для C + +/ CLR см. раздел [Развертывание собственного приложения с помощью ClickOnce](/cpp/windows/clickonce-deployment-for-visual-cpp-applications). Для C/C++ см. раздел [Развертывание собственного приложения с помощью проекта установки](/cpp/windows/walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project).

## <a name="publish-to-a-web-site"></a>Публикация на веб-сайте

1. В обозревателе решений щелкните проект правой кнопкой мыши и выберите пункт **Опубликовать** (или воспользуйтесь командой меню **Сборка** > **Опубликовать**).

    ![Команда Опубликовать в контекстном меню проекта в обозревателе решений](../deployment/media/quickstart-publish.png "Выбор команды Опубликовать")

1. Если ранее вы настроили какие-либо профили публикации, появится панель **Опубликовать**. Нажмите кнопку **Создать**.

1. В окне **Публикация** выберите **Веб-сервер (IIS)** .

    ![Выбор целевого объекта публикации](../deployment/media/quickstart-publish-iis.png "Выберите IIS, FTP или другой вариант.")

1. В качестве метода развертывания выберите **Веб-развертывание**. "Веб-развертывание" упрощает развертывание веб-приложений и веб-сайтов на серверах IIS, и его требуется устанавливать в качестве приложения на сервере. Для его установки используйте [установщик веб-платформы](https://www.microsoft.com/web/downloads/platform.aspx).

    ![Выбор метода развертывания](../deployment/media/quickstart-publish-iis-web-deploy.png "Выберите IIS, FTP или другой вариант.")

1. Настройте необходимые параметры для способа публикации и нажмите кнопку **Готово**. 

    ![Сведения о подключении для веб-развертывания](../deployment/media/quickstart-publish-iis-web-deploy-connection-details.png)

1. Для публикации выберите **Опубликовать** на странице сводки. В окне вывода отображаются ход развертывания и результаты.

   Если вам нужна помощь в устранении неполадок ASP.NET Core IIS, см. статью [Устранение неполадок ASP.NET Core в Службе приложений Azure и в IIS](/aspnet/core/test/troubleshoot-azure-iis).

## <a name="next-steps"></a>Следующие шаги

Из этого краткого руководства вы узнали, как использовать Visual Studio, чтобы создать профиль публикации. Вы также можете настроить профиль публикации путем импорта параметров публикации.

> [!div class="nextstepaction"]
> [Импорт параметров публикации и развертывание в IIS](tutorial-import-publish-settings-iis.md)
