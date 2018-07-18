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
ms.openlocfilehash: d781bbfefa59b2e124cf76c11b8fd7c06cc66dda
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/05/2018
ms.locfileid: "34764674"
---
# <a name="diagnostic-namespace"></a>Пространство имен diagnostic
Пространство имен `diagnostics` предоставляет функциональные возможности для выпуска маркеров визуализатора параллелизма.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
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
 **Заголовок:** *cvmarkersobj.h*  
  
 **Пространство имен** : Concurrency  
  
## <a name="see-also"></a>См. также  
 [Пространство имен Concurrency (визуализатор параллелизма)](../profiling/concurrency-namespace-concurrency-visualizer.md)