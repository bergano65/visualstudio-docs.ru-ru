---
title: Поддержка launchSettings.json
description: В этом документе описывается поддержка файла launchSettings.json в Visual Studio для Mac
author: sayedihashimi
ms.author: sayedha
ms.date: 09/18/2019
ms.assetid: a556f9d7-86a8-408e-aa54-392584845889
ms.openlocfilehash: e7de368dd26bf2724a7bc060dade46422817da1e
ms.sourcegitcommit: ea182703e922c74725045afc251bcebac305068a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2019
ms.locfileid: "71213819"
---
# <a name="launchsettingsjson"></a>launchSettings.json

При разработке проектов ASP.NET Core можно настроить запуск проекта для целей разработки, изменив содержимое файла `launchSettings.json`. В Visual Studio для Mac это можно сделать в окне "Параметры проекта" или путем непосредственного редактирования файла `launchSettings.json`. Это тот же файл конфигурации, который можно использовать в Visual Studio для Windows или в командной строке с помощью команды `dotnet`. Он хранится в проекте в папке `Properties`.

Подробные сведения см. в статье [Использование нескольких сред в ASP.NET Core](https://docs.microsoft.com/aspnet/core/fundamentals/environments). В этом документе мы расскажем, как изменить этот файл в Visual Studio для Mac.

## <a name="updating-start-configuration-using-visual-studio-for-mac"></a>Изменение конфигурации запуска в Visual Studio для Mac

Файл `launchSettings.json` можно изменить непосредственно в Visual Studio для Mac или в параметрах проекта. Чтобы перейти к параметрам проекта, щелкните проект правой кнопкой мыши и выберите пункт "Параметры". См. изображение ниже.

![Выбор пункта "Параметры" в контекстном меню проекта](media/vsmac-ctx-proj-options.png)

Открыв это диалоговое окно, выберите узел "Запуск" > "Конфигурации" > "По умолчанию".

![конфигурации запуска по умолчанию](media/vsmac-run-config-default.png)

Здесь можно настроить два основных аспекта:

 - переменные среды, задаваемые при запуске;
 - начальный URL-адрес проекта.

## <a name="configure-environment-variables"></a>Настройка переменных среды

Присвоить значения переменным среды можно в сетке. Эти переменные среды будут задаваться при запуске приложения в Visual Studio для Mac. При разработке приложений ASP.NET Core следует помнить об особой переменной среды `ASPNETCORE_ENVIRONMENT`. Дополнительные сведения см. в статье [Использование нескольких сред в ASP.NET Core](https://docs.microsoft.com/aspnet/core/fundamentals/environments).


## <a name="configure-start-url"></a>Настройка начального URL-адреса

Чтобы настроить URL-адрес, с которого будет запускаться приложение, перейдите на вкладку "ASP.NET Core".

![начальный URL-адрес в параметрах проекта](media/vsmac-run-config-default-aspnetcore.png)

Здесь можно указать URL-адреса, по которым приложение будет ожидать передачи данных при запуске.