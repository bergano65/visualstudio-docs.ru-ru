---
title: IDebugДокументОпозиция2::GetRange Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentPosition2::GetRange
helpviewer_keywords:
- IDebugDocumentPosition2::GetRange
ms.assetid: 91a06ee7-253a-4215-be22-04bf57305aa8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a923691afdfe145931ab31d0e9bbc6142e7c8d1c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731666"
---
# <a name="idebugdocumentposition2getrange"></a>IDebugDocumentPosition2::GetRange
Получает диапазон для этой позиции документа.

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
(в, вне) [Структура TEXT_POSITION,](../../../extensibility/debugger/reference/text-position.md) заполненная исходным положением. Установите этот аргумент в нулевую величину, если эта информация не нужна.

`pEndPosition`\
(в, вне) [Структура TEXT_POSITION,](../../../extensibility/debugger/reference/text-position.md) заполненная окончанием положения. Установите этот аргумент в нулевую величину, если эта информация не нужна.

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
- [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)
- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
