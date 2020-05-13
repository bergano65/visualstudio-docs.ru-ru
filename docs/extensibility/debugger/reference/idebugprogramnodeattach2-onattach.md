---
title: IDebugProgramNodeAttach2::OnAttach Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNodeAttach2::OnAttach
helpviewer_keywords:
- IDebugProgramNodeAttach2::OnAttach
ms.assetid: 5fe52761-a508-4ab5-abdb-334fb6590334
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: dfb8a39af3c030dadddcb148a79a96b57f20e183
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721873"
---
# <a name="idebugprogramnodeattach2onattach"></a>IDebugProgramNodeAttach2::OnAttach
Прикрепляется к сопутствуеной программе или откладывает процесс присоединения к методу [присоединения.](../../../extensibility/debugger/reference/idebugengine2-attach.md)

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT OnAttach(
   [in] REFGUID guidProgramId
);
```

```csharp
int OnAttach(
   ref Guid guidProgramId
};
```

## <a name="parameters"></a>Параметры
`guidProgramId`\
(в) `GUID` присваивать сяваемую программу.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK`. Возвращает, `S_FALSE` если метод [присоединения](../../../extensibility/debugger/reference/idebugengine2-attach.md) не должен вызываться. В противном случае возвращается код ошибки.

## <a name="remarks"></a>Примечания
 Этот метод вызывается во время процесса присоединения, прежде чем метод [присоединения](../../../extensibility/debugger/reference/idebugengine2-attach.md) называется. Метод `OnAttach` может выполнять процесс присоединения себя (в этом `S_FALSE`случае, этот метод возвращается) `OnAttach` или `S_OK`отложить процесс присоединения к методу `IDebugEngine2::Attach` (метод возвращается). В любом случае `OnAttach` метод может `GUID` настроить отладку программы в `GUID`данную.

## <a name="see-also"></a>См. также
- [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)
- [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)
