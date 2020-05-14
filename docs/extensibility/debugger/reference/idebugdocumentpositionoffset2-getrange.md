---
title: IDebugДокументОпозицияСтекти2::GetRange Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentPositionOffset2::GetRange
ms.assetid: 27da7130-0932-4f97-abde-05e6fb018606
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fd305b6506471a40de90fbd954e54461d2a139d0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731630"
---
# <a name="idebugdocumentpositionoffset2getrange"></a>IDebugDocumentPositionOffset2::GetRange
Извлекает диапазон для текущего положения документа.

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
(в, вне) Смещение для стартовой позиции диапазона. Установите этот параметр в нулевую величину, если эта информация не нужна.

`pdwEndOffset`\
(в, вне) Смещение для конечного положения диапазона. Установите этот параметр в нулевую величину, если эта информация не нужна.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Диапазон, указанный в позиции документа для точки разрыва местоположения, используется движком отладки (DE) для поиска заранее оператора, который фактически вносит код. Рассмотрим следующий пример кода:

```
Line 5: // comment
Line 6: x = 1;
```

 Строка 5 не вносит код в отладку программы. Если отладчик, устанавливающий точку разрыва на строке 5, хочет, чтобы DE выдвигал определенную сумму для первой строки, которая вносит код, отладчик указывает диапазон, включающий дополнительные строки кандидатов, где точка разрыва может быть правильно размещена. DE будет искать вперед через эти строки, пока он не нашел строку, которая может принять точку разрыва.

## <a name="see-also"></a>См. также
- [IDebugDocumentPositionOffset2](../../../extensibility/debugger/reference/idebugdocumentpositionoffset2.md)
- [GetRange](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md)
