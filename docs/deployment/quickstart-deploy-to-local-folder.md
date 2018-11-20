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
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2018
ms.locfileid: "38781917"
---
# <a name="deploy-an-app-to-a-local-folder-using-visual-studio"></a>Развертывание приложения в локальную папку с помощью Visual Studio

Вы можете использовать средство **публикации** для публикации приложений ASP.NET, ASP.NET Core, .NET Core и Python в локальную папку из Visual Studio. Для Node.js эти действия поддерживаются, однако отличается пользовательский интерфейс.

[!INCLUDE [quickstart-prereqs](includes/quickstart-prereqs.md)]

## <a name="deploy-to-a-local-folder"></a>Развертывание в локальную папку

1. В обозревателе решений щелкните проект правой кнопкой мыши и выберите пункт **Опубликовать** (или воспользуйтесь командой меню **Сборка** > **Опубликовать**).

    ![Команда "Опубликовать" в контекстном меню проекта в обозревателе решений](../deployment/media/quickstart-publish.png "Выбор команды \"Опубликовать\"")

1. Если ранее вы настроили какие-либо профили публикации, появится панель **Опубликовать**. Выберите команду **Создать профиль**.

1. В открывшемся диалоговом окне **Выберите целевой объект публикации** и укажите **Папка**.

    ![Выбор локальной папки в качестве цели публикации](../deployment/media/quickstart-publish-folder.png "Выбор параметра \"Папка\"")

1. Введите путь или выберите **Обзор**, чтобы указать локальную папку.

1. Нажмите **Публиковать**. Visual Studio создает проект и публикует его в указанной папке. Отображается панель **Публикация** со свойствами проекта, содержащая сводку по профилю.

    ![Панель свойств публикации с обзором профиля](../deployment/media/quickstart-publish-folder-summary.png)

1. Чтобы настроить параметры развертывания, выберите **Настройка** в сводке по профилю и откройте вкладку **Параметры**.

    ![Параметры профиля](../deployment/media/quickstart-profile-settings.png "Параметры профиля")

1. Настройте параметры, например следует ли развернуть конфигурацию отладки или выпуска, а затем выберите **Сохранить**.

1. Для повторной публикации выберите **Публиковать**.

Разверните опубликованные файлы любым удобным вам способом. Например, можно упаковать их в *ZIP-файл*, использовать простую команду copy или развернуть их с помощью любого установочного пакета на выбор.

## <a name="next-steps"></a>Следующие шаги

- [Развертывание приложения .NET Core с помощью средства публикации](/dotnet/core/deploying/deploy-with-vs?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- [Упаковка классического приложения для Магазина Майкрософт (мост для классических приложений)](/windows/uwp/porting/desktop-to-uwp-packaging-dot-net?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- (.NET) [Развертывание .NET Framework и приложений](/dotnet/framework/deployment/)
