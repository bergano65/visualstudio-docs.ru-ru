---
title: IDebugPortNotify2::AddProgramNode | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortNotify2::AddProgramNode
helpviewer_keywords:
- IDebugPortNotify2::AddProgramNode
ms.assetid: 34c0e949-1eb9-4108-9cb8-a3eb87fcf190
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 225fb622507ea1ea6473a97c379bc1026cc9fcb6
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/24/2019
ms.locfileid: "66208948"
---
# <a name="idebugportnotify2addprogramnode"></a>IDebugPortNotify2::AddProgramNode
Регистрирует порт, на котором он выполняется на программы, которые можно отлаживать.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT AddProgramNode( 
   IDebugProgramNode2* pProgramNode
);
```

```csharp
int AddProgramNode( 
   IDebugProgramNode2 pProgramNode
);
```

## <a name="parameters"></a>Параметры
`pProgramNode`\
[in] [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) объект, представляющий программу для регистрации.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Узел программы можно отменить регистрацию из порта путем вызова [RemoveProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md) метод.

## <a name="see-also"></a>См. также
- [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
- [RemoveProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md)