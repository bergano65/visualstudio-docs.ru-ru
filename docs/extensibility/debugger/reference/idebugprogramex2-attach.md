---
title: IDebugProgramEx2::Прикрепите Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramEx2::Attach
helpviewer_keywords:
- IDebugProgramEx2::Attach
ms.assetid: 33b22b2f-431e-4205-9441-d28a9c928c97
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fcb52a96074b783043af1e908cf454466df74c30
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722387"
---
# <a name="idebugprogramex2attach"></a>IDebugProgramEx2::Attach
Прикрепите сеанс к программе.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT Attach( 
   IDebugEventCallback2* pCallback,
   DWORD                 dwReason,
   IDebugSession2*       pSession
);
```

```csharp
int Attach( 
   IDebugEventCallback2 pCallback,
   uint                 dwReason,
   IDebugSession2       pSession
);
```

## <a name="parameters"></a>Параметры
`pCallback`\
(в) Объект [IDebugEventCallback2,](../../../extensibility/debugger/reference/idebugeventcallback2.md) представляющий функцию обратного вызова, на который прилагаемый отладивший двигатель отправляет события.

`dwReason`\
(в) Значение из [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md) перечисления, описывающий причину операции присоединения.

`pSession`\
(в) Значение, которое однозначно определяет сеанс, прилагаемый к программе.

## <a name="return-value"></a>Возвращаемое значение
 В случае `S_OK`успеха, возвращается ; в противном случае возвращает код ошибки. Этот метод `E_ATTACH_DEBUGGER_ALREADY_ATTACHED` должен вернуться, если программа уже подключена.

## <a name="remarks"></a>Примечания
 Порт, содержащий программу, может `pSession` использовать значение, чтобы определить, какой сеанс пытается прикрепить к программе. Например, если порт позволяет прикреплять к процессу только один сеанс отладки, порт может определить, подключен ли тот же сеанс к другим программам в процессе.

> [!NOTE]
> Интерфейс, пройденый, `pSession` должен рассматриваться только как файлcookieое, значение, которое однозначно определяет менеджер отладки сеанса, прикрепляющий сякшет к этой программе; ни один из методов на поставляемом интерфейсе не является функциональным.

## <a name="see-also"></a>См. также
- [IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)
