---
title: Практическое руководство. Создание отчета трассировки событий Windows для средств профилирования | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: bf5547b3-f6c7-4989-9d47-2fe4f1261444
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6b172ffbf481ea077d099288b3b79254b89b13a5
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63432746"
---
# <a name="how-to-create-a-profiling-tools-etw-report"></a>Практическое руководство. Создание отчета трассировки событий Windows для средств профилирования
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Отчет трассировки событий для Windows информирует о событиях трассировки событий Windows, которые были сохранены в ходе сеанса анализа производительности для средств профилирования [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Данные трассировки событий Windows собираются в двоичном ETL-файле. Дополнительные сведения об отчете трассировки событий Windows см. в [этой статье](../profiling/event-tracing-for-windows-etw-report.md).  
  
> [!NOTE]
> Отчеты трассировки событий Windows невозможно отобразить в интерфейсе [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
- Сведения о сборе данных трассировки событий Windows с помощью интерфейса [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] см. в статье [Практическое руководство. Сбор трассировки событий Windows (ETW) данных](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md).  
  
- Сведения о сборе данных трассировки событий Windows из командной строки см. в статьях с описанием [средства VSPerfCmd](../profiling/vsperfcmd.md) и [событий](../profiling/events-vsperfcmd.md).  
  
  Отчет трассировки событий Windows можно создать с помощью команды **VSReport/summary:etw**. ETL-файл с данными трассировки событий Windows должен располагаться в том же каталоге, что и файл данных профилирования (VSP или VSPS). По умолчанию отчет создается как CSV-файл с разделителями запятыми. Дополнительные сведения см. в разделе [VSPerfReport](../profiling/vsperfreport.md).  
  
### <a name="to-generate-an-etw-report"></a>Создание отчета трассировки событий Windows  
  
- В окне **командной строки** введите следующую команду:  
  
     *ToolsPath* **VSPerfReport** *VSPFile* **/Summary:ETW [/Xml]**  
  
    |||  
    |-|-|  
    |*ToolsPath*|Путь к программе средств профилирования. Дополнительные сведения см. в статье [Указание пути к средствам командной строки](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).|  
    |*VSPFile*|Файл данных профилирования (VSP или VSPS). Допускаются полные или частичные пути.|  
    |Xml|Создает отчет в формате XML.|
