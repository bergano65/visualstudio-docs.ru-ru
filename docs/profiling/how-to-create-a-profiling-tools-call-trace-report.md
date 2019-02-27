---
title: Как выполнить Создание отчета о трассировке вызовов для средств профилирования | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- performance tools, viewing ETW data
- ETW [Visual Studio ALM], viewing data
ms.assetid: 7640520a-7d3c-456c-b184-872a5d2f82f3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cdfe600192e61e8e7721c0e5486afafbedcaa6eb
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56624221"
---
# <a name="how-to-create-a-profiling-tools-call-trace-report"></a>Как выполнить Создание отчета трассировки вызовов для средств профилирования
*Отчет о трассировке вызовов* для средств профилирования [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] содержит сведения о времени для каждой точки входа и выхода в функциях приложения, а также для каждого вызова других функций вашей функцией. Отчеты о трассировке вызовов доступны для данных профилирования, только если они были собраны с помощью метода инструментирования.

> [!NOTE]
>  Отчеты о трассировке вызовов невозможно отобразить в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Для создания файла значений с разделителями запятыми (*CSV*) или *XML*-файла следует использовать программу командной строки **VSPerfReport**. Дополнительные сведения об этой программе см. в разделе [VSPerfReport](../profiling/vsperfreport.md).

### <a name="to-create-a-call-trace-report"></a>Создание отчета от трассировке вызовов

1.  Откройте окно **командной строки**.

2.  В командной строке введите следующую команду:

     *ToolsPath* **VSPerfReport** *VSPFile*  **/CallTrace [/Xml]**

    |||
    |-|-|
    |*ToolsPath*|Путь к инструментам программы командной строки средств профилирования. Дополнительные сведения см. в статье [Указание пути к программам командной строки средств профилирования](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).|
    |*VSPFile*|Файл данных профилирования (*VSP* или *VSPS*). Допускаются полные или частичные пути.|
    |Xml|Создает отчет в формате XML.|


## <a name="see-also"></a>См. также
- [Практическое руководство. Сбор данных трассировки событий Windows](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)
- [Интерфейсы API средств профилирования](../profiling/profiling-tools-apis.md)
