---
title: "Практическое руководство. Сбор данных трассировки событий Windows | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.performance.property.events
helpviewer_keywords:
- event trace providers, performance tools
- profiling tools, event trace providers
- performance tools, enabling event trace providers
ms.assetid: aa2261fe-d5f5-49fc-a171-d18842e1dc7d
caps.latest.revision: "26"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 66ad7c937ba6c3845e905abea31f4525198f8389
ms.sourcegitcommit: 26419ab0cccdc30d279c32d6a841758cfa903806
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/11/2017
---
# <a name="how-to-collect-event-tracing-for-windows-etw-data"></a>Практическое руководство. Сбор данных трассировки событий Windows
Трассировка событий Windows (ETW) является эффективным средством трассировки на уровне ядра, которое позволяет профилировщику регистрировать события ядра или приложения. Данные, полученные от поставщика событий, можно просматривать только с помощью параметра /**Summary:ETW** программы командной строки [VSPerfReport](../profiling/vsperfreport.md). Этот отчет можно использовать для определения наличия проблем производительности в приложении.  
  
 **Requirements**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
> [!NOTE]
>  Возможности расширенной безопасности в Windows 8 и Windows Server 2012 требовали значительных изменений в способе, которым профилировщик Visual Studio собирает данные на этих платформах. Для приложений универсальной платформы Windows также требуются новые методы сбора. См. раздел [Средства производительности в приложениях Windows 8 и Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
### <a name="to-enable-event-trace-providers"></a>Включение поставщиков трассировки событий  
  
1.  В **обозревателе производительности**щелкните правой кнопкой мыши сеанс производительности, а затем выберите **Свойства**.  
  
2.  В окне **Страницы свойств** щелкните свойства **События Windows**.  
  
3.  В списке **Выберите поставщик трассировки для сбора данных** выберите поставщики событий для использования при профилировании приложения.  
  
## <a name="see-also"></a>См. также  
 [Настройка сеансов анализа производительности](../profiling/configuring-performance-sessions.md)