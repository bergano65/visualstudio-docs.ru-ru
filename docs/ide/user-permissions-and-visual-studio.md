---
title: "Разрешения пользователей и Visual Studio | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio, user permissions
- user permissions
- administrative privileges
- permissions
ms.assetid: 70485ed7-6342-41bf-8250-7a6826e21b98
caps.latest.revision: 14
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: ca7c86466fa23fb21a932f26dc24e37c71cf29b4
ms.openlocfilehash: 0dc9fed1e5fc5a827e836310175d558b14cd41b4
ms.lasthandoff: 04/05/2017

---
# <a name="user-permissions-and-visual-studio"></a>Разрешения пользователей и Visual Studio
Для обеспечения безопасности следует по возможности запускать Visual Studio от имени обычного пользователя.  

> [!WARNING]
>  Также необходимо компилировать, запускать и отлаживать только те решения Visual Studio, которые получены от надежных людей или из надежных расположений.  

 В интегрированной среде разработки Visual Studio можно выполнять большинство операций от имени обычного пользователя, а права администратора требуются для выполнения следующих задач:  

|Область|Задача|Дополнительные сведения|  
|----------|----------|--------------------------|  
|Установка|Установка Visual Studio.|[Установка Visual Studio](../install/install-visual-studio.md)|  
||Установка, обновление или удаление локального содержимого справки.|[Установка локального содержимого и управление им](../ide/install-and-manage-local-content.md)|  
|Типы приложений|Разработка решений для SharePoint.|[Требования по разработке решений SharePoint](/office-dev/office-dev/requirements-for-developing-sharepoint-solutions)|  
||Получение лицензии разработчика для [!INCLUDE[win8_appstore_long](../debugger/includes/win8_appstore_long_md.md)].|[Получение лицензии разработчика (приложения Магазина Windows)](http://go.microsoft.com/fwlink/?LinkID=241313)|  
|Панель элементов|Добавление классических элементов управления COM на **Панель элементов**.|[Использование панели элементов](../ide/using-the-toolbox.md)|  
|Надстройки|Установка и использование надстроек, которые были созданы с помощью классической COM-модели в интегрированной среде разработки.|[Создание надстроек и мастеров](http://msdn.microsoft.com/Library/c5a47c21-6668-4de3-898d-afa969317e73)|  
|Сборка|Использование выполняющихся после сборки событий, которые регистрируют компонент.|[Сведения об этапах настраиваемой сборки и событиях сборки](/cpp/ide/understanding-custom-build-steps-and-build-events)|  
||Включение этапа регистрации при сборке проектов С++.|[Сведения об этапах настраиваемой сборки и событиях сборки](/cpp/ide/understanding-custom-build-steps-and-build-events)|  
|Отладка|Отладка приложений с повышенными разрешениями.|[Параметры отладчика и подготовка](../debugger/debugger-settings-and-preparation.md)|  
||Отладка приложений, выполняемых под другой учетной записью пользователя, например веб-сайтов ASP.NET.|[Отладка приложений ASP.NET и AJAX](../debugger/debugging-aspnet-and-ajax-applications.md)|  
||Отладка в зоне для приложений XAML-браузера (XBAP).|[Основное приложение WPF (PresentationHost.exe)](http://msdn.microsoft.com/Library/3215bfa1-722c-4ac8-a7c5-bdd02d30afbd)|  
||Использование эмулятора для отладки проектов облачных служб для Microsoft Azure.|[Отладка облачной службы в Visual Studio](http://go.microsoft.com/fwlink/?LinkId=266725)|  
||Настройка межсетевого экрана для удаленной отладки.|[Удаленная отладка](../debugger/remote-debugging.md)|  
|Средства производительности|Профилирование приложения.|[Руководство по профилированию производительности для начинающих](../profiling/beginners-guide-to-performance-profiling.md)|  
|Развертывание|Развертывание веб-приложения в службах IIS на локальном компьютере.|[Развертывание веб-приложения ASP.NET у поставщика услуг размещения с использованием Visual Studio или Visual Web Developer: развертывание в IIS в качестве тестовой среды](http://go.microsoft.com/fwlink/?LinkId=266478)|

## <a name="running-visual-studio-as-an-administrator"></a>Запуск Visual Studio от имени администратора  
 Visual Studio можно запускать с правами администратора при каждом запуске интегрированной среды разработки или изменить ярлык приложения так, чтобы оно всегда запускалось с правами администратора. Дополнительные сведения см. в справке Windows.  

#### <a name="to-run-visual-studio-with-administrative-permissions-on-includewin8debuggerincludeswin8mdmd-includewin81debuggerincludeswin81mdmd-includewinserver8debuggerincludeswinserver8mdmd-or-includewinblueserver2ideincludeswinblueserver2mdmd"></a>Запуск Visual Studio с правами администратора в [!INCLUDE[win8](../debugger/includes/win8_md.md)], [!INCLUDE[win81](../debugger/includes/win81_md.md)], [!INCLUDE[winserver8](../debugger/includes/winserver8_md.md)] и [!INCLUDE[winblue_server_2](../ide/includes/winblue_server_2_md.md)]  

1.  На **начальном экране** введите **Visual Studio**. Вы увидите установленные версии Visual Studio.  

2.  Выберите версию Visual Studio, которую нужно запустить, а затем откройте контекстное меню (оно появится внизу экрана). Выберите **Запуск от имени администратора**.  

     После запуска Visual Studio в заголовке окна после имени продукта будет указано **(Администратор)**.  

#### <a name="to-run-visual-studio-with-administrative-permissions-on-includewin7debuggerincludeswin7mdmd-or-includewinsvr08r2debuggerincludeswinsvr08r2mdmd"></a>Запуск Visual Studio с правами администратора в [!INCLUDE[win7](../debugger/includes/win7_md.md)] и [!INCLUDE[winsvr08_r2](../debugger/includes/winsvr08_r2_md.md)]  

1.  Нажмите кнопку **Пуск** и выберите **Все программы**.  

2.  В папке **Microsoft Visual Studio** *версия* выберите **Visual Studio** *версия*, откройте контекстное меню, а затем выберите пункт **Запуск от имени администратора**.  

     После запуска Visual Studio в заголовке окна после имени продукта будет указано **(Администратор)**.  

## <a name="see-also"></a>См. также  
 [Перенос, миграция и обновление проектов Visual Studio](../porting/port-migrate-and-upgrade-visual-studio-projects.md)   
 [Установка Visual Studio](../install/install-visual-studio.md)

