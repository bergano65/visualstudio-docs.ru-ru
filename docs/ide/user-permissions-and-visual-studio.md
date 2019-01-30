---
title: Запуск от имени администратора
ms.date: 06/05/2018
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, user permissions
- user permissions
- administrative privileges
- permissions
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 09fe84a9cd48f85ffac1f98b9300e1bdbad96ade
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "55012200"
---
# <a name="user-permissions-and-visual-studio"></a>Разрешения пользователей и Visual Studio

Для обеспечения безопасности следует по возможности запускать Visual Studio от имени обычного пользователя.

> [!WARNING]
> Также необходимо компилировать, запускать и отлаживать только те решения Visual Studio, которые получены от надежных людей или из надежных расположений.

Под именем обычного пользователя в Visual Studio IDE можно делать практически все. Разрешения администратора необходимы для выполнения следующих задач.

|Область|Задача|Дополнительные сведения|
|----------|----------| - |
|Установка|Установка Visual Studio.|[Установка Visual Studio](../install/install-visual-studio.md)|
||Установка, обновление или удаление содержимого локальной справки.|[Установка содержимого локальной справки и управление им](../help-viewer/install-manage-local-content.md)|
|Панель элементов|Добавление классических элементов управления COM в **панель элементов**.|[Панель элементов](../ide/reference/toolbox.md)|
|Сборка|Использование выполняющихся после сборки событий, которые регистрируют компонент.|[Сведения о настраиваемых этапах сборки и событиях сборки](/cpp/ide/understanding-custom-build-steps-and-build-events)|
||Включение этапа регистрации при сборке проектов С++.||
|Отладка|Отладка приложений с повышенными разрешениями.|[Параметры отладчика и подготовка](../debugger/debugger-settings-and-preparation.md)|
||Отладка приложений, выполняемых под другой учетной записью пользователя, например веб-сайтов ASP.NET.|[Отладка приложений ASP.NET и AJAX](../debugger/how-to-enable-debugging-for-aspnet-applications.md)|
||Отладка в зоне для приложений XAML-браузера (XBAP).|[Основное приложение WPF (PresentationHost.exe)](/dotnet/framework/wpf/app-development/wpf-host-presentationhost-exe)|
||Использование эмулятора для отладки проектов облачных служб для Microsoft Azure.|[Отладка облачной службы в Visual Studio](/azure/vs-azure-tools-debug-cloud-services-virtual-machines)|
||Настройка брандмауэра для удаленной отладки.|[Удаленная отладка](../debugger/remote-debugging.md)|
|Средства производительности|Профилирование приложения.|[Руководство по профилированию производительности для начинающих](../profiling/beginners-guide-to-performance-profiling.md)|
|Развертывание|Развертывание веб-приложения в службах IIS на локальном компьютере.|[Развертывание веб-приложения ASP.NET с помощью Visual Studio](/aspnet/web-forms/overview/older-versions-getting-started/deployment-to-a-hosting-provider/)|

## <a name="run-visual-studio-as-an-administrator"></a>Запуск Visual Studio от имени администратора

Если необходимо запустить Visual Studio от имени администратора, выполните следующие действия, чтобы открыть интегрированную среду разработки.

> [!NOTE]
> Эти инструкции предназначены для Windows 10. Для других версий Windows они аналогичны.

1. Откройте меню **Пуск** и перейдите к Visual Studio 2017.

1. При помощи щелчка правой кнопкой или контекстного меню **Visual Studio 2017** выберите **More (Дополнительно)** > **Запуск от имени администратора**.

   После запуска Visual Studio в заголовке окна после имени продукта будет указано **(Администратор)**.

Можно также изменить ярлык приложения, чтобы всегда запускать его с правами администратора.

## <a name="see-also"></a>См. также

- [Перенос, миграция и обновление проектов Visual Studio](../porting/port-migrate-and-upgrade-visual-studio-projects.md)
- [Установка Visual Studio](../install/install-visual-studio.md)