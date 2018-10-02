---
title: Практическое руководство. Создание отчета о трассировке вызовов для средств профилирования | Документы Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- performance tools, viewing ETW data
- ETW [Visual Studio ALM], viewing data
ms.assetid: 7640520a-7d3c-456c-b184-872a5d2f82f3
caps.latest.revision: 24
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b643e0bf356e7ffb3bf6030ff46cf38ad4a1d98a
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47572691"
---
# <a name="how-to-create-a-profiling-tools-call-trace-report"></a>Практическое руководство. Создание отчета трассировки вызовов для средств профилирования
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [как: Создание отчета профилирования трассировки вызова средств](https://docs.microsoft.com/visualstudio/profiling/how-to-create-a-profiling-tools-call-trace-report).  
  
*Отчет о трассировке вызовов* для средств профилирования [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] содержит сведения о времени для каждой точки входа и выхода в функциях приложения, а также для каждого вызова других функций вашей функцией. Отчеты о трассировке вызовов доступны для данных профилирования, только если они были собраны с помощью метода инструментирования.  
  
> [!NOTE]
>  Отчеты о трассировке вызовов невозможно отобразить в [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Для создания файла значений с разделителями запятыми (CSV) или XML-файла следует использовать программу командной строки **VSPerfReport**. Дополнительные сведения об этой программе см. в разделе [VSPerfReport](../profiling/vsperfreport.md).  
  
### <a name="to-create-a-call-trace-report"></a>Создание отчета от трассировке вызовов  
  
1.  Откройте окно **командной строки**.  
  
2.  В командной строке введите следующую команду:  
  
     *ToolsPath* **VSPerfReport** *VSPFile*  **/CallTrace [/Xml]**  
  
    |||  
    |-|-|  
    |*ToolsPath*|Путь к программам командной строки средств профилирования. Дополнительные сведения см. в статье [Указание пути к средствам командной строки](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).|  
    |*VSPFile*|Файл данных профилирования (VSP или VSPS). Допускаются полные или частичные пути.|  
    |Xml|Создает отчет в формате XML.|  
  
## <a name="see-also"></a>См. также  
 [Практическое руководство. Сбор данных трассировки событий Windows](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)   
 [Интерфейсы API средств профилирования](../profiling/profiling-tools-apis.md)



