---
title: "Проверка и отладка кода SharePoint | Документы Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- unit testing [SharePoint development in Visual Studio]
- IntelliTrace [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, IntelliTrace
- SharePoint development in Visual Studio, unit testing
ms.assetid: b5f3bce2-6a51-41b1-a292-9e384bae420c
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: d3717d3bee3665705ce39307b640e02a931cd75f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="verifying-and-debugging-sharepoint-code"></a>Проверка и отладка кода SharePoint
  С помощью IntelliTrace и модульного тестирования вы сможете гораздо легче отлаживать свои решения SharePoint и проверять, что каждый метод в них работает правильно. Можно использовать эти функции для проектов SharePoint в [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)] так же, как и в проектах других типов.  
  
## <a name="intellitrace"></a>IntelliTrace  
 С помощью IntelliTrace можно не только определять текущее состояние своего решения SharePoint, но также отслеживать прошедшие события и контекст, в котором эти события произошли. В своем решении SharePoint можно переходить назад и вперед к различным моментам во времени, в которых произошли события, и просматривать состояния и значения переменных в каждый момент времени. С помощью динамических переходов можно более быстро и легко отлаживать решения SharePoint без установки нескольких точек останова. Также можно сохранить сеанс отладки в файл журнала IntelliTrace (.iTrace), открыть его позже в Visual Studio Ultimate и выполнить отладку после аварийного завершения. ITRACE-файл содержит подробные сведения о когда и где случились определенные ошибки SharePoint, чтобы легче можно выяснить причину ошибки. Сведения в ITRACE-файле являются подмножеством всего журнала ошибок, который создается унифицированной системой ведения журнала (ULS) в SharePoint. Эти сведения включают события, относящихся к SharePoint, например при открытии или закрытии профиля пользователя и при загрузке свойств в проекте SharePoint, их чтении или изменении. Можно настроить записываемые события IntelliTrace. Дополнительные сведения см. в разделе [использование сохраненных данных IntelliTrace](/visualstudio/debugger/using-saved-intellitrace-data) и [настроить IntelliTrace](http://msdn.microsoft.com/en-us/7657ecab-e07e-4b1b-872d-f05d966be37e).  
  
 При возникновении ошибки в SharePoint, диалоговое окно ошибки указывает идентификатор "идентификатор корреляции" для конкретной ошибки. Можно также получить идентификаторы корреляции из событий, перечисленных в ITRACE-файле. Чтобы отобразить список всех событий, которые выполнялись с заданным Идентификатором корреляции, можно ввести идентификатор в **Analysis** раздел страницы со сводкой IntelliTrace. В этом разделе вы можете выбрать, следует ли показывать только имена произошедших событий или их имена вместе со сведениями о вызовах, к примеру: имя функции, точки выхода и точки входа, параметры и возвращаемые значения.  
  
 Можно получить события Visual Studio в IntelliTrace, нажав **F5** ключа. Для получения событий, относящихся к SharePoint, необходимо собирать данные IntelliTrace в решениях SharePoint с помощью Microsoft Monitoring Agent. Этот инструмент собирает данные IntelliTrace и создает ITRACE-файлы для приложений, которые развертываются вне Visual Studio. Дополнительные сведения см. в разделе [возможности IntelliTrace](/visualstudio/debugger/intellitrace-features) и [использование автономного сборщика IntelliTrace](/visualstudio/debugger/using-the-intellitrace-stand-alone-collector).  
  
## <a name="unit-testing"></a>Модульное тестирование  
 Можно было легко найти ошибки в коде модульное тестирование, записи и запустите тестовый код внутри методов теста. Эти методы содержат пустые переменные и оператор Assert, который можно использовать для проверки логики и функциональности своего проекта, основанного на объектной модели SharePoint. Дополнительные сведения см. в статье [Модульное тестирование кода](/visualstudio/test/unit-test-your-code).  
  
### <a name="support-for-microsoft-fakes-framework"></a>Поддержка Microsoft Fakes Framework  
 Проекты SharePoint поддерживают Microsoft Fakes, платформу изоляции, в которой можно создать тестовые заглушки и оболочки на основе делегатов (в приложениях на основе платформы .NET Framework). С помощью платформы Fakes вы можете создавать, поддерживать и встраивать заглушки в модульные тесты. Эти заглушки и оболочки изолируют модульные тесты от среды. Вы можете создавать заглушки для тестирования кода, который использует интерфейсы или незапечатанные классы с переопределяемыми методами. Можно создавать оболочки для перенаправления жестко заданных вызовов к запечатанным классам со статическими или непереопределяемыми методами альтернативной реализации оболочки. Вы также можете использовать делегаты с заглушками и оболочками для динамической настройки поведения отдельных членов заглушки. Дополнительные сведения см. в разделе [изоляция тестируемым кодом с помощью Microsoft Fakes](/visualstudio/test/isolating-code-under-test-with-microsoft-fakes).  
  
## <a name="related-topics"></a>См. также  
  
|Заголовок|Описание:|  
|-----------|-----------------|  
|[IntelliTrace](/visualstudio/debugger/intellitrace)|Описаны более простые способы отладки решений Visual Studio с помощью IntelliTrace.|  
|[Пошаговое руководство. Отладка приложения SharePoint при помощи IntelliTrace](../sharepoint/walkthrough-debugging-a-sharepoint-application-by-using-intellitrace.md)|Описывает использование IntelliTrace для поиска ошибок кода в проекте SharePoint.|  
|[Модульное тестирование кода](/visualstudio/test/unit-test-your-code)|Описывает способ поиска логических ошибок в коде с помощью модульных тестов.|  
  
## <a name="see-also"></a>См. также  
 [Улучшение качества кода](/visualstudio/test/improve-code-quality)  
  
  