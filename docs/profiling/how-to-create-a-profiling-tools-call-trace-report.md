---
title: "Практическое руководство. Создание отчета трассировки вызовов для средств профилирования | Microsoft Docs"
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
  - "трассировка событий Windows [Visual Studio ALM], просмотр данных"
  - "средства повышения производительности, просмотр ETW-данных"
ms.assetid: 7640520a-7d3c-456c-b184-872a5d2f82f3
caps.latest.revision: 19
caps.handback.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Практическое руководство. Создание отчета трассировки вызовов для средств профилирования
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

В *отчете о трассировке вызовов* для средств профилирования [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] содержатся сведения о времени для каждой точки входа в функций приложения и выхода из них, а также каждого вызова других функций текущей функцией.  Отчеты о трассировке вызовов доступны для данных профилирования, только если они были собраны с помощью метода инструментирования.  
  
> [!NOTE]
>  Отображение отчетов о трассировке вызовов в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] невозможно.  Для создания файла данных с разделителям\-запятыми \(CSV\) или XML\-файла нужно использовать программу командной строки **VSPerfReport**.  Дополнительные сведения об этом инструменте см. в разделе [VSPerfReport](../profiling/vsperfreport.md).  
  
### Создание отчета о трассировке вызовов  
  
1.  Откройте окно **командной строки**.  
  
2.  В командной строке введите следующую команду:  
  
     *ToolsPath* **VSPerfReport** *VSPFile* **\/CallTrace \[\/Xml\]**  
  
    |||  
    |-|-|  
    |*ToolsPath*|Путь к программам командной строки средств профилирования.  Для получения дополнительной информации см. [Указание пути к средствам командной строки](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).|  
    |*VSPFile*|Файл данных профилирования \(VSP или VSPS\).  Можно задавать как полный, так и частичный путь.|  
    |Xml|Создание отчета в формате XML.|  
  
## См. также  
 [Практическое руководство. Сбор данных трассировки событий Windows](../Topic/How%20to:%20Collect%20Event%20Tracing%20for%20Windows%20\(ETW\)%20Data.md)   
 [Интерфейсы API средств профилирования](../profiling/profiling-tools-apis.md)