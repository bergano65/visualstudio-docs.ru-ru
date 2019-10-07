---
title: Поддержка launchSettings.json
description: В этом документе описывается поддержка файла launchSettings.json в Visual Studio для Mac
author: sayedihashimi
ms.author: sayedha
ms.date: 09/18/2019
ms.assetid: a556f9d7-86a8-408e-aa54-392584845889
ms.openlocfilehash: 7135dd05c687e3caed3ee64618ff71c093f4cd63
ms.sourcegitcommit: 4d2620bee4688fb881e09a07ea4a264b99f0743e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71322585"
---
# <a name="launchsettingsjson"></a>launchSettings.json

При разработке проектов ASP.NET Core можно настроить запуск проекта для целей разработки, изменив содержимое файла launchSettings.json. В Visual Studio для Mac это можно сделать в окне "Параметры проекта" или путем непосредственного редактирования файла. Это тот же файл конфигурации, который можно использовать в Visual Studio для Windows или в командной строке с помощью команды `dotnet`. Он хранится в проекте в папке "Свойства".

Подробные сведения см. в статье [Использование нескольких сред в ASP.NET Core](https://docs.microsoft.com/aspnet/core/fundamentals/environments). В этой статье мы расскажем, как изменить этот файл в Visual Studio для Mac.

## <a name="update-the-start-configuration-by-using-visual-studio-for-mac"></a>Обновление конфигурации запуска в Visual Studio для Mac

Файл launchSettings.json можно изменить непосредственно в Visual Studio для Mac или в параметрах проекта. Чтобы перейти к параметрам проекта, щелкните проект правой кнопкой мыши и выберите пункт **Параметры**.

![Контекстное меню проекта с выбранным параметром "Параметры"](media/vsmac-ctx-proj-options.png)

Выберите **Запустить** > **Конфигурации** > **По умолчанию**.

![Пункты "Запустить", "Конфигурации" и "По умолчанию "в параметрах проекта](media/vsmac-run-config-default.png)

В первую очередь необходимо настроить две вещи:

 - Переменные среды
 - URL-адрес приложения для проекта.

## <a name="configure-environment-variables"></a>Настройка переменных среды

Присвоить значения переменным среды можно в сетке. Эти переменные среды будут задаваться при запуске приложения в Visual Studio для Mac. При разработке приложений ASP.NET Core следует помнить об особой переменной среды `ASPNETCORE_ENVIRONMENT`. Дополнительные сведения см. в статье [Использование нескольких сред в ASP.NET Core](https://docs.microsoft.com/aspnet/core/fundamentals/environments).


## <a name="configure-the-start-url"></a>Настройка начального URL-адреса

Чтобы настроить URL-адрес, с которого будет запускаться приложение, перейдите на вкладку **ASP.NET Core**.

![URL-адрес приложения в параметрах проекта](media/vsmac-run-config-default-aspnetcore.png)

Здесь можно указать URL-адрес, по которому приложение будет ожидать передачи данных при запуске.