---
title: Класс marker_series | Документы Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- cvmarkersobj/Concurrency::diagnostic::marker_series
helpviewer_keywords:
- Concurrency::diagnostic::marker_series class
ms.assetid: b8445ed0-c512-4f92-b6b4-3d05c044f939
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5a5791d338b204417d4d765b22a5050f4065faef
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49203863"
---
# <a name="markerseries-class"></a>Класс marker_series
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Представляет последовательный канал событий, созданных одним поставщиком.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
class marker_series;  
```  
  
## <a name="members"></a>Участники  
  
### <a name="public-constructors"></a>Открытые конструкторы  
  
|Имя|Описание|  
|----------|-----------------|  
|[Конструктор marker_series::marker_series](../profiling/marker-series-marker-series-constructor.md)|Инициализирует новый экземпляр класса `marker_series`.|  
|[Деструктор marker_series::~marker_series](../profiling/marker-series-tilde-marker-series-destructor.md)|Удаляет объект marker_series и освобождает все выделенные ресурсы.|  
  
### <a name="public-methods"></a>Открытые методы  
  
|Имя|Описание|  
|----------|-----------------|  
|[Метод marker_series::is_enabled](../profiling/marker-series-is-enabled-method.md)|Определяет, разрешен ли поставщик данным сеансом.|  
|[Метод marker_series::write_alert](../profiling/marker-series-write-alert-method.md)|Записывает оповещение в файл трассировки визуализатора параллелизма.|  
|[Метод marker_series::write_flag](../profiling/marker-series-write-flag-method.md)|Записывает флаг в файл трассировки визуализатора параллелизма.|  
|[Метод marker_series::write_message](../profiling/marker-series-write-message-method.md)|Записывает сообщение в файл трассировки визуализатора параллелизма.|  
  
## <a name="inheritance-hierarchy"></a>Иерархия наследования  
 `marker_series`  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** cvmarkersobj.h  
  
 **Пространство имен:** Concurrency::diagnostic  
  
## <a name="see-also"></a>См. также  
 [Пространство имен diagnostic](../profiling/diagnostic-namespace.md)



