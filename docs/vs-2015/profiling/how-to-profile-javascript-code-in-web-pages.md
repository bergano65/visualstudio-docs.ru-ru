---
title: Практическое руководство. Профилирование кода JavaScript в веб-страницах | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- JavaScript performance profiling
- Profiling Tools,JavaScript
- web site performance profiling
ms.assetid: 37d02aad-ca4d-4eb0-bf66-ca3ecef31fbe
caps.latest.revision: 32
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5f838974292a16a9aeaea11362848b06f5abe982
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60048519"
---
# <a name="how-to-profile-javascript-code-in-web-pages"></a>Практическое руководство. Профилирование кода JavaScript на веб-страницах
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Средства профилирования[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] могут собирать данные о производительности для кода JavaScript, который выполняется в веб-приложении [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] , на произвольной веб-странице или в приложении JavaScript путем использования метода профилирования инструментирования.  
  
 **Требования**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
- Internet Explorer 8 или более поздней версии.  
  
> [!WARNING]
>  Для профилирования JavaScript в приложениях для Магазина Windows см. один из следующих разделов:  
> 
> - [Время выполнения функций JavaScript](http://msdn.microsoft.com/library/b2bf49fc-aea7-4d9c-8fcf-cff8b8dd0c03) [время выполнения функций JavaScript на удаленном устройстве](http://msdn.microsoft.com/library/d78812b6-a97e-46dc-8d99-e724d1d725d8)  
>   - [Анализ данных о времени выполнения функций JavaScript](http://msdn.microsoft.com/library/b5aea8d8-36df-47ba-a7ca-95406700ca9b)  
>   - 
  
 Вы можете использовать мастер профилирования для создания сеанса производительности. Укажите способ инструментирования, а затем выберите вариант профилирования JavaScript на странице "Инструментирование" диалогового окна свойств для сеанса производительности.  
  
 При указании профилирования JavaScript профилируется как код JavaScript, который выполняется в браузере, так и код [!INCLUDE[vstecasp](../includes/vstecasp-md.md)], который выполняется на сервере.  
  
- Для веб-приложения [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] профилируется как код JavaScript, который выполняется в браузере, так и код [!INCLUDE[vstecasp](../includes/vstecasp-md.md)], который выполняется на сервере.  
  
- На произвольной веб-странице профилируется код JavaScript, который выполняется в браузере.  
  
### <a name="to-profile-javascript-in-an-aspnet-web-application-project"></a>Профилирование JavaScript в проекте веб-приложения ASP.NET  
  
1. В [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)] откройте веб-проект [!INCLUDE[vstecasp](../includes/vstecasp-md.md)].  
  
2. В меню **Анализ** выберите команду **Запустить мастер производительности**.  
  
3. На первой странице мастера производительности укажите способ профилирования **Инструментирование** и нажмите кнопку **Далее**.  
  
4. На второй странице мастера убедитесь, что в списке целевых объектов выбран текущий проект, затем нажмите кнопку **Далее**.  
  
5. На третьей странице мастера установите флажок **Профилировать JavaScript** и нажмите кнопку **Далее**.  
  
6. На четвертой странице мастера нажмите кнопку **Готово** , чтобы запустить веб-приложение в браузере.  
  
7. Воспользуйтесь функциями, которые вы хотите профилировать.  
  
8. Чтобы завершить сеанс профилирования, закройте браузер.  
  
### <a name="to-profile-javascript-in-individual-web-pages-or-a-javascript-applications"></a>Профилирование JavaScript на отдельных веб-страницах или в приложениях JavaScript  
  
1. Откройте [!INCLUDE[vsPreShort](../includes/vspreshort-md.md)].  
  
2. В меню **Анализ** выберите команду **Запустить мастер производительности**.  
  
3. На первой странице мастера производительности укажите способ профилирования **Инструментирование** и нажмите кнопку **Далее**.  
  
4. На второй странице мастера выберите приложение ASP.NET или JavaScript, а затем нажмите кнопку **Далее.**  
  
5. На третьей странице мастера:  
  
    1. введите URL-адрес страницы в поле **URL-адрес или путь запуска приложения** ;  
  
    2. установите флажок **Профилировать JavaScript** и нажмите кнопку **Далее**.  
  
6. На четвертой странице мастера нажмите кнопку **Готово** , чтобы открыть веб-страницу в браузере.  
  
7. Воспользуйтесь функциями, которые вы хотите профилировать.  
  
8. Чтобы завершить сеанс профилирования, закройте браузер.
