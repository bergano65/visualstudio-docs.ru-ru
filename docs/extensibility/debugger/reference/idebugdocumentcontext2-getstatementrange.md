---
title: IDebugDocumentContext2:GetStatementRange Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentContext2::GetStatementRange
helpviewer_keywords:
- IDebugDocumentContext2::GetStatementRange
ms.assetid: bc94851a-0ec4-47ea-99c7-0a585e54e726
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 50e521d98f10477d56dfece30e20fd000b87b632
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731766"
---
# <a name="idebugdocumentcontext2getstatementrange"></a>IDebugDocumentContext2::GetStatementRange
Получает диапазон файлового заявления контекста документа.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetStatementRange(
    TEXT_POSITION* pBegPosition,
    TEXT_POSITION* pEndPosition
);
```

```csharp
int GetStatementRange(
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
Диапазон оператора — это диапазон строк, которые внесли код, на который ссылается этот контекст документа.

Чтобы получить диапазон исходного кода (включая комментарии) в этом контексте документа, позвоните в метод [GetSourceRange.](../../../extensibility/debugger/reference/idebugdocumentcontext2-getsourcerange.md)

## <a name="example"></a>Пример
В следующем примере показано, как `CDebugContext` реализовать этот метод для простого объекта, который предоставляет интерфейс [IDebugDocumentContext2.](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) Этот пример заполняет окончание позиции только в том случае, если начальное положение не является нулевая величина.

```cpp
HRESULT CDebugContext::GetStatementRange(TEXT_POSITION* pBegPosition,
                                         TEXT_POSITION* pEndPosition)
{
    HRESULT hr;

    // Check for a valid beginning position argument pointer.
    if (pBegPosition)
    {
        // Copy the member TEXT_POSITION into the local pBegPosition.
        memcpy(pBegPosition, &m_pos, sizeof (TEXT_POSITION));

        // Check for a valid ending position argument pointer.
        if (pEndPosition)
        {
            // Copy the member TEXT_POSITION into the local pEndPosition.
            memcpy(pEndPosition, &m_pos, sizeof (TEXT_POSITION));
        }
        hr = S_OK;
    }
    else
    {
        hr = E_INVALIDARG;
    }

    return hr;
}
```

## <a name="see-also"></a>См. также
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
- [GetSourceRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getsourcerange.md)
- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
