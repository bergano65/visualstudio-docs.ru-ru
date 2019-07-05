---
title: IDebugTypeFieldBuilder2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugTypeFieldBuilder2 interface
ms.assetid: 23911c5b-2bbf-4734-9976-87a0bd6ea36c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a22f8d60318721fbb51e0d5be7965c27666b8c48
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66319764"
---
# <a name="idebugtypefieldbuilder2"></a>IDebugTypeFieldBuilder2
Расширяет **IDebugTypeFieldBuilder** чтобы иметь возможность создавать типы массивов.

## <a name="syntax"></a>Синтаксис

```
IDebugTypeFieldBuilder2 : IDebugTypeFieldBuilder
```

## <a name="notes-for-callers"></a>Заметки о вызывающих объектов
 Этот интерфейс можно получить от поставщика символов.

## <a name="methods"></a>Методы
 В дополнение к методам на [IDebugTypeFieldBuilder](../../../extensibility/debugger/reference/idebugtypefieldbuilder.md) интерфейс, этот интерфейс реализует следующий метод:

|Метод|Описание|
|------------|-----------------|
|[CreateArrayOfType](../../../extensibility/debugger/reference/idebugtypefieldbuilder2-createarrayoftype.md)|Создает массив указанного типа и размера.|

## <a name="requirements"></a>Требования
 Заголовок: Sh.h

 Пространство имен: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll