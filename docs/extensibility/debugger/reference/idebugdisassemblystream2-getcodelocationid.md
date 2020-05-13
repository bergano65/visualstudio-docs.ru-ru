---
title: IDebugDisassemblyStream2::GetCodeLocationId (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDisassemblyStream2::GetCodeLocationId
helpviewer_keywords:
- IDebugDisassemblyStream2::GetCodeLocationId
ms.assetid: 567adfb8-2f54-499a-a027-e4ecb82277ef
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 32be70e11776177a0e68f09689c2262497703ab1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732253"
---
# <a name="idebugdisassemblystream2getcodelocationid"></a>IDebugDisassemblyStream2::GetCodeLocationId
Возвращает идентификатор местоположения кода для определенного контекста кода.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetCodeLocationId( 
   IDebugCodeContext2* pCodeContext,
   UINT64*             puCodeLocationId
);
```

```csharp
int GetCodeLocationId( 
   IDebugCodeContext2 pCodeContext,
   out ulong          puCodeLocationId
);
```

## <a name="parameters"></a>Параметры
`pCodeContext`\
(в) Объект [IDebugCodeContext2,](../../../extensibility/debugger/reference/idebugcodecontext2.md) который будет преобразован в идентификатор.

`puCodeLocationId`(ваут) Возвращает идентификатор местоположения кода. См. заметки.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки. Возвращает, `E_CODE_CONTEXT_OUT_OF_SCOPE` если контекст кода действителен, но находится за пределами сферы действия.

## <a name="remarks"></a>Примечания
 Идентификатор местоположения кода специфичен для движка отладки (DE), поддерживающего демонтаж. Этот идентификатор местоположения используется DE внутри компании для отслеживания позиций в коде и, как правило, является адресом или смещением какого-либо вида. Единственным требованием является то, что если контекст кода одного местоположения меньше, чем контекст кода другого местоположения, то соответствующий идентификатор местоположения кода первого контекста кода также должен быть меньше, чем идентификатор местоположения кода второго контекста кода.

 Чтобы получить кодовый контекст идентификатора местоположения кода, позвоните в метод [GetCodeContext.](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md)

## <a name="see-also"></a>См. также
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [GetCodeContext](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md)
