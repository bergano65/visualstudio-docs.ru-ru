---
title: Практическое руководство. Сбор данных счетчиков производительности Windows | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.property.syscounter
- vs.performance.property.wincounter
helpviewer_keywords:
- windows counters
- performance tools, using windows counters
- profiling tools, using windows counters
ms.assetid: db4fbac2-bea5-4558-aa8b-160fcccf4b33
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4fb88d4db82bde5f93d33716b65e2e8a4b48305a
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60115670"
---
# <a name="how-to-collect-windows-counter-data"></a>Практическое руководство. Сбор данных счетчиков производительности Windows
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Счетчики Windows являются счетчиками производительности системы. Сбор данных с них можно выполнять через заданные интервалы во время профилирования. В представлении "Метки" отчета средств профилирования строка имеет метку **AutoMark** для каждого интервала сбора данных. Строка содержит столбцы, которые описывают значения счетчиков производительности в этом интервале. Чтобы ограничить период анализа интервалом между двумя определенными метками, выберите метки, щелкните их правой кнопкой мыши и выберите в контекстном меню команду **Фильтрация по** ->  **Метки**.  
  
 **Требования**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
> [!NOTE]
>  Возможности расширенной безопасности в Windows 8 и Windows Server 2012 требовали значительных изменений в способе, которым профилировщик Visual Studio собирает данные на этих платформах. Приложениям для магазина Windows также требуются новые методы сбора. См. раздел [Средства производительности в приложениях Windows 8 и Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
### <a name="to-collect-windows-counter-data"></a>Сбор данных счетчиков производительности Windows  
  
1. В обозревателе производительности щелкните правой кнопкой мыши сеанс, для которого требуется настроить счетчики Windows, и выберите **Свойства**.  
  
2. В окне **Страницы свойств** щелкните страницу **Счетчики Windows**.  
  
3. Установите флажок **Сбор счетчиков Windows**.  
  
4. В текстовом поле **Интервал сбора (мс)** введите интервал времени.  
  
5. Выберите категорию в раскрывающемся списке **Категория счетчика**.  
  
6. Выберите экземпляр в раскрывающемся списке **Экземпляр**.  
  
7. Выберите счетчики, которые будут использоваться при профилировании приложения.  
  
8. Нажмите кнопку **Применить**.  
  
## <a name="see-also"></a>См. также раздел  
 [Настройка сеансов анализа производительности](../profiling/configuring-performance-sessions.md)   
 [Свойства сеанса анализа производительности](../profiling/performance-session-properties.md)   
 [Счетчики ЦП и Windows](../profiling/cpu-and-windows-counters.md)
