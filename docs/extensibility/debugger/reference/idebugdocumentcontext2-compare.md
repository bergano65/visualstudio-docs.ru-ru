---
title: IDebugДокументКонтекст2:Сравнение Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentContext2::Compare
helpviewer_keywords:
- IDebugDocumentContext2::Compare
ms.assetid: 2327b1ba-52d0-42fb-a01e-63cb4b332d2f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b0e46f765c8e4c0e12c3bb9447e0713919fae7b8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731891"
---
# <a name="idebugdocumentcontext2compare"></a>IDebugDocumentContext2::Compare
Сравнивает контекст этого документа с данным массивом контекстов документов.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT Compare( 
   DOCCONTEXT_COMPARE       compare,
   IDebugDocumentContext2** rgpDocContextSet,
   DWORD                    dwDocContextSetLen,
   DWORD*                   pdwDocContext
);
```

```csharp
int Compare( 
   enum_ DOCCONTEXT_COMPARE compare,
   IDebugDocumentContext2[] rgpDocContextSet,
   uint                     dwDocContextSetLen,
   out uint                 pdwDocContext
);
```

## <a name="parameters"></a>Параметры
`compare`\
(в) Значение из [DOCCONTEXT_COMPARE](../../../extensibility/debugger/reference/doccontext-compare.md) перечисления, которое определяет тип сравнения.

`rgpDocContextSet`\
(в) Массив объектов [IDebugDocumentContext2,](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) представляющих контексты документов.

`dwDocContextSetLen`\
(в) Длина массива контекстов документов для сравнения.

`pdwDocContext`\
(ваут) Возвращает индекс в `rgpDocContextSet` массив контекста первого документа, удовлетворяя сравнение.

## <a name="return-value"></a>Возвращаемое значение
 Возвращается, `S_OK` если совпадение найдено. Возвращает, `S_FALSE` если не найдено совпадений. В противном случае возвращается код ошибки.

## <a name="remarks"></a>Примечания
 [Объекты IDebugDocumentContext2,](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) которые передаются в массиве, должны быть реализованы тем же движком отладки, который реализует вызов `IDebugDocumentContext2` объекта; в противном случае сравнение неявляется.

## <a name="see-also"></a>См. также
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
- [DOCCONTEXT_COMPARE](../../../extensibility/debugger/reference/doccontext-compare.md)
