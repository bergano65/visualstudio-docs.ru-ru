---
title: Как выполнить Сбор данных счетчиков производительности Windows | Документация Майкрософт
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
ms.openlocfilehash: 2c3e4a9cffd81561af39cef5eb88f4a7745b2dad
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "54753420"
---
# <a name="how-to-collect-windows-counter-data"></a>Как выполнить Сбор данных счетчиков производительности Windows
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Счетчики Windows являются счетчиками производительности системы. Сбор данных с них можно выполнять через заданные интервалы во время профилирования. В представлении "Метки" отчета средств профилирования строка имеет метку **AutoMark** для каждого интервала сбора данных. Строка содержит столбцы, которые описывают значения счетчиков производительности в этом интервале. Чтобы ограничить период анализа интервалом между двумя определенными метками, выберите метки, щелкните их правой кнопкой мыши и выберите в контекстном меню команду **Фильтрация по** ->  **Метки**.  
  
 **Требования**  
  
-   [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
> [!NOTE]
>  Возможности расширенной безопасности в Windows 8 и Windows Server 2012 требовали значительных изменений в способе, которым профилировщик Visual Studio собирает данные на этих платформах. Приложениям для магазина Windows также требуются новые методы сбора. См. раздел [Средства производительности в приложениях Windows 8 и Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
### <a name="to-collect-windows-counter-data"></a>Сбор данных счетчиков производительности Windows  
  
1.  В обозревателе производительности щелкните правой кнопкой мыши сеанс, для которого требуется настроить счетчики Windows, и выберите **Свойства**.  
  
2.  В окне **Страницы свойств** щелкните страницу **Счетчики Windows**.  
  
3.  Установите флажок **Сбор счетчиков Windows**.  
  
4.  В текстовом поле **Интервал сбора (мс)** введите интервал времени.  
  
5.  Выберите категорию в раскрывающемся списке **Категория счетчика**.  
  
6.  Выберите экземпляр в раскрывающемся списке **Экземпляр**.  
  
7.  Выберите счетчики, которые будут использоваться при профилировании приложения.  
  
8.  Нажмите кнопку **Применить**.  
  
## <a name="see-also"></a>См. также раздел  
 [Настройка сеансов анализа производительности](../profiling/configuring-performance-sessions.md)   
 [Свойства сеанса анализа производительности](../profiling/performance-session-properties.md)   
 [Счетчики ЦП и Windows](../profiling/cpu-and-windows-counters.md)
