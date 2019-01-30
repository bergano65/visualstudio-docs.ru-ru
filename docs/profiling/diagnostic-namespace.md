---
title: Пространство имен diagnostic | Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- cvmarkersobj/Concurrency::diagnostic
helpviewer_keywords:
- Concurrency::diagnostic namespace
ms.assetid: ad786b19-7c4c-46ee-bfb6-c4752b373a09
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 68f365210c2ed365a7e9ce75ab3c6fbcd309e01a
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54984058"
---
# <a name="diagnostic-namespace"></a>Пространство имен diagnostic
Пространство имен `diagnostics` предоставляет функциональные возможности для выпуска маркеров визуализатора параллелизма.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
namespace diagnostic;  
```  
  
## <a name="members"></a>Участники  
  
### <a name="classes"></a>Классы  
  
|name|Описание|  
|----------|-----------------|  
|[Класс marker_series](../profiling/marker-series-class.md)|Представляет последовательный канал событий, созданных одним поставщиком.|  
|[Класс span](../profiling/span-class.md)|Определяет этапы приложения.|  
  
### <a name="enumerations"></a>Перечисления  
  
|name|Описание|  
|----------|-----------------|  
|[Перечисление marker_importance](../profiling/marker-importance-enumeration.md)|Представляет уровень важности маркера визуализатора параллелизма.|  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** *cvmarkersobj.h*  
  
 **Пространство имен:** параллелизм  
  
## <a name="see-also"></a>См. также  
 [Пространство имен Concurrency (визуализатор параллелизма)](../profiling/concurrency-namespace-concurrency-visualizer.md)