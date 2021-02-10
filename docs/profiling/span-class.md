---
title: Класс span | Документы Майкрософт
description: Сведения о классе span и о том, как он определяет этапы приложения. Также в этой статье описываются открытые конструкторы и иерархия наследования класса span.
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- cvmarkersobj/Concurrency::diagnostic::span
helpviewer_keywords:
- Concurrency::diagnostic::span class
ms.assetid: 527826a8-2590-43ad-b907-7bc0b7288e92
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: fff7f91326cac47100f5b2b1b42e22b9c0fc1d9b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99949965"
---
# <a name="span-class"></a>Класс span
Определяет этапы приложения.

## <a name="syntax"></a>Синтаксис

```cpp
class span;
```

## <a name="members"></a>Члены

### <a name="public-constructors"></a>Открытые конструкторы

|Имя|Описание|
|----------|-----------------|
|[Конструктор span::span](../profiling/span-span-constructor.md)|Инициализирует новый экземпляр класса `span`.|
|[Деструктор span::~span](../profiling/span-tilde-span-destructor.md)|Уничтожает объект `span` и высвобождает его ресурсы.|

## <a name="inheritance-hierarchy"></a>Иерархия наследования
 `span`

## <a name="requirements"></a>Требования
 **Заголовок:** *cvmarkersobj.h*

 **Пространство имен:** Concurrency::diagnostic

## <a name="see-also"></a>См. также
- [Пространство имен diagnostic](../profiling/diagnostic-namespace.md)