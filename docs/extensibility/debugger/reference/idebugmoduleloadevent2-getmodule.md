---
title: IDebugModuleLoadEvent2::GetModule | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModuleLoadEvent2::GetModule
helpviewer_keywords:
- IDebugModuleLoadEvent2::GetModule
ms.assetid: c86482bb-9ce5-4e63-bbe0-969b50169424
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2d6f6672349d6a37d0f7b5e43c9a68d765d3abc7
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/24/2019
ms.locfileid: "66203000"
---
# <a name="idebugmoduleloadevent2getmodule"></a>IDebugModuleLoadEvent2::GetModule
Возвращает модуль, для которого создается загрузке или выгрузке.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetModule( 
   IDebugModule2** pModule,
   BSTR*           pbstrDebugMessage,
   BOOL*           pbLoad
);
```

```csharp
int GetModule( 
   out IDebugModule2 pModule,
   ref string        pbstrDebugMessage,
   ref int           pbLoad
);
```

## <a name="parameters"></a>Параметры
`pModule`\
[out] Возвращает [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) , представляющий модуль, который загрузкой или выгрузкой.

`pbstrDebugMessage`\
[in, out] Возвращает необязательное сообщение, описывающее данное событие. Если этот параметр имеет значение null, сообщение не запрашивается.

`pbLoad`\
[in, out] Ненулевое значение (`TRUE`) Если модуль является загрузка и ноль (`FALSE`) Если модуль выгружается. Если этот параметр имеет значение null, состояние не запрашивается.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также
- [IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md)
- [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)