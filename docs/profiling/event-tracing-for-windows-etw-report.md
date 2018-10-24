---
title: Отчет о трассировке событий Windows | Документы Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Event tracing for Windows profiling report
- ETW profiling report
ms.assetid: 81e88162-b88a-40b6-8b85-a232c8096a47
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d8e75d9cbcb67ab9f97b83bf388cc5b6fec58ba3
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49823116"
---
# <a name="event-tracing-for-windows-etw-report"></a>Отчет трассировки событий Windows
Отчет о трассировке событий Windows содержит события трассировки событий Windows, зарегистрированные в ходе сеанса производительности для средств профилирования [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Данные трассировки событий Windows собираются в двоичном *ETL*-файле.  
  
> [!NOTE]
>  Отчеты о трассировке событий Windows невозможно отобразить в интерфейсе [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
- Сведения о сборе данных трассировки событий Windows с помощью средств профилирования из интерфейса [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] см. в статье [Практическое руководство. Сбор данных трассировки событий Windows](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md).  
  
- Сведения о сборе данных трассировки событий Windows с помощью программ командной строки [VSPerfCmd](../profiling/vsperfcmd.md) см. в статье [События](../profiling/events-vsperfcmd.md).  
  
- Отчет о трассировке событий Windows можно создать с помощью команды **VSReport/Summary:ETW**. Дополнительные сведения см. в разделе [VSPerfReport](../profiling/vsperfreport.md).  
  
|Столбец|Описание:|  
|------------|-----------------|  
|**Метка времени**|Указывает время, когда произошло событие.|  
|**Идентификатор процесса**|Указывает процесс, создавший событие.|  
|**Идентификатор потока**|Указывает поток, создавший событие.|  
|**Описание**|Указывает поставщик событий.|  
|**Type**|Указывает тип события.|  
|**Свойства**|Свойства события. Каждое событие представляет собой заключенную в скобки пару имя-значение, отделенную точкой с запятой.|