---
title: IDebugProgramEx2::GetProgramNode | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramEx2::Attach
helpviewer_keywords:
- IDebugProgramEx2::Attach
ms.assetid: 1545ffbf-1422-4b5d-9bb9-314ba8665041
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8c6a683aacf0de18ee4ce0b00f5f12c2104ce333
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/24/2019
ms.locfileid: "66211112"
---
# <a name="idebugprogramex2getprogramnode"></a>IDebugProgramEx2::GetProgramNode
Получает узел программы, связанный с программой.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetProgramNode( 
   IDebugProgramNode2** ppProgramNode
);
```

```csharp
int GetProgramNode( 
   out IDebugProgramNode2 ppProgramNode
);
```

## <a name="parameters"></a>Параметры
`ppProgramNode`\
[out] Возвращает [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) , представляющий узел программы, связанные с этой программой.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также
- [IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)