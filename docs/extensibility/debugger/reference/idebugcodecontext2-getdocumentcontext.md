---
title: IDebugCodeContext2::GetDocumentКонтекст Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCodeContext2::GetDocumentContext
helpviewer_keywords:
- IDebugCodeContext2::GetDocumentContext
ms.assetid: d552cc92-963f-43c1-949f-ae6b63a427b8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 46510ce794ea30fdd365a77007b962a1eafd5d31
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734341"
---
# <a name="idebugcodecontext2getdocumentcontext"></a>IDebugCodeContext2::GetDocumentContext
Получает контекст документа, соответствующий данному контексту кода. Контекст документа представляет собой позицию в исходном файле, которая соответствует исходному коду, который генерировал эту инструкцию.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetDocumentContext( 
   IDebugDocumentContext2** ppSrcCxt
);
```

```csharp
int GetDocumentContext( 
   out IDebugDocumentContext2 ppSrcCxt
);
```

## <a name="parameters"></a>Параметры
`ppSrcCxt`\
(ваут) Возвращает объект [IDebugDocumentContext2,](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) соответствующий контексту кода. Если `S_OK` возвращается, ths должны`null`быть не- .

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки. Отладочный движок должен вернуть `E_FAIL` код `out` отказа, например, когда параметр например, `null` когда контекст кода не имеет связанного исходного положения.

## <a name="remarks"></a>Примечания
 Как правило, контекст документа можно рассматривать как позицию в исходном файле, в то время как контекст кода — это позиция инструкции кода в потоке выполнения.

## <a name="see-also"></a>См. также
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
