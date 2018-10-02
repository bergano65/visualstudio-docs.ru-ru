---
title: Практическое руководство. Создание отчета трассировки событий Windows для средств профилирования | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bf5547b3-f6c7-4989-9d47-2fe4f1261444
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 93aea1474bb8e8ac215a6eb8e3c8b695d4901cba
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47571026"
---
# <a name="how-to-create-a-profiling-tools-etw-report"></a>Практическое руководство. Создание отчета трассировки событий Windows для средств профилирования
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [как: Создание отчета трассировки событий Windows средств профилирования](https://docs.microsoft.com/visualstudio/profiling/how-to-create-a-profiling-tools-etw-report).  
  
Отчет трассировки событий для Windows информирует о событиях трассировки событий Windows, которые были сохранены в ходе сеанса анализа производительности для средств профилирования [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Данные трассировки событий Windows собираются в двоичном ETL-файле. Дополнительные сведения об отчете трассировки событий Windows см. в [этой статье](../profiling/event-tracing-for-windows-etw-report.md).  
  
> [!NOTE]
>  Отчеты трассировки событий Windows невозможно отобразить в интерфейсе [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
-   Сведения о сборе данных трассировки событий Windows с помощью интерфейса [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] вы найдете в статье [How to: Collect Event Tracing for Windows (ETW) Data](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md) (Практическое руководство: сбор данных трассировки событий Windows).  
  
-   Сведения о сборе данных трассировки событий Windows из командной строки см. в статьях с описанием [средства VSPerfCmd](../profiling/vsperfcmd.md) и [событий](../profiling/events-vsperfcmd.md).  
  
 Отчет трассировки событий Windows можно создать с помощью команды **VSReport/summary:etw**. ETL-файл с данными трассировки событий Windows должен располагаться в том же каталоге, что и файл данных профилирования (VSP или VSPS). По умолчанию отчет создается как CSV-файл с разделителями запятыми. Дополнительные сведения см. в разделе [VSPerfReport](../profiling/vsperfreport.md).  
  
### <a name="to-generate-an-etw-report"></a>Создание отчета трассировки событий Windows  
  
-   В окне **командной строки** введите следующую команду:  
  
     *ToolsPath* **VSPerfReport** *VSPFile* **/Summary:ETW [/Xml]**  
  
    |||  
    |-|-|  
    |*ToolsPath*|Путь к программе средств профилирования. Дополнительные сведения см. в статье [Указание пути к средствам командной строки](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).|  
    |*VSPFile*|Файл данных профилирования (VSP или VSPS). Допускаются полные или частичные пути.|  
    |Xml|Создает отчет в формате XML.|



