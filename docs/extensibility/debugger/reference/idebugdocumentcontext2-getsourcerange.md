---
title: IDebugДокументКонтекст2:GetSourceRange Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentContext2::GetSourceRange
helpviewer_keywords:
- IDebugDocumentContext2::GetSourceRange
ms.assetid: 5903c75e-5390-4d13-9314-1ee276255313
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 782cf230c38af77da09b49f69c093e2e95bf7199
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731801"
---
# <a name="idebugdocumentcontext2getsourcerange"></a>IDebugDocumentContext2::GetSourceRange
Получает диапазон исходного кода этого контекста документа.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetSourceRange( 
   TEXT_POSITION* pBegPosition,
   TEXT_POSITION* pEndPosition
);
```

```csharp
int GetSourceRange( 
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
 Исходный диапазон — это весь диапазон исходного кода, от текущего оператора до сразу после предыдущего оператора, в котором был внесен код. Диапазон исходных источников обычно используется для смешивания исходных заявлений, включая комментарии, с кодом в окне разборки.

 Чтобы получить диапазон только для кодов, содержащихся в этом контексте документа, позвоните в метод [GetStatementRange.](../../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)

## <a name="see-also"></a>См. также
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
- [GetStatementRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)
- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
