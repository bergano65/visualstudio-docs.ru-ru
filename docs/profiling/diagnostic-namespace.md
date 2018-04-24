---
title: Пространство имен diagnostic | Документы Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- cvmarkersobj/Concurrency::diagnostic
helpviewer_keywords:
- Concurrency::diagnostic namespace
ms.assetid: ad786b19-7c4c-46ee-bfb6-c4752b373a09
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 29164c08b03bd23980aad381a1a832b2857309a6
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/19/2018
---
# <a name="diagnostic-namespace"></a>Пространство имен diagnostic
Пространство имен `diagnostics` предоставляет функциональные возможности для выпуска маркеров визуализатора параллелизма.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
namespace diagnostic;  
```  
  
## <a name="members"></a>Участники  
  
### <a name="classes"></a>Классы  
  
|name|Описание:|  
|----------|-----------------|  
|[Класс marker_series](../profiling/marker-series-class.md)|Представляет последовательный канал событий, созданных одним поставщиком.|  
|[Класс span](../profiling/span-class.md)|Определяет этапы приложения.|  
  
### <a name="enumerations"></a>Перечисления  
  
|name|Описание:|  
|----------|-----------------|  
|[Перечисление marker_importance](../profiling/marker-importance-enumeration.md)|Представляет уровень важности маркера визуализатора параллелизма.|  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** cvmarkersobj.h  
  
 **Пространство имен** : Concurrency  
  
## <a name="see-also"></a>См. также  
 [Пространство имен Concurrency (визуализатор параллелизма)](../profiling/concurrency-namespace-concurrency-visualizer.md)