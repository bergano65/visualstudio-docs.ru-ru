---
title: Создание отчета о трассировке вызовов для средств профилирования | Документация Майкрософт
description: Сведения о создании отчета о трассировке вызовов для средств производительности, в котором представлены сведения о времени для функций и вызываемых ими функций.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- performance tools, viewing ETW data
- ETW [Visual Studio ALM], viewing data
ms.assetid: 7640520a-7d3c-456c-b184-872a5d2f82f3
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 12d294202c3cea2c19f4f88ca4e7bd1dfd62df67
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99860832"
---
# <a name="how-to-create-a-profiling-tools-call-trace-report"></a>Практическое руководство. Создание отчета трассировки вызовов для средств профилирования
*Отчет о трассировке вызовов* для средств профилирования [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] содержит сведения о времени для каждой точки входа и выхода в функциях приложения, а также для каждого вызова других функций вашей функцией. Отчеты о трассировке вызовов доступны для данных профилирования, только если они были собраны с помощью метода инструментирования.

> [!NOTE]
> Отчеты о трассировке вызовов невозможно отобразить в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Для создания файла значений с разделителями запятыми (*CSV*) или *XML*-файла следует использовать программу командной строки **VSPerfReport**. Дополнительные сведения об этой программе см. в разделе [VSPerfReport](../profiling/vsperfreport.md).

### <a name="to-create-a-call-trace-report"></a>Создание отчета от трассировке вызовов

1. Откройте окно **командной строки**.

2. В командной строке введите следующую команду:

     *ToolsPath* **VSPerfReport** *VSPFile*  **/CallTrace [/Xml]**

    |Элемент|Описание|
    |-|-|
    |*ToolsPath*|Путь к инструментам программы командной строки средств профилирования. Дополнительные сведения см. в статье [Указание пути к программам командной строки средств профилирования](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).|
    |*VSPFile*|Файл данных профилирования (*VSP* или *VSPS*). Допускаются полные или частичные пути.|
    |Xml|Создает отчет в формате XML.|

## <a name="see-also"></a>См. также
- [Практическое руководство. Сбор данных трассировки событий Windows](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)
- [Интерфейсы API средств профилирования](../profiling/profiling-tools-apis.md)
