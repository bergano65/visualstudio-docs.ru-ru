---
title: "Развертывание в локальную папку - Visual Studio | Документы Microsoft"
ms.custom: 
ms.date: 11/22/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: quickstart
helpviewer_keywords: deployment, local folder
ms.assetid: adb461c4-812a-4b8c-b2ab-96002379f6a9
caps.latest.revision: "1"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4c8696e7ffb4120bae12538a03b77d62c0d091a7
ms.sourcegitcommit: 64c7682ec3a2cbea684e716803398d4278b591d1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/15/2017
---
# <a name="deploy-a-web-app-or-net-core-app-to-a-local-folder-using-the-visual-studio-publish-tool"></a>Развертывание веб-приложения или приложения .NET Core в локальной папке, используя средство публикации Visual Studio

Можно использовать **публикации** средство для публикации приложения в локальную папку. 

Эти шаги применимы к ASP.NET, ASP.NET Core, .NET Core и Python приложений в Visual Studio. Для Node.js действия поддерживаются, но пользовательский интерфейс отличается.

## <a name="create-a-new-project"></a>Создание нового проекта 

1. В Visual Studio выберите **файл > Новый проект**.

1. В разделе **Visual C#** или **Visual Basic**, выберите **.NET Core**, а затем в средней области выберите **консольного приложения (.NET Core)**.

1. Введите имя, например **MyLocalApp** и нажмите кнопку **ОК**.

    Visual Studio создаст проект.

## <a name="deploy-to-a-local-folder"></a>Развертывание в локальную папку

1. В обозревателе решений щелкните правой кнопкой мыши проект и выберите команду **публикации**.

    ![Выберите опубликовать](../deployment/media/quickstart-publish.png "выберите публикации")

1. В **публикации** области, выберите **папки**.

    ![Выберите папку](../deployment/media/quickstart-publish-folder.png "выберите папку")

1. Введите путь или нажмите кнопку **Обзор** для просмотра в локальную папку.

1. Нажмите кнопку **Опубликовать**.

    Visual Studio создает проект и публикует его в указанную папку.

    Область Публикация сводкой профиля.

1. Чтобы настроить параметры развертывания, щелкните **параметры** в профиле сводки.

    ![Параметры профилей](../deployment/media/quickstart-profile-settings.png "параметры профилей") 

1. Настройте параметры, как развернуть конфигурацию отладки или выпуска, а затем нажмите кнопку **Сохранить**.

1. Для повторной публикации, нажмите кнопку **публикации**.

Разверните опубликованные файлы любым способом. Например можно упаковать их в ZIP-файле, используйте команду простое копирование или развертывать вместе с любой пакет установки, по своему усмотрению.

## <a name="next-steps"></a>Следующие шаги

- [Развертывание приложения .NET Core с помощью средства публикации](https://docs.microsoft.com/en-us/dotnet/core/deploying/deploy-with-vs)
- [Пакет классического приложения для магазина Microsoft (мост рабочий стол)](https://docs.microsoft.com/en-us/windows/uwp/porting/desktop-to-uwp-packaging-dot-net)
- (.NET) [Развертывание .NET Framework и приложений](https://docs.microsoft.com/en-us/dotnet/framework/deployment/)
