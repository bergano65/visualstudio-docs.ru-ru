---
title: IDebugProgram2::EnumModules | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::EnumModules
helpviewer_keywords:
- IDebugProgram2::EnumModules
ms.assetid: 876ac9da-3b7c-4156-b79a-8f340e9fcea6
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 68ccc490476fcb8ccf3cc135493f5d95253f1018
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/24/2019
ms.locfileid: "66200305"
---
# <a name="idebugprogram2enummodules"></a>IDebugProgram2::EnumModules
Извлекает список модулей, эта программа загрузки и выполнения.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT EnumModules( 
   IEnumDebugModules2** ppEnum
);
```

```csharp
int EnumModules( 
   out IEnumDebugModules2 ppEnum
);
```

## <a name="parameters"></a>Параметры
`ppEnum`\
[out] Возвращает [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md) , содержащий список модулей.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Модуль — это библиотека DLL или сборки и обычно указывается в **модули** окно отладки.

## <a name="see-also"></a>См. также
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)