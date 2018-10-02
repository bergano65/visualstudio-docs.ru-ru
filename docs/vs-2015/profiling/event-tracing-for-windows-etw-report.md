---
title: Отчет о трассировке событий Windows | Документы Майкрософт
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
- Event tracing for Windows profiling report
- ETW profiling report
ms.assetid: 81e88162-b88a-40b6-8b85-a232c8096a47
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 49ea37f6830c7e4fdf8c8d94b0f323c6337329c5
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47572626"
---
# <a name="event-tracing-for-windows-etw-report"></a>Отчет трассировки событий Windows
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [отчет трассировки событий для Windows (ETW)](https://docs.microsoft.com/visualstudio/profiling/event-tracing-for-windows-etw-report).  
  
Отчет о трассировке событий Windows содержит события трассировки событий Windows, зарегистрированные в ходе сеанса производительности для средств профилирования [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Данные трассировки событий Windows собираются в двоичном ETL-файле.  
  
> [!NOTE]
>  Отчеты о трассировке событий Windows невозможно отобразить в интерфейсе [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
-   Сведения о сборе данных трассировки событий Windows с помощью средств профилирования из интерфейса [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] см. в статье [Практическое руководство. Сбор данных трассировки событий Windows](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md).  
  
-   Сведения о сборе данных трассировки событий Windows с помощью программ командной строки [VSPerfCmd](../profiling/vsperfcmd.md) см. в статье [События](../profiling/events-vsperfcmd.md).  
  
-   Отчет о трассировке событий Windows можно создать с помощью команды **VSReport/Summary:ETW**. Дополнительные сведения см. в разделе [VSPerfReport](../profiling/vsperfreport.md).  
  
|Столбец|Описание|  
|------------|-----------------|  
|**Метка времени**|Указывает время, когда произошло событие.|  
|**Идентификатор процесса**|Указывает процесс, создавший событие.|  
|**Идентификатор потока**|Указывает поток, создавший событие.|  
|**Описание**|Указывает поставщик событий.|  
|**Type**|Указывает тип события.|  
|**Свойства**|Свойства события. Каждое событие представляет собой заключенную в скобки пару имя-значение, отделенную точкой с запятой.|



