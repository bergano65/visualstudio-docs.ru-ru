---
title: Отчет о трассировке событий Windows | Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Event tracing for Windows profiling report
- ETW profiling report
ms.assetid: 81e88162-b88a-40b6-8b85-a232c8096a47
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 19412d184377637c29f34b2fe3ffd033f176b97c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779302"
---
# <a name="event-tracing-for-windows-etw-report"></a>Отчет трассировки событий Windows
Отчет о трассировке событий Windows содержит события трассировки событий Windows, зарегистрированные в ходе сеанса производительности для средств профилирования [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Данные трассировки событий Windows собираются в двоичном *ETL*-файле.

> [!NOTE]
> Отчеты о трассировке событий Windows невозможно отобразить в интерфейсе [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

- Сведения о сборе данных трассировки событий Windows с помощью средств профилирования из интерфейса [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] см. в статье [Практическое руководство. Сбор данных трассировки событий Windows](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md).

- Сведения о сборе данных трассировки событий Windows с помощью программ командной строки [VSPerfCmd](../profiling/vsperfcmd.md) см. в статье [События](../profiling/events-vsperfcmd.md).

- Отчет о трассировке событий Windows можно создать с помощью команды **VSReport/Summary:ETW**. Дополнительные сведения см. в разделе [VSPerfReport](../profiling/vsperfreport.md).

|Столбец|Description|
|------------|-----------------|
|**Timestamp**|Указывает время, когда произошло событие.|
|**Идентификатор процесса**|Указывает процесс, создавший событие.|
|**Идентификатор потока**|Указывает поток, создавший событие.|
|**Описание**|Указывает поставщик событий.|
|**Тип**|Указывает тип события.|
|**Свойства**|Свойства события. Каждое событие представляет собой заключенную в скобки пару имя-значение, отделенную точкой с запятой.|
