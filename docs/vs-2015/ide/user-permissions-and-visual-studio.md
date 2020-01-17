---
title: Разрешения пользователей | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, user permissions
- user permissions
- administrative privileges
- permissions
ms.assetid: 70485ed7-6342-41bf-8250-7a6826e21b98
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: aa01cb77e8a003438721984da13f46de350104ea
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/13/2020
ms.locfileid: "75918994"
---
# <a name="user-permissions-and-visual-studio"></a>Разрешения пользователей и Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Для обеспечения безопасности следует по возможности запускать Visual Studio от имени обычного пользователя.

> [!WARNING]
> Также необходимо компилировать, запускать и отлаживать только те решения Visual Studio, которые получены от надежных людей или из надежных расположений.

 В интегрированной среде разработки Visual Studio можно выполнять большинство операций от имени обычного пользователя, а права администратора требуются для выполнения следующих задач:

|Область|Задача|Дополнительные сведения|
|----------|----------|--------------------------|
|Установка|Установка Visual Studio.|[Установка Visual Studio 2015](../install/install-visual-studio-2015.md)|
||Обновление с пробного выпуска Visual Studio.|[Практическое руководство. Переход с ознакомительного выпуска Visual Studio](../install/how-to-upgrade-from-a-trial-edition-of-visual-studio.md)|
||Установка, обновление или удаление локального содержимого справки.|[Установка локального содержимого и управление им](../ide/install-and-manage-local-content.md)|
|Типы приложений|Разработка решений для SharePoint 2010.|[Требования по разработке решений SharePoint](https://msdn.microsoft.com/library/ae8ff69d-4540-4380-ab0b-845f7108e89c)|
||Получение лицензии разработчика для [!INCLUDE[win8_appstore_long](../includes/win8-appstore-long-md.md)].|[Получение лицензии разработчика (приложения Магазина Windows)](https://msdn.microsoft.com/library/windows/apps/hh974578.aspx)|
|Панель элементов|Добавление классических элементов управления COM на **Панель элементов**.|[Использование панели элементов](../ide/using-the-toolbox.md)|
|Надстройки|Установка и использование надстроек, которые были созданы с помощью классической COM-модели в интегрированной среде разработки.|[Создание надстроек и мастеров](https://msdn.microsoft.com/library/c5a47c21-6668-4de3-898d-afa969317e73)|
|Сборка|Использование выполняющихся после сборки событий, которые регистрируют компонент.|[Сведения об этапах настраиваемой сборки и событиях сборки](https://msdn.microsoft.com/library/beb2f017-3e9f-4b2c-9b57-2572fd2628e4)|
||Включение этапа регистрации при сборке проектов С++.|[Сведения об этапах настраиваемой сборки и событиях сборки](https://msdn.microsoft.com/library/beb2f017-3e9f-4b2c-9b57-2572fd2628e4)|
|Отладка|Отладка приложений с повышенными разрешениями.|[Параметры отладчика и подготовка](../debugger/debugger-settings-and-preparation.md)|
||Отладка приложений, выполняемых под другой учетной записью пользователя, например веб-сайтов ASP.NET.|[Отладка приложений ASP.NET и AJAX](../debugger/debugging-aspnet-and-ajax-applications.md)|
||Отладка в зоне для приложений XAML-браузера (XBAP).|[Основное приложение WPF (PresentationHost.exe)](https://msdn.microsoft.com/library/3215bfa1-722c-4ac8-a7c5-bdd02d30afbd)|
||Использование эмулятора для отладки проектов облачных служб для Microsoft Azure.|[Отладка облачной службы в Visual Studio](../azure/vs-azure-tools-debug-cloud-services-virtual-machines.md)|
||Настройка межсетевого экрана для удаленной отладки.|[Настройка инструментов удаленной отладки в устройстве](https://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c)|
|Средства производительности|Профилирование приложения.|[Руководство по профилированию производительности для начинающих](../profiling/beginners-guide-to-performance-profiling.md)|
|Развертывание|Развертывание веб-приложения в службах IIS на локальном компьютере.|[Развертывание веб-приложения ASP.NET у поставщика услуг размещения с помощью Visual Studio или Visual Web Developer: развертывание в IIS в качестве тестовой среды](https://www.asp.net/web-forms/tutorials/deployment/deployment-to-a-hosting-provider/Deployment-to-a-Hosting-Provider-Deploying-to-IIS-as-a-Test-Environment-5-of-12)|
|Предоставление обратной связи в корпорацию Майкрософт|Изменение режима участия в программе улучшения качества Visual Studio.|[Практическое руководство. отправка отзыва](../misc/how-to-send-feedback-about-visual-studio.md)|

## <a name="running-visual-studio-as-an-administrator"></a>Запуск Visual Studio от имени администратора
 Visual Studio можно запускать с правами администратора при каждом запуске интегрированной среды разработки или изменить ярлык приложения так, чтобы оно всегда запускалось с правами администратора. Дополнительные сведения см. в справке Windows.

#### <a name="to-run-visual-studio-with-administrative-permissions-on-includewin8includeswin8-mdmd-includewin81includeswin81-mdmd-includewinserver8includeswinserver8-mdmd-or-includewinblue_server_2includeswinblue-server-2-mdmd"></a>Запуск Visual Studio с правами администратора в [!INCLUDE[win8](../includes/win8-md.md)], [!INCLUDE[win81](../includes/win81-md.md)], [!INCLUDE[winserver8](../includes/winserver8-md.md)] и [!INCLUDE[winblue_server_2](../includes/winblue-server-2-md.md)]

1. На **начальном экране** введите **Visual Studio**. Вы увидите установленные версии Visual Studio.

2. Выберите версию Visual Studio, которую нужно запустить, а затем откройте контекстное меню (оно появится внизу экрана). Выберите **Запуск от имени администратора**.

     После запуска Visual Studio в заголовке окна после имени продукта будет указано **(Администратор)** .

#### <a name="to-run-visual-studio-with-administrative-permissions-on-includewin7includeswin7-mdmd-or-includewinsvr08_r2includeswinsvr08-r2-mdmd"></a>Запуск Visual Studio с правами администратора в [!INCLUDE[win7](../includes/win7-md.md)] и [!INCLUDE[winsvr08_r2](../includes/winsvr08-r2-md.md)]

1. Нажмите кнопку **Пуск** и выберите **Все программы**.

2. В папке **Microsoft Visual Studio** *версия* выберите **Visual Studio** *версия*, откройте контекстное меню, а затем выберите пункт **Запуск от имени администратора**.

     После запуска Visual Studio в заголовке окна после имени продукта будет указано **(Администратор)** .

## <a name="see-also"></a>См. также
 [Перенос, миграция и обновление проектов Visual Studio](../porting/porting-migrating-and-upgrading-visual-studio-projects.md) [Статья об установке Visual Studio 2015](../install/install-visual-studio-2015.md)
