---
title: "Отчет трассировки событий Windows | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "отчет о профилировании трассировки событий Windows"
  - "отчет о профилировании трассировки событий Windows"
ms.assetid: 81e88162-b88a-40b6-8b85-a232c8096a47
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Отчет трассировки событий Windows
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

В отчете трассировки событий Windows перечисляются события, зарегистрированные в ходе сеанса анализа производительности средств профилирования [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Данные трассировка событий Windows записываются в двоичный файл \(ETL\).  
  
> [!NOTE]
>  Отображение отчетов трассировки событий Windows с помощью интерфейса [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] невозможно.  
  
-   Дополнительные сведения о сборе отчетов трассировки событий Windows с помощью средств профилирования из интерфейса [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] см. в разделе [Практическое руководство. Сбор данных трассировки событий Windows](../Topic/How%20to:%20Collect%20Event%20Tracing%20for%20Windows%20\(ETW\)%20Data.md).  
  
-   Дополнительные сведения о сборе данных трассировки событий Windows с помощью программы командной строки [VSPerfCmd](../profiling/vsperfcmd.md) см. в разделе [События](../profiling/events-vsperfcmd.md).  
  
-   Отчет трассировки событий Windows создается с помощью команды **VSReport \/Summary:ETW**.  Для получения дополнительной информации см. [VSPerfReport](../profiling/vsperfreport.md).  
  
|Столбец|Описание|  
|-------------|--------------|  
|**Отметка времени**|Определяет, когда произошло событие.|  
|**Идентификатор процесса**|Позволяет идентифицировать процесс, создавший событие.|  
|**Идентификатор потока**|Позволяет идентифицировать поток, создавший событие.|  
|**Описание**|Позволяет идентифицировать поставщик события.|  
|**Тип**|Позволяет идентифицировать тип события.|  
|**Свойства**|Свойства события.  Каждое событие представляет собой сочетание имени и значения, разделенные запятой и заключенные в скобки.|