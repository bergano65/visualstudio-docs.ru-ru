---
title: Развертывание в локальную папку
ms.custom: ''
ms.date: 06/22/2018
ms.technology: vs-ide-deployment
ms.topic: quickstart
helpviewer_keywords:
- deployment, local folder
ms.assetid: adb461c4-812a-4b8c-b2ab-96002379f6a9
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 517698aa2e042d74138579dae3633930b338cd61
ms.sourcegitcommit: c57ae28181ffe14a30731736661bf59c3eff1211
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2018
ms.locfileid: "38781917"
---
# <a name="deploy-an-app-to-a-local-folder-using-visual-studio"></a>Развертывание приложения в локальную папку, с помощью Visual Studio

Можно использовать **публикации** средство для публикации приложений ASP.NET, ASP.NET Core, .NET Core и Python в локальную папку из Visual Studio. Для Node.js действия поддерживаются, но имеют разные пользовательские интерфейсы.

[!INCLUDE [quickstart-prereqs](includes/quickstart-prereqs.md)]

## <a name="deploy-to-a-local-folder"></a>Развертывание в локальную папку

1. В обозревателе решений щелкните правой кнопкой мыши проект и выберите **публикации** (или используйте **построения** > **публикации** пункт меню).

    ![Команда публикации в контекстном меню проекта в обозревателе решений](../deployment/media/quickstart-publish.png "выберите публикации")

1. Если ранее вы настроили все профили публикации **публикации** откроется панель. Выберите **создать новый профиль**.

1. В **выберите целевой объект публикации** диалоговом окне выберите **папку**.

    ![Выберите локальную папку как целевые публикации](../deployment/media/quickstart-publish-folder.png "выбрать папку")

1. Введите путь или выберите **Обзор** в локальную папку.

1. Нажмите **Публиковать**. Visual Studio выполняет сборку проекта и публикует его в указанную папку. Свойства проекта **публикации** откроется панель, со сводкой профиля.

    ![Панель свойств со сводкой профиля публикации](../deployment/media/quickstart-publish-folder-summary.png)

1. Чтобы настроить параметры развертывания, выберите **Настройка** в профиле сводные данные и выберите **параметры** вкладки.

    ![Параметры профилей](../deployment/media/quickstart-profile-settings.png "параметров профиля")

1. Настройте параметры, например следует ли развернуть конфигурацию отладки или выпуска, а затем выберите **Сохранить**.

1. Чтобы повторно опубликовать, выберите **публикации**.

Разверните опубликованные файлы любым удобным вам способом. Например, вы можете упаковать их в *ZIP-файл* файл, используйте команду простое копирование или развернуть их с помощью любого установочного пакета по своему усмотрению.

## <a name="next-steps"></a>Следующие шаги

- [Развертывание приложения .NET Core с помощью средства публикации](/dotnet/core/deploying/deploy-with-vs?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- [Упаковка классического приложения для Магазина Майкрософт (мост для классических приложений)](/windows/uwp/porting/desktop-to-uwp-packaging-dot-net?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- (.NET) [Развертывания .NET Framework и приложений](/dotnet/framework/deployment/)
