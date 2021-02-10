---
title: 'IDebugDocumentPosition2:: Range | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentPosition2::GetRange
helpviewer_keywords:
- IDebugDocumentPosition2::GetRange
ms.assetid: 91a06ee7-253a-4215-be22-04bf57305aa8
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bd0a08889507c03ec1a8c5c72a615edfb195e7d6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99946856"
---
# <a name="idebugdocumentposition2getrange"></a>IDebugDocumentPosition2::GetRange
Возвращает диапазон для этой должности документа.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetRange( 
   TEXT_POSITION* pBegPosition,
   TEXT_POSITION* pEndPosition
);
```

```csharp
int GetRange( 
   TEXT_POSITION[] pBegPosition,
   TEXT_POSITION[] pEndPosition
);
```

## <a name="parameters"></a>Параметры
`pBegPosition`\
[вход, выход] Структура [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) , которая заполняется начальной позицией. Присвойте этому аргументу значение null, если эти сведения не требуются.

`pEndPosition`\
[вход, выход] Структура [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) , которая заполняется конечной позицией. Присвойте этому аргументу значение null, если эти сведения не требуются.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Remarks
 Диапазон, указанный в позиции документа для точки останова расположения, используется модулем отладки (DE) для поиска оператора, который фактически участвует в коде. Рассмотрим следующий пример кода:

```
Line 5: // comment
Line 6: x = 1;
```

 Строка 5 не вносит код в отлаживаемую программу. Если в отладчике, устанавливающем точку останова в строке 5, требуется, чтобы DE был в первую очередь выполнять поиск первой строки кода, отладчик укажет диапазон, включающий дополнительные строки-кандидаты, в которых может быть правильно размещена точка останова. После этого команда «DE» будет выполнять поиск вперед по этим строкам, пока не найдет строку, которая может принять точку останова.

## <a name="see-also"></a>См. также раздел
- [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)
- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
