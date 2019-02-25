---
title: IDebugTypeFieldBuilder | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugTypeFieldBuilder interface
ms.assetid: 2dfed0be-6972-4bec-baec-f0b78df9ef97
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 456fe2656949e0cc862acdb97149b85f037beac8
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56720119"
---
# <a name="idebugtypefieldbuilder"></a>IDebugTypeFieldBuilder
Представляет возможность создавать поле, которое представляет тип.

## <a name="syntax"></a>Синтаксис

```
IDebugTypeFieldBuilder : IUnknown
```

## <a name="notes-for-callers"></a>Заметки о вызывающих объектов
 Этот интерфейс получается от поставщика символов.

## <a name="methods"></a>Методы
 Этот интерфейс реализует следующие методы:

|Метод|Описание:|
|------------|-----------------|
|[CreatePrimitive](../../../extensibility/debugger/reference/idebugtypefieldbuilder-createprimitive.md)|Создает объект, представляющий тип-примитив.|
|[CreatePointerToType](../../../extensibility/debugger/reference/idebugtypefieldbuilder-createpointertotype.md)|Создает указатель к заданному типу.|

## <a name="requirements"></a>Требования
 Заголовок: Sh.h

 Пространство имен: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll