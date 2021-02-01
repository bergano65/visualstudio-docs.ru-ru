---
title: Пространство имен diagnostic | Документы Майкрософт
description: Пространство имен diagnostic используется для выпуска маркеров визуализатора параллелизма. Пространство имен diagnostic является членом пространства имен Concurrency.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cvmarkersobj/Concurrency, diagnostic
helpviewer_keywords:
- Concurrency, diagnostic namespace
ms.assetid: ad786b19-7c4c-46ee-bfb6-c4752b373a09
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 20b25e2974f4b0e4a6bbf6cf02c411fde3f3de1a
ms.sourcegitcommit: d13f7050c873b6284911d1f4acf07cfd29360183
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/22/2021
ms.locfileid: "98686549"
---
# <a name="diagnostic-namespace"></a>Пространство имен diagnostic
Пространство имен `diagnostics` предоставляет функциональные возможности для выпуска маркеров визуализатора параллелизма.

## <a name="syntax"></a>Синтаксис

```cpp
namespace diagnostic;
```

## <a name="members"></a>Члены

### <a name="classes"></a>Классы

|name|Описание|
|----------|-----------------|
|[Класс marker_series](../profiling/marker-series-class.md)|Представляет последовательный канал событий, созданных одним поставщиком.|
|[Класс span](../profiling/span-class.md)|Определяет этапы приложения.|

### <a name="enumerations"></a>Перечисления

|Имя|Описание|
|----------|-----------------|
|[Перечисление marker_importance](../profiling/marker-importance-enumeration.md)|Представляет уровень важности маркера визуализатора параллелизма.|

## <a name="requirements"></a>Требования
 **Заголовок:** *cvmarkersobj.h*

 **Пространство имен** : Concurrency

## <a name="see-also"></a>См. также
- [Пространство имен Concurrency (визуализатор параллелизма)](../profiling/concurrency-namespace-concurrency-visualizer.md)