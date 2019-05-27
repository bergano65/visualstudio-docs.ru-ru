---
title: IDebugPortSupplier2::RemovePort | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier2::RemovePort
helpviewer_keywords:
- IDebugPortSupplier2::RemovePort
ms.assetid: f5c1fbf2-9084-46f2-a682-7db963928df2
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ced86b93bb1fe9fcff791cbb3c4bbc040b30764c
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/24/2019
ms.locfileid: "66204376"
---
# <a name="idebugportsupplier2removeport"></a>IDebugPortSupplier2::RemovePort
Удаляет порт.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT RemovePort( 
   IDebugPort2* pPort
);
```

```csharp
int RemovePort( 
   IDebugPort2 pPort
);
```

## <a name="parameters"></a>Параметры
`pPort`\
[in] [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) , представляющий удаляемый порт.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Этот метод удаляет порт из внутреннего списка активные порты поставщика порта.

## <a name="see-also"></a>См. также
- [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)