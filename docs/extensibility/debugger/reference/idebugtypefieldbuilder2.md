---
title: IDebugTypeFieldBuilder2 Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugTypeFieldBuilder2 interface
ms.assetid: 23911c5b-2bbf-4734-9976-87a0bd6ea36c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ed34284e373a7d96761aabe5a7f179367649bc0f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718302"
---
# <a name="idebugtypefieldbuilder2"></a>IDebugTypeFieldBuilder2
Расширяет **IDebugTypeFieldBuilder,** чтобы иметь возможность создавать типы массивов.

## <a name="syntax"></a>Синтаксис

```
IDebugTypeFieldBuilder2 : IDebugTypeFieldBuilder
```

## <a name="notes-for-callers"></a>Заметки для абонентов
 Этот интерфейс можно получить от поставщика символов.

## <a name="methods"></a>Методы
 В дополнение к методам на интерфейсе [IDebugTypeFieldBuilder,](../../../extensibility/debugger/reference/idebugtypefieldbuilder.md) этот интерфейс реализует следующий метод:

|Метод|Описание|
|------------|-----------------|
|[CreateArrayOfType](../../../extensibility/debugger/reference/idebugtypefieldbuilder2-createarrayoftype.md)|Создает массив указанного типа и размера.|

## <a name="requirements"></a>Требования
 Заголовок: Sh.h

 Название: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll
