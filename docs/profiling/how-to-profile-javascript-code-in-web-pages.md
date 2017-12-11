---
title: "Практическое руководство. Профилирование кода JavaScript в веб-страницах | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- JavaScript performance profiling
- Profiling Tools,JavaScript
- web site performance profiling
ms.assetid: 37d02aad-ca4d-4eb0-bf66-ca3ecef31fbe
caps.latest.revision: "27"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8e33605b75dfe80bf755081692bc8a4991def801
ms.sourcegitcommit: 26419ab0cccdc30d279c32d6a841758cfa903806
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/11/2017
---
# <a name="how-to-profile-javascript-code-in-web-pages"></a>Практическое руководство. Профилирование кода JavaScript в веб-страницах
Средства профилирования [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] могут собирать данные о производительности для кода JavaScript, который выполняется в веб-приложении [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], на произвольной веб-странице или в приложении JavaScript путем использования метода профилирования инструментирования.  
  
 **Требования**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
-   Internet Explorer 8 или более поздней версии.  
  
> [!WARNING]
>  Сведения о профилировании JavaScript в приложениях универсальной платформы Windows см. в разделе [Память JavaScript](../profiling/javascript-memory.md). 
  
 Вы можете использовать мастер профилирования для создания сеанса производительности. Укажите способ инструментирования, а затем выберите вариант профилирования JavaScript на странице "Инструментирование" диалогового окна свойств для сеанса производительности.  
  
 При указании профилирования JavaScript профилируется как код JavaScript, который выполняется в браузере, так и код [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] , который выполняется на сервере.  
  
-   Для веб-приложения [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] профилируется как код JavaScript, который выполняется в браузере, так и код [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] , который выполняется на сервере.  
  
-   На произвольной веб-странице профилируется код JavaScript, который выполняется в браузере.  
  
### <a name="to-profile-javascript-in-an-aspnet-web-application-project"></a>Профилирование JavaScript в проекте веб-приложения ASP.NET  
  
1.  В [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)]откройте веб-проект [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] .  
  
2.  В меню **Анализ** выберите команду **Запустить мастер производительности**.  
  
3.  На первой странице мастера производительности укажите способ профилирования **Инструментирование** и нажмите кнопку **Далее**.  
  
4.  На второй странице мастера убедитесь, что в списке целевых объектов выбран текущий проект, затем нажмите кнопку **Далее**.  
  
5.  На третьей странице мастера установите флажок **Профилировать JavaScript** и нажмите кнопку **Далее**.  
  
6.  На четвертой странице мастера нажмите кнопку **Готово** , чтобы запустить веб-приложение в браузере.  
  
7.  Воспользуйтесь функциями, которые вы хотите профилировать.  
  
8.  Чтобы завершить сеанс профилирования, закройте браузер.  
  
### <a name="to-profile-javascript-in-individual-web-pages-or-a-javascript-applications"></a>Профилирование JavaScript на отдельных веб-страницах или в приложениях JavaScript  
  
1.  Откройте [!INCLUDE[vsPreShort](../code-quality/includes/vspreshort_md.md)].  
  
2.  В меню **Анализ** выберите команду **Запустить мастер производительности**.  
  
3.  На первой странице мастера производительности укажите способ профилирования **Инструментирование** и нажмите кнопку **Далее**.  
  
4.  На второй странице мастера выберите приложение ASP.NET или JavaScript, а затем нажмите кнопку **Далее.**  
  
5.  На третьей странице мастера:  
  
    1.  введите URL-адрес страницы в поле **URL-адрес или путь запуска приложения** ;  
  
    2.  установите флажок **Профилировать JavaScript** и нажмите кнопку **Далее**.  
  
6.  На четвертой странице мастера нажмите кнопку **Готово** , чтобы открыть веб-страницу в браузере.  
  
7.  Воспользуйтесь функциями, которые вы хотите профилировать.  
  
8.  Чтобы завершить сеанс профилирования, закройте браузер.