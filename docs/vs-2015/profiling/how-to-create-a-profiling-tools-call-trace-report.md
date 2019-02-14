---
title: Практическое руководство. Создание отчета о трассировке вызовов для средств профилирования | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- performance tools, viewing ETW data
- ETW [Visual Studio ALM], viewing data
ms.assetid: 7640520a-7d3c-456c-b184-872a5d2f82f3
caps.latest.revision: 24
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3669803bd87cbe04117246afad4d5d61866af896
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "54774905"
---
# <a name="how-to-create-a-profiling-tools-call-trace-report"></a>Практическое руководство. Создание отчета трассировки вызовов для средств профилирования
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
  
## <a name="see-also"></a>См. также раздел  
 [Практическое руководство. Сбор данных трассировки событий Windows](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)   
 [Интерфейсы API средств профилирования](../profiling/profiling-tools-apis.md)
