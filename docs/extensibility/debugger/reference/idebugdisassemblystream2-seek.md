---
title: IDebugDisassemblyStream2::Ищите Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDisassemblyStream2::Seek
helpviewer_keywords:
- IDebugDisassemblyStream2::Seek
ms.assetid: afec3008-b1e0-4803-ad24-195dbfb6497e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4954b3b278b3c7a6b798a4ffda3856ab8bb200c1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732083"
---
# <a name="idebugdisassemblystream2seek"></a>IDebugDisassemblyStream2::Seek
Перемещает указатель чтения в потоке разборки определенное количество инструкций относительно заданной позиции.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT Seek( 
   SEEK_START          dwSeekStart,
   IDebugCodeContext2* pCodeContext,
   UINT64              uCodeLocationId,
   INT64               iInstructions
);
```

```csharp
int Seek( 
   enum_SEEK_START    dwSeekStart,
   IDebugCodeContext2 pCodeContext,
   ulong              uCodeLocationId,
   long               iInstructions
);
```

## <a name="parameters"></a>Параметры
`dwSeekStart`\
(в) Значение из [SEEK_START](../../../extensibility/debugger/reference/seek-start.md) перечисления, которое определяет относительное положение для начала процесса поиска.

`pCodeContext`\
(в) Объект [IDebugCodeContext2,](../../../extensibility/debugger/reference/idebugcodecontext2.md) представляющий контекст кода, к которым связана операция поиска. Этот параметр используется `dwSeekStart`  =  `SEEK_START_CODECONTEXT`только в том случае, если; в противном случае этот параметр игнорируется и может быть нулевой стоимостью.

`uCodeLocationId`\
(в) Идентификатор местоположения кода, к которому связана операция поиска. Этот параметр `dwSeekStart`  =  `SEEK_START_CODELOCID`используется, если ; в противном случае этот параметр игнорируется и может быть установлен на 0. Ознакомиться с разделом «Замечания» для метода [GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md) для описания идентификатора местоположения кода.

`iInstructions`\
(в) Количество инструкций для перемещения относительно позиции, `dwSeekStart`указанной в . Это значение может быть отрицательным, чтобы двигаться назад.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK`. Возвращает, `S_FALSE` если позиция поиска была в точке за пределами списка доступных инструкций. В противном случае возвращается код ошибки.

## <a name="remarks"></a>Примечания
 Если цель была в позицию до начала списка, зачитываемые позиции устанавливается в первую инструкцию в списке. Если см. было в положение после окончания списка, позиция чтения устанавливается в последнюю инструкцию в списке.

## <a name="see-also"></a>См. также
- [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)
- [SEEK_START](../../../extensibility/debugger/reference/seek-start.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md)
