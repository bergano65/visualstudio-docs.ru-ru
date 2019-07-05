---
title: Практическое руководство. Создание отчета о трассировке вызовов для средств профилирования | Документация Майкрософт
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
ms.openlocfilehash: 03c039d0059e3e5768681ece9bb547b0f4eb7783
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63432749"
---
# <a name="how-to-create-a-profiling-tools-call-trace-report"></a>Практическое руководство. Создание отчета трассировки вызовов профилирования средств
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

*Отчет о трассировке вызовов* для средств профилирования [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] содержит сведения о времени для каждой точки входа и выхода в функциях приложения, а также для каждого вызова других функций вашей функцией. Отчеты о трассировке вызовов доступны для данных профилирования, только если они были собраны с помощью метода инструментирования.  
  
> [!NOTE]
> Отчеты о трассировке вызовов невозможно отобразить в [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Для создания файла значений с разделителями запятыми (CSV) или XML-файла следует использовать программу командной строки **VSPerfReport**. Дополнительные сведения об этой программе см. в разделе [VSPerfReport](../profiling/vsperfreport.md).  
  
### <a name="to-create-a-call-trace-report"></a>Создание отчета от трассировке вызовов  
  
1. Откройте окно **командной строки**.  
  
2. В командной строке введите следующую команду:  
  
     *ToolsPath* **VSPerfReport** *VSPFile*  **/CallTrace [/Xml]**  
  
    |||  
    |-|-|  
    |*ToolsPath*|Путь к программам командной строки средств профилирования. Дополнительные сведения см. в статье [Указание пути к средствам командной строки](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).|  
    |*VSPFile*|Файл данных профилирования (VSP или VSPS). Допускаются полные или частичные пути.|  
    |Xml|Создает отчет в формате XML.|  
  
## <a name="see-also"></a>См. также  
 [Практическое руководство. Сбор трассировки событий для Windows (ETW) данных](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)   
 [Интерфейсы API средств профилирования](../profiling/profiling-tools-apis.md)
