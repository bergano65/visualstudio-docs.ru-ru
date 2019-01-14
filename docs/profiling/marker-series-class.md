---
title: Класс marker_series | Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- cvmarkersobj/Concurrency::diagnostic::marker_series
helpviewer_keywords:
- Concurrency::diagnostic::marker_series class
ms.assetid: b8445ed0-c512-4f92-b6b4-3d05c044f939
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e8ecc6a14cce80197c1221734aadb4ce7e6758cf
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53869824"
---
# <a name="markerseries-class"></a>Класс marker_series
Представляет последовательный канал событий, созданных одним поставщиком.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
class marker_series;  
```  
  
## <a name="members"></a>Участники  
  
### <a name="public-constructors"></a>Открытые конструкторы  
  
|name|Описание|  
|----------|-----------------|  
|[Конструктор marker_series::marker_series](../profiling/marker-series-marker-series-constructor.md)|Инициализирует новый экземпляр класса `marker_series`.|  
|[Деструктор marker_series::~marker_series](../profiling/marker-series-tilde-marker-series-destructor.md)|Удаляет объект marker_series и освобождает все выделенные ресурсы.|  
  
### <a name="public-methods"></a>Открытые методы  
  
|name|Описание|  
|----------|-----------------|  
|[Метод marker_series::is_enabled](../profiling/marker-series-is-enabled-method.md)|Определяет, разрешен ли поставщик данным сеансом.|  
|[Метод marker_series::write_alert](../profiling/marker-series-write-alert-method.md)|Записывает оповещение в файл трассировки визуализатора параллелизма.|  
|[Метод marker_series::write_flag](../profiling/marker-series-write-flag-method.md)|Записывает флаг в файл трассировки визуализатора параллелизма.|  
|[Метод marker_series::write_message](../profiling/marker-series-write-message-method.md)|Записывает сообщение в файл трассировки визуализатора параллелизма.|  
  
## <a name="inheritance-hierarchy"></a>Иерархия наследования  
 `marker_series`  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** *cvmarkersobj.h*  
  
 **Пространство имен:** Concurrency::diagnostic  
  
## <a name="see-also"></a>См. также  
 [Пространство имен diagnostic](../profiling/diagnostic-namespace.md)