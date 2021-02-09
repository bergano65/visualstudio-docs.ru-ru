---
title: 'IDebugDocumentContext2:: Compare | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentContext2::Compare
helpviewer_keywords:
- IDebugDocumentContext2::Compare
ms.assetid: 2327b1ba-52d0-42fb-a01e-63cb4b332d2f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 959d909d0c777110905aff3b11c8c29d27d628dd
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99880766"
---
# <a name="idebugdocumentcontext2compare"></a>IDebugDocumentContext2::Compare
Сравнивает данный контекст документа с заданным массивом контекстов документа.

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
окне Значение из перечисления [DOCCONTEXT_COMPARE](../../../extensibility/debugger/reference/doccontext-compare.md) , указывающее тип сравнения.

`rgpDocContextSet`\
окне Массив объектов [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) , которые представляют контексты документа, сравниваемые с.

`dwDocContextSetLen`\
окне Длина массива контекстов документа для сравнения.

`pdwDocContext`\
заполняет Возвращает индекс в `rgpDocContextSet` массив первого контекста документа, удовлетворяющего условию сравнения.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK` , если найдено совпадение. Возвращает значение `S_FALSE` , если совпадение не найдено. В противном случае возвращается код ошибки.

## <a name="remarks"></a>Remarks
 Объекты [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) , переданные в массиве, должны быть реализованы с помощью того же модуля отладки, который реализует `IDebugDocumentContext2` вызываемый объект; в противном случае сравнение недопустимо.

## <a name="see-also"></a>См. также раздел
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
- [DOCCONTEXT_COMPARE](../../../extensibility/debugger/reference/doccontext-compare.md)
