---
title: IDebugDocumentPositionOffset2::GetRange | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentPositionOffset2::GetRange
ms.assetid: 27da7130-0932-4f97-abde-05e6fb018606
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c86b97fd2437f19e280d9cf9e81454cceee9e47f
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/24/2019
ms.locfileid: "66199180"
---
# <a name="idebugdocumentpositionoffset2getrange"></a>IDebugDocumentPositionOffset2::GetRange
Извлекает диапазон для текущей позиции документа.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetRange(
   DWORD* pdwBegOffset,
   DWORD* pdwEndOffset
);
```

```csharp
public int GetRange(
   ref uint pdwBegOffset,
   ref uint pdwEndOffset
);
```

## <a name="parameters"></a>Параметры
`pdwBegOffset`\
[in, out] Смещение для начальное положение диапазона. Установите этот параметр в значение null, если эта информация не требуется.

`pdwEndOffset`\
[in, out] Смещение для конечное положение диапазона. Установите этот параметр в значение null, если эта информация не требуется.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Диапазон, указанный в документе должности точку останова используется модуль отладки (DE) для поиска вперед инструкцию, которая фактически участвует код. Рассмотрим следующий пример кода:

```
Line 5: // comment
Line 6: x = 1;
```

 Строка 5 вносит нет кода для отлаживаемой программы. Отладчик, который задает точку останова в строке 5 DE поиска в прямом направлении отведенного для первой строки, содержащей код, отладчик будет указать диапазон, включающий дополнительный кандидат строки, где точки останова может быть правильно расположены. DE будет затем поиска в прямом направлении через эти строки до ее найти строку, которая могла бы принять точку останова.

## <a name="see-also"></a>См. также
- [IDebugDocumentPositionOffset2](../../../extensibility/debugger/reference/idebugdocumentpositionoffset2.md)
- [GetRange](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md)