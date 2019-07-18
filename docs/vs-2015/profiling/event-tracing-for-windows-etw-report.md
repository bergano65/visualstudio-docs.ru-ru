---
title: Отчет о трассировке событий Windows | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Event tracing for Windows profiling report
- ETW profiling report
ms.assetid: 81e88162-b88a-40b6-8b85-a232c8096a47
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: bc0e139644a0b3df29109c1543140e57c5378f31
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63444011"
---
# <a name="event-tracing-for-windows-etw-report"></a>Отчет трассировки событий Windows
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Отчет о трассировке событий Windows содержит события трассировки событий Windows, зарегистрированные в ходе сеанса производительности для средств профилирования [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Данные трассировки событий Windows собираются в двоичном ETL-файле.  
  
> [!NOTE]
> Отчеты о трассировке событий Windows невозможно отобразить в интерфейсе [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
- Сведения о сборе данных трассировки событий Windows с помощью средств профилирования из интерфейса [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] см. в статье [Практическое руководство. Сбор трассировки событий Windows (ETW) данных](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md).  
  
- Сведения о сборе данных трассировки событий Windows с помощью программ командной строки [VSPerfCmd](../profiling/vsperfcmd.md) см. в статье [События](../profiling/events-vsperfcmd.md).  
  
- Отчет о трассировке событий Windows можно создать с помощью команды **VSReport/Summary:ETW**. Дополнительные сведения см. в разделе [VSPerfReport](../profiling/vsperfreport.md).  
  
|Столбец|Описание|  
|------------|-----------------|  
|**Метка времени**|Указывает время, когда произошло событие.|  
|**Идентификатор процесса**|Указывает процесс, создавший событие.|  
|**Идентификатор потока**|Указывает поток, создавший событие.|  
|**Описание**|Указывает поставщик событий.|  
|**Type**|Указывает тип события.|  
|**Свойства**|Свойства события. Каждое событие представляет собой заключенную в скобки пару имя-значение, отделенную точкой с запятой.|
